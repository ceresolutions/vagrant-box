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

 [1]: https://box.scotch.io/
 [2]: https://git-scm.com/downloads
 [3]: https://www.vagrantup.com/downloads.html
 [4]: https://www.virtualbox.org/wiki/Downloads
 [5]: http://192.168.33.10/
