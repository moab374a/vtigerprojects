balenaCloud GLPI + FusionInventory (from balena Lamp Stack)
============================================================

### Introduction

This project creates three containerized services -- _apache_, _mysql_ and _php_ -- that together provide a basic LAMP stack.

```
/balena-glpi-fusioninventory/
├── .balena
│   ├── secrets
│   └── balena.yml
├── apache
│   ├── Dockerfile
│   └── demo.apache.conf
├── docker-compose.yml
├── php
│   └── Dockerfile
│   └── index.php
```

Apache, PHP and MySQL are built during the balena push action. The apache service depends on both _mysql_ and _php_ and shares a the _/var/www/html_ volume with _php_. This is the location of the main _index.php_ file, which runs a test connection to _mysql_. Notice that the hostname in this file is set to _"mysql"_ (not localhost), and is resolvable by name based on the network configuration.

Two networks are used. The _frontend_ network enables external connections to port 80. The _backend_ network enables _php_ and _mysql_ to use non-public ports to reach _apache_.

Note that specific versions of each Docker image is defined in each _Dockerfile.template_. These could be replaced with _:latest_ or other versions that suit your needs. The _mysql_ passwords, database name and username are set as variables from the _.balena/balena.yml_ file. You should change them for production uses, but be sure to update the _php/index.php_ file to match.

### Deploy

[![](https://balena.io/deploy.png)](https://dashboard.balena-cloud.com/deploy)

__or__

Clone this repository, change into the balena-lamp directory and push to your application:

```
 git clone git@github.com/THaupt-work/balena-glpi-fusioninventory.git
 cd balena-glpi-fusioninventory
 balena push <appname>
```

### Changed

### Infos
#### GLPI
https://glpi-install.readthedocs.io/en/latest/index.html

Currently, only MySQL (5.6 minimum) and MariaDB (10.0 minimum) database servers are supported by GLPI.


##### Mandatory extensions
Following PHP extensions are required for the app to work properly:
- curl
- fileinfo
- gd
- json
- mbstring
- mysqli
- session
- zlib
- simplexml
- xml
- intl
- cli
- domxml
- ldap    (php7-ldap)
- openssl (php7-openssl) 
- xmlrpc  (php7-xmlrpc)
- apcu    (php7-pecl-apcu)
##### PHP Settings

memory_limit = 64M ;        // max memory limit
file_uploads = on ;
max_execution_time = 600 ;  // not mandatory but recommended
session.auto_start = off ;
session.use_trans_sid = 0 ; // not mandatory but recommended

##### Download URI for GLPI-9.5.5
wget https://github.com/glpi-project/glpi/releases/download/9.5.5/glpi-9.5.5.tgz


#### Fusioninventory
https://fusioninventory.org/documentation/fi4g/installation.html

### Notes

