[Scotch Box][1]
==========

## Get Started

* Download and Install [Git BASH][2] (Windows only)
* Download and Install [Vagrant][3]
* Download and Install [VirtualBox][4]
* Clone the Vagrant Box [GitHub Repository](https://github.com/ceresolutions/vagrant-box.git)
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

- Hostname: 192.168.33.10
- Port: 22
- Username: vagrant
- Password: vagrant

```
#connect in cli
ssh vagrant@192.168.33.10

#vagrant@192.168.33.10's password: vagrant
```

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
root@scotchbox:/home/vagrant# a2enmod rewrite
root@scotchbox:/home/vagrant# a2enmod ssl
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

*Do not remove edited config file. It can be used again for new vagrant-box (in case having problems with current box)*
```
#vagrant ssh

#copy
vagrant@scotchbox:~$ sudo su
root@scotchbox:/home/vagrant# cp /var/www/new_project.conf /etc/apache2/sites-available/new_project.conf

#enable virtual host
root@scotchbox:/home/vagrant# a2ensite new_project
root@scotchbox:/home/vagrant# service apache2 restart
```

Update file host in real machine
```
192.168.33.10 uc.dev www.uc.dev abc.uc.dev
```
==========
## Advanced

```
# vagrant ssh

vagrant@scotchbox:~$ cp /var/www/create_swap.sh /home/vagrant/create_swap.sh
vagrant@scotchbox:~$ chmod 775 create_swap.sh
vagrant@scotchbox:~$ crontab -e

# Add below lines to the end of the editor

# Auto start Mailcatcher
@reboot /home/vagrant/.rbenv/shims/mailcatcher --http-ip=0.0.0.0

# Auto update time server
@reboot sudo /etc/init.d/ntp restart
@reboot sudo /usr/sbin/ntpdate pool.ntp.org

# Fix swap memory issue (file create_swap.sh is required)
@reboot sudo /home/vagrant/create_swap.sh
```

==========
For more details please visit https://box.scotch.io/

 [1]: https://box.scotch.io/
 [2]: https://git-scm.com/downloads
 [3]: https://www.vagrantup.com/downloads.html
 [4]: https://www.virtualbox.org/wiki/Downloads
 [5]: http://192.168.33.10/
