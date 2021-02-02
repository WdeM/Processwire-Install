# Processwire-Install
Processwire install steps.

### Tested on ubuntu 20.04 with apache2 ###

## Install ##

Install necessary packages

`sudo apt-get install apache2 php libapache2-mod-php mysql-server php-mysql php7.4-gd php-zip`

Enable apache module mod_rewrite

`sudo a2enmod rewrite`

Configure database

```
sudo mysql_secure_installation <- do steps

sudo mysql
create database DATABASENAME;
create user 'username'@'localhost' identified by 'password';
grant all privileges on DATABASENAME.* to 'username'@'localhost';
flush privileges;
```

Edit /etc/apache2/apache2.conf

```
Edit from the conf file

<Directory /var/www/>
    Options FollowSymLinks
    AllowOverride None -> Change to ALL
    ...
```

Download and build processwire

```
cd /var/www/html/
sudo rm index.html <- remove unnecessary default page
sudo git clone https://github.com/processwire/processwire.git <- using sudo because folder owner root by default
sudo mv processwire/* ./
sudo rm -rf processwire/ <- unnecessary folder
sudo chown -R www-data:www-data * <- adjust ownership to user and group www-data
sudo systemctl restart apache2.service
```

Go to http://localhost or ip and finish the install with correct parameters.




