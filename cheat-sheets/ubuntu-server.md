# Ubuntu Server

## General

Check version: `$ cat /etc/lsb-release`

## [Securing new server](https://www.linode.com/docs/security/securing-your-server)

On remote server install [Fail2Ban](http://www.fail2ban.org/wiki/index.php/Main\_Page):`sudo apt-get update && sudo apt-get install fail2ban`

Add folder for SSH keys:`mkdir -p ~/.ssh && sudo chmod -R 700 ~/.ssh/`

On your local machine create an SSH key pair if you haven't before:`ssh-keygen -b 4096`

Push SSH Key on local machine to remove server:`cat ~/.ssh/id_rsa.pub | ssh ROOT@EXAMPLE.COM 'cat >> ~/.ssh/authorized_keys'`

Verify SSH key connection, then disable password entry on remote server:`vim /etc/ssh/sshd_config`

Then change `PasswordAuthentication` from `yes` to `no`, save the file, and finally restart SSH:`sudo systemctl restart sshd`

Check recent SSH logins:`grep "Accepted" /var/log/auth.log`

## [Setup](https://developer.ibm.com/devpractices/devops/blogs/two-factor-authentication-for-ssh/) [2FA](https://www.digitalocean.com/community/tutorials/how-to-set-up-multi-factor-authentication-for-ssh-on-ubuntu-16-04) [for SSH](https://ubuntu.com/tutorials/configure-ssh-2fa#1-overview)

Start a terminal session and type:`sudo apt install libpam-google-authenticator` To make SSH use the Google Authenticator PAM module, add the following line to the `/etc/pam.d/sshd` file:

```
auth required pam_google_authenticator.so
```

Also, so we don't get asked for a password, and instead use our SSH key for auth, comment out the line `@include common-auth`:

```
#@include common-auth
```

Modify `/etc/ssh/sshd_config` – change `ChallengeResponseAuthentication` from no to yes, so this part of the file looks like this:

```
# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no # CHANGE THIS TO YES

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes
```

Then add this to the same `/etc/ssh/sshd_config` file:`AuthenticationMethods publickey,keyboard-interactive`

In a terminal, run the `google-authenticator` command.

It will ask you a series of questions, here is a recommended configuration:

* Make tokens “time-base””: yes
* Update the .google\_authenticator file: yes
* Disallow multiple uses: yes
* Increase the original generation time limit: no
* Enable rate-limiting: yes

Store the 2FA stuff in your favorite auth manager, and keep a copy of the recovery codes.

Restart the sshd daemon using:`sudo systemctl restart sshd.service`

## [Installing WordPress](https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-on-ubuntu-20-04-with-a-lamp-stack)

Digital Ocean, start with [LAMP app](https://marketplace.digitalocean.com/apps/lamp), otherwise follow [these instructions](https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-20-04) to get LAMP going.

Download WordPress, and setup the WP Config and Htaccess files:

```
cd /tmp
curl -O https://wordpress.org/latest.tar.gz
tar xzvf latest.tar.gz
touch /tmp/wordpress/.htaccess
cp /tmp/wordpress/wp-config-sample.php /tmp/wordpress/wp-config.php
mkdir /tmp/wordpress/wp-content/upgrade
```

Now, we copy the contents of the WordPress temp directory to our Apache2 site. We are using a dot at the end of our source directory to indicate that everything within the directory should be copied, including hidden files:`sudo cp -a /tmp/wordpress/. /var/www/MY_DIR`

Update the ownership with the chown and chmod commands.

```
sudo chown -R www-data:www-data /var/www/MY_DIR
chmod -R g+s /var/www/MY_DIR
sudo find /var/www/MY_DIR/ -type d -exec chmod 750 {} \;
sudo find /var/www/MY_DIR/ -type f -exec chmod 640 {} \;
```

Login to MYSQL:`$ mysql -u USERNAME -pPASSWORD`

Create a MySQL database and user (note these instructions will give the resulting user access to all databases):

```
CREATE DATABASE databasename;
CREATE USER 'newuser'@'localhost' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON * . * TO 'newuser'@'localhost';
FLUSH PRIVILEGES;
```

Update the `wp-config.php` file to reference your new database and user name. Also update the SALT values.

Visit the site in your browser to finish the installation.

#### Additional PHP extensions

One of the themes I use requires mbstring which you can install like this: `$ sudo apt install php-mbstring`

&#x20;Then restart Apache: `$ sudo service apache2 restart`

## [Installing Rails](https://gorails.com/setup/ubuntu/16.04)

Install Ruby dependencies:`sudo apt-get install git-core curl zlib1g-dev build-essential libssl-dev libreadline-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev libcurl4-openssl-dev python-software-properties libffi-dev nodejs`

Install Ruby with rbenv, be sure to change 2.2.2 with whatever Ruby version you want:

```
cd
git clone https://github.com/rbenv/rbenv.git ~/.rbenv
echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(rbenv init -)"' >> ~/.bashrc
exec $SHELL

git clone https://github.com/rbenv/ruby-build.git ~/.rbenv/plugins/ruby-build
echo 'export PATH="$HOME/.rbenv/plugins/ruby-build/bin:$PATH"' >> ~/.bashrc
exec $SHELL

rbenv install 2.4.1
rbenv global 2.4.1
ruby -v

gem install bundler
```

Install NodeJS:`curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash - sudo apt-get install -y nodejs`

Install Rails, change the version to the one you want:

```
gem install rails -v 5.1.3
rbenv rehash
rails -v
```

Install PostgreSQL:

```
sudo sh -c "echo 'deb http://apt.postgresql.org/pub/repos/apt/ xenial-pgdg main' > /etc/apt/sources.list.d/pgdg.list"
wget --quiet -O - http://apt.postgresql.org/pub/repos/apt/ACCC4CF8.asc | sudo apt-key add -
sudo apt-get update
sudo apt-get install postgresql-common
sudo apt-get install postgresql-9.5 libpq-dev

sudo -u postgres createuser chris -s

# If you would like to set a password for the user, you can do the following
sudo -u postgres psql
postgres=# \password chris
```

Setting up a project with SQLite:`rails new myapp`

Setting up a project with PostgreSQL, you may need to edit `config/database.yml` to match the user you created earlier:`rails new myapp -d postgresql`

Run Rails dev server so you can [access it remotely](https://stackoverflow.com/a/30723007/648844):`rails s -b 0.0.0.0`

## Webpack

Increase file watching limit:

```
echo fs.inotify.max_user_watches=524288 | sudo tee -a /etc/sysctl.conf
sudo sysctl -p
```

## Firewall

I had to open up port 3000 to get browsersync on port 3000 to work with my local browser.

Check firewall status: `$ sudo ufw status`

Allow port access (port/protocal): `$ ufw allow 3000/tcp`&#x20;

Remove an allow rule: `$ ufw delete allow 3000/tcp`

## Postgres

Installing postgres on Ubuntu/Debian for dev

```
sudo apt update
sudo apt install postgresql postgresql-contrib
```

Log in to postgres and create the uprise db

```
sudo -u postgres psql
createdb my_db;
\q
```

Allow passwordless connections for postgres dev:

```
sudo -u postgres psql
show hba_file;
\q
```

Copy result of command above, and edit in vim/nano

Change this line:

```
host    all             all             127.0.0.1/32            md5
```

To:

```
host    all             all             127.0.0.1/32            trust
```

Restart postgres:

```
sudo /etc/init.d/postgresql restart
```
