# Apache

[Digital Ocean tutorial for Virtual Hosts](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-18-04).

Enable site:`sudo a2ensite SITENAME`

Disable site:`sudo a2dissite SITENAME`

List apache modules:`apache2ctl -M`

Enable an apache2 module:`sudo a2enmod MODULENAME`

Disable an apache2 module:`sudo a2dismod MODULENAME`

Enable mod rewrite: `sudo a2enmod rewrite`

Reload server:`service apache2 reload`

Force reload the server:`sudo /etc/init.d/apache2 force-reload`

Apache file permissions:

```text
chown -R www-data:www-data /folder/
chmod +r /folder
```

Virtual hosts directory: `/etc/apache2/sites-available/`

Virtual Host sample file:

```text
<VirtualHost *:80>
  DocumentRoot /var/www/site
  ServerName site.example.com
  CustomLog /var/www/logs/site/access.log combined
  ErrorLog /var/www/logs/site/error.log
</VirtualHost>
```

