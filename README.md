Scotch Box
==========

## Get Started

* Download and Install [Vagrant][3]
* Download and Install [VirtualBox][4]
* Clone the Scotch Box [GitHub Repository](https://github.com/nxthuy/vagrant-box.git)
* Run ``` vagrant up ```
* Access Your Project at  [http://192.168.33.10/][14]

## Basic Vagrant Commands


### Start or resume your server
```bash
vagrant up
```

### Pause your server
```bash
vagrant suspend
```

### Delete your server
```bash
vagrant destroy
```

### SSH into your server
```bash
vagrant ssh
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

 [1]: https://github.com/MiniCodeMonkey/Vagrant-LAMP-Stack
 [2]: http://scotch.io/tutorials/get-vagrant-up-and-running-in-no-time
 [3]: https://www.vagrantup.com/downloads.html
 [4]: https://www.virtualbox.org/wiki/Downloads
 [5]: http://www.sequelpro.com/
 [6]: http://www.navicat.com/
 [7]: http://github.com/scotch-io
 [8]: http://twitter.com/scotch_io
 [9]: https://github.com/smdahlen/vagrant-hostmanager
 [10]: http://scotch.io/tutorials/sharing-your-virtual-machine-on-the-web-with-vagrant-share
 [11]: http://scotch.io/tutorials/php/getting-started-with-laravel-homestead
 [12]: https://www.vagrantup.com/downloads.html
 [13]: https://www.virtualbox.org/wiki/Downloads
 [14]: http://192.168.33.10/
 [15]: https://github.com/smdahlen/vagrant-hostmanager
 [16]: http://box.scotch.io
 [17]: http://scotch.io/bar-talk/introducing-scotch-box-a-vagrant-lamp-stack-that-just-works
