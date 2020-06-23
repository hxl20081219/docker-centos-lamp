LAMP built with Docker Compose
# introduction
A basic LAMP environment built using Docker Compose. It consists of the following:

- centos7
- PHP7.4
- Apache2.4
- MySQL5.7
- Redis

# Installation
- install docker,docker-compose for centos
```
yum install -y docker
yum install -y yum install epel-release
yum install -y docker-compose
```
- install docker desktop for windows
```
https://www.docker.com/get-started
```
- Clone this repository on your local computer
- Run the docker-compose up -d
```
git clone https://github.com/hxl20081219/docker-centos-lamp.git
cd docker-centos-lamp/
docker-compose up -d
// visit localhost
```
Your LAMP is now ready!! You can access it via http://localhost.

# Configuration and Usage

## General Information
This Docker Stack is build for local development and not for production usage.

---
## PHP
PHP_INI Define your custom php.ini modification to meet your requirments.

### Extensions
- mysqli
- pdo_sqlite
- pdo_mysql
- mbstring
- zip
- mcrypt
- curl
- json
- gd
- pear

> If you want to install more extension, just update .Dockerfile. You can also generate a PR and we will merge if it seems good for general purpose. You have to rebuild the docker image by running docker-compose build and restart the docker containers.

---

## apache
Apache is configured to run on port 80. So, you can access it via http://localhost.

### Apache Modules
By default following modules are enabled.
- rewrite
- headers

### Connect via SSH
You can connect to web server using docker-compose exec command to perform various operation on it. Use below command to login to container via ssh.
```
docker-compose exec centos bash
```
### DOCUMENT_ROOT
It is a document root for Apache server. The default value for this is ./www. All your sites will go here and will be synced automatically.

### VHOSTS_DIR
This is for virtual hosts. The default value for this is ./config/httpd/conf.d. You can place your virtual hosts conf files here.

### APACHE_LOG_DIR
This will be used to store Apache logs. The default value for this is ./logs/httpd.

---
## Database

### MYSQL_DATA_DIR
This is MySQL data directory. The default value for this is ./data/mysql. All your MySQL data files will be stored here.

### MYSQL_LOG_DIR
This will be used to store mysql logs. The default value for this is ./logs/mysql.

### connect
use host:mysql
---

## Redis
It comes with Redis. It runs on default port 6379.

### connect
use host:redis
