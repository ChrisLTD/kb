# Ubuntu Server

### [Securing new server](https://www.linode.com/docs/security/securing-your-server)

On remote server install [Fail2Ban](http://www.fail2ban.org/wiki/index.php/Main_Page):`sudo apt-get update && sudo apt-get install fail2ban`

Add folder for SSH keys:`mkdir -p ~/.ssh && sudo chmod -R 700 ~/.ssh/`

On your local machine create an SSH key pair if you haven't before:`ssh-keygen -b 4096`

Push SSH Key on local machine to remove server:`cat ~/.ssh/id_rsa.pub | ssh ROOT@EXAMPLE.COM 'cat >> ~/.ssh/authorized_keys'`

Verify SSH key connection, then disable password entry on remote server:`vim /etc/ssh/sshd_config`

Then change `PasswordAuthentication` from `yes` to `no`, save the file, and finally restart SSH:`sudo systemctl restart sshd`

### [Installing Rails](https://gorails.com/setup/ubuntu/16.04)

Install Ruby dependencies:`sudo apt-get install git-core curl zlib1g-dev build-essential libssl-dev libreadline-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev libcurl4-openssl-dev python-software-properties libffi-dev nodejs`

Install Ruby with rbenv, be sure to change 2.2.2 with whatever Ruby version you want:

```text
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

```text
gem install rails -v 5.1.3
rbenv rehash
rails -v
```

Install PostgreSQL:

```text
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

