[Scotch Box][1]
==========

## Get Started

* Download and Install [Git BASH][2] (Windows only)
* Download and Install [Vagrant][3]
* Download and Install [VirtualBox][4]
* Clone the Vagrant Box [GitHub Repository](https://github.com/nxthuy/vagrant-box.git)
* Run ``` vagrant up ```
* Access Your Project at  [http://192.168.33.10/][5]

## Basic Vagrant Commands


### Start or resume your server
```bash
vagrant up
```

### SSH into your server
```bash
vagrant ssh
```

### Pause your server
```bash
vagrant suspend
```

### Delete your server
```bash
vagrant destroy
```


## Database Access

### MySQL 

- Hostname: localhost or 127.0.0.1
- Username: root
- Password: root
- Database: scotchbox

### PostgreSQL

- Hostname: localhost or 127.0.0.1
- Username: root
- Password: root
- Database: scotchbox
- Port: 5432


### MongoDB

- Hostname: localhost
- Database: scotchbox
- Port: 27017

### From a Desktop Client

You'll need to download either [Sequel Pro] (http://www.sequelpro.com/) or [Navicat] (http://www.navicat.com/) or some other desktop database client. Switching to one of these from phpMyAdmin will be a life changing experience so just do it already. After this, create a "new connection" and select SSH Forwarding and enter these parameters:

![alt text] (https://box.scotch.io/database-logins.jpg)


- Database Name:	(leave blank)
- Database User: root
- Database Password:	root
- Database Host: 127.0.0.1
- Database Port: 3306
- SSH Host: 192.168.33.10
- SSH User: vagrant
- SSH Password: vagrant

## SSH Access

- Hostname: 127.0.0.1:2222
- Username: vagrant
- Password: vagrant

## Mailcatcher

Just do:

```
vagrant ssh
mailcatcher --http-ip=0.0.0.0
```

Then visit:

```
http://192.168.33.10:1080
```

## Enable Apache Modes
```
#vagrant ssh
vagrant@scotchbox:~$ sudo su
vagrant@scotchbox:~$ a2enmod rewrite
vagrant@scotchbox:~$ a2enmod ssl
```

## Clone project source
```
#git-bash
cd public/
git clone ....
```

## Config VirtualHost
Clone file virtual_host_config.conf (virtual_host_config_ssl.conf for SSL)
```
cp virtual_host_config.conf new_project.conf
```
Edit new_project.conf to concide with project
```
<VirtualHost *:80>
        ServerAdmin admin@uc.dev #admin email
        ServerName uc.dev #domain name
        ServerAlias www.uc.dev abc.uc.dev
        DocumentRoot /var/www/public/trunk/public #absolute path of project dir
        ErrorLog ${APACHE_LOG_DIR}/ultracrm.dev_error.log
        CustomLog ${APACHE_LOG_DIR}/ultracrm.dev__access.log combined
        <Directory /var/www/public/ultracrm/trunk/public> #absolute path of project dir
                Options Indexes FollowSymLinks
                AllowOverride All
               Require all granted
                Satisfy all
        </Directory>
</VirtualHost>
```
Copy edited config file to apache sites-available dir
```
#vagrant ssh

#copy
vagrant@scotchbox:~$ sudo su
vagrant@scotchbox:~$ cp /var/www/new_project.conf /etc/apache2/sites-available/new_project.conf

#enable virtual host
vagrant@scotchbox:~$ a2ensite new_project
vagrant@scotchbox:~$ service apache2 restart
```

Update file host in real machine
```
192.168.33.10 uc.dev www.uc.dev abc.uc.dev
```



 [1]: https://box.scotch.io/
 [2]: https://git-scm.com/downloads
 [3]: https://www.vagrantup.com/downloads.html
 [4]: https://www.virtualbox.org/wiki/Downloads
 [5]: http://192.168.33.10/
