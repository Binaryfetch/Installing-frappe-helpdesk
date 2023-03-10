# Installing Frappe Helpdesk
<br>
FrappeDesk offers an easy setup, clean user interface, and automation tools to resolve customer issues efficiently. It is based on Frappe Framework. It lets you streamline your company's support and helps you to efficiently manage your customer queries. It can help you to,

- Create tickets from email or help center
- Empower customers with a comprehensive knowledge base and self-service portal
- Automate redundant tasks like agent assignment and set up triggers to notify agents and customers based on certain events

## Commands for ubuntu 22.04 LTS 

## Install the frappe bench 
## If done then [click here](https://binaryfetch.github.io/Installing-frappe-helpdesk/##now-download-the-helpdesk-app)

## Pre-requisites
``` python 
  Python 3.6+
  Node.js 14.18.0 =+
  Redis 5                                       (caching and real time updates)
  MariaDB 10.3.x / Postgres 9.5.x               (to run database driven apps)
  yarn 1.12+                                    (js dependency manager)
  pip 20+                                       (py dependency manager)
  wkhtmltopdf (version 0.12.5 with patched qt)  (for pdf generation)
  cron                                          (bench's scheduled jobs: automated certificate renewal, scheduled backups)
  NGINX                                         (proxying multitenant sites in production)
```

### Step 1 Install git
``` java 
sudo apt-get install git 
```
### Step 2 install python-dev
``` python
sudo apt-get install python3-dev
```
### Step 3 Install setuptools and pip (Python's Package Manager).
``` java
sudo apt-get install python3-setuptools python3-pip
```
### Step 4 Install virtualenv
``` java
sudo apt-get install virtualenv
```
### check python version
``` python 
python3 --version
```
#### If Version is 3.8.X RUN
``` python
sudo apt install python3.8-venv
```
#### If Version is 3.10.X Run
``` python 
sudo apt install python3.10-venv
```
### Step 5 Install MariaDB
``` python 
sudo apt-get install software-properties-common
sudo apt install mariadb-server
sudo mysql_secure_installation
```
### Step 6 MySQL database development files
``` python 
sudo apt-get install libmysqlclient-dev
```

### Step 7 Edit the mariadb configuration ( unicode character encoding )
``` python 
sudo nano /etc/mysql/mariadb.conf.d/50-server.cnf
```
#### add this to the 50-server.cnf file
``` python 
[server]
 user = mysql
 pid-file = /run/mysqld/mysqld.pid
 socket = /run/mysqld/mysqld.sock
 basedir = /usr
 datadir = /var/lib/mysql
 tmpdir = /tmp
 lc-messages-dir = /usr/share/mysql
 bind-address = 127.0.0.1
 query_cache_size = 16M
 log_error = /var/log/mysql/error.log

[mysqld]
 innodb-file-format=barracuda
 innodb-file-per-table=1
 innodb-large-prefix=1
 character-set-client-handshake = FALSE
 character-set-server = utf8mb4
 collation-server = utf8mb4_unicode_ci      
 
[mysql]
 default-character-set = utf8mb4
```
#### Now press (Ctrl+o) to save then press (ctrl+x) to exit


#### Then run
``` python 
sudo service mysql restart
```
### Step 8 install Redis
``` python 
sudo apt-get install redis-server
```
### Step 9 install Node.js 14.X package
``` python 
sudo apt install curl 
curl https://raw.githubusercontent.com/creationix/nvm/master/install.sh | bash
source ~/.profile
nvm install 14.18.0  
```
### Step 10 install Yarn
``` python 
sudo apt-get install npm

sudo npm install -g yarn
```

### Step 11 install wkhtmltopdf
``` python 
sudo apt-get install xvfb libfontconfig wkhtmltopdf
```

### Step 12 install frappe-bench
``` python 
sudo -H pip3 install frappe-bench

bench --version
```
####Bench version should be 5.16.X

### Step 13 initilise the frappe bench & install frappe latest version
``` python 
bench init frappe-bench 

cd frappe-bench/
bench start
```
## Now Download the Helpdesk app

### In a separate terminal window, create a new site by running
``` python 
cd frappe-bench/
bench new-site frappedesk.test
```
### Map your site to localhost with the command
``` python 
bench --site frappedesk.test add-to-hosts
```
### Get the Frappe helpDesk app , Run
``` python 
bench get-app https://github.com/frappe/desk
```
### Then Run 
``` python 
bench --site frappedesk.test install-app frappedesk
```

### Now open the URL in your browser, you should see the app running
``` python 
http://frappedesk.test:8000/frappedesk
```

Login 
email - Administrator <br>
password - {passowrd enter for administrator after command of get the frappe desk app}
