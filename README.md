## Udacity-Linux-Server-Configuration
# By Apuroop Kanda
# About
This is the Udacity project 6 about the Configuring the Linux the server.

# Server Details
Server IP Address 13.232.131.253

Hosted site Url http://13.232.131.253.xip.io/

# How to connect as grader:
save private key provided in your local machine and run the following command

ssh -i path/to/privatekey -p 2200 grader@13.232.131.253
  
## Configuring Linux Server
# Updating all packages

sudo apt-get update
sudo apt-get upgrade
# Creating grader User:

sudo adduser grader

This will add new user

password for grader: apuroop123

sudo nano /etc/sudoers

Below the Root user append the following line

grader  ALL=(ALL:ALL) ALL
This will grant sudo permission to grader

open puttygen load atext.pem file and save private key which is saved as private.ppk 

# Creating a ssh key pair for grader
On your local machine in terminal/command prompt

ssh-keygen

This will generate public and private ssh keys which is saved to .ssh folder
# id_rsa:
-----BEGIN RSA PRIVATE KEY-----
MIIEowIBAAKCAQEAzqQ7azUqMAWXcio8wvY2fQQRafU9wM27nEKy9NRwBiVP73DP
8cO+NO2Vfokvtv3UQBmi6p0FgvBnENwMAQ5MzfBQBA5lKc1Xn+EJiE3qMV35t//2
Dk1E43jU3G6BZQY0wiYRS6CupWSOHRmlU6aCbQvzEOlaQSsooLAHZ5ZmRdp8fl0N
XhpDCkevNxlEa9CEuFYsBBis6cmXVwWwTrYtBZ3cQ3nsmI0xykuYlCG73kPABqqE
hvAF+zidDCbzVsrKMP6Ezcd/IpKBhrUcRvNzcQA6ehAWNJ5kr04BM441TS+xePak
O7FGhll1g9TCCnp5UF9qE9EnBchayPHDzHbI8QIDAQABAoIBAGL1YYM45agztVA2
C/0t3fBGt3QvvtALdlIh2wPGjJNU4RAAzYSxQfCk6pe7aP9QVYoQ/OUwJ0iKikEX
sCP9Tii9cgRPRIEdVl45bdA5x/K2V3WXfaVhuaDZ585cmVjg/PkRM+0s2RZZrnkf
I/6IWiOQummZ5uAYpA833YPtEbNXTgNzqjmTfQbqzOtYcQkf9UK6L3I+Y4dD5ARA
JPsuLWejxdI5jiDXH9PLgLEoml/VpStMDCpJjyAirFOOQs6YRZI2WsrmCpscGiuc
jmeeZbL9v2jbkhFWSt6QEQYXZ7MbzhjhCi87l1q2gh+AaIlFMKCSoqCMt7D/ggO+
UZW2l/ECgYEA//ZAcYL7+AlyzZSpYIOcGIfsm2CZMCiQepFla+kUxqHByzhCq5Dh
eRKgYrPh/zgYPXr2FPfH2z6BF3bOztDndeS9vwU6ED2zm9Lu1m/aa9nLXQsUEzT+
VNxlwh2OdICAwvuiZlIJOnIjT7pgsBzR2O1DZRyDKn396RorcSs6cvUCgYEAzqwa
HZAUFX3X8QZvoEqAgXkBAIV/r1iJKRqV5/yDUjphjFmAWiAGWqNUz19pFlycs4kk
T2cLUCec5wvybttUVwKXA5XLVsHGRyMZqMWtMdTTw3tf7KyaT0KbP/1zq6tZxfgn
CVtB63MNIwFhRsuCMVOcBZe0XkAyf/JkPCp0mI0CgYEA1XwJEePizmTrCMZ2YtZC
aj9sO8fc3MrofiIoylE0D9u4bAv3p2sGc9nyRYCs/RZHOXgGKUTkv1sphm2EXgDl
HHJ1RA5S+FrOJChRJi9SqOOVd3wW+VIY0qSkhrvqJgdL3dTNBbRkmAe8pfHYVOsk
p150+K9IQzekgDhghVo9vMUCgYBL2TWsa9gzGwBJYMdO2IjY+4O2oUf/HksYXr1t
amr3np12WNKWQPKUCSVzBd0Xa93GtioxSewI+sDGuse6j5wgYr7xfeQmbu9J5EPi
gMnTY/xj3b+SqLXpKNS5Y1c0Raqo0S3ibS+ALbVAh50f0khxufGky8xSWtUtx9Op
kRtBcQKBgGD6bvh0r1aa3Ol1YbizufhpN27ggiBj/8z6Vq8Z5vxE7GiRowH+48Cf
WIC7eezFHIH9g2PCcTmsJlvhktn/3fxq2QCxrtS0K46ZZWvyWtsT264nkGye83FG
fRz7acP/qen4DdZzn3yEsn1PLQV1etPwQVQcJiUr+WK2hJLLIZmK
-----END RSA PRIVATE KEY-----



Then in your virtual machine change to newly created user


su - grader
Create a new directory .ssh and new file authorized_keys in that directory

mkdir .ssh
sudo nano .ssh/authorized_keys
Copy the public key with .pub extension to authorized_keys and save the file
# id_rsa.pub file:

ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDOpDtrNSowBZdyKjzC9jZ9BBFp9T3AzbucQrL01HAGJU/vcM/xw7407ZV+iS+2/dRAGaLqnQWC8GcQ3AwBDkzN8FAEDmUpzVef4QmITeoxXfm3//YOTUTjeNTcboFlBjTCJhFLoK6lZI4dGaVTpoJtC/MQ6VpBKyigsAdnlmZF2nx+XQ1eGkMKR683GURr0IS4ViwEGKzpyZdXBbBOti0FndxDeeyYjTHKS5iUIbveQ8AGqoSG8AX7OJ0MJvNWysow/oTNx38ikoGGtRxG83NxADp6EBY0nmSvTgEzjjVNL7F49qQ7sUaGWXWD1MIKenlQX2oT0ScFyFrI8cPMdsjx hp@DESKTOP-E82NM60


chmod 700 .ssh
chmod 644 .ssh/authorized_keys
700 will give read write and execute permission to user.
644 prevent other user from writting in to file. Then restart ssh server
service ssh restart
Now from your log in to grader with private key generated

ssh -i .ssh/id_rsa grader@13.232.131.253 
# Changing the ssh port to 2200

sudo nano /etc/ssh/sshd_config
Change port 22 to port 2200

Restart the ssh server

service ssh restart
Note: Before Logging using ssh add custom TCP port 2200 under lightsaail firewall in networking tab in lightsail instance console

Now Login using command like this

ssh -i .ssh/id_rsa -p 2200 grader@13.232.131.253
# Disabling ssh login as root

sudo nano /etc/ssh/sshd_config

make change PermitRootLogin no

# Configurating Ufw firewall

sudo ufw allow 2200/tcp
sudo ufw allow 80/tcp
sudo ufw allow 123/udp
sudo ufw enable

This will allow all required ports and enables the ufw

After that

sudo ufw status

It will display all allowed ports

select none from list and then select utc.

Installing Apache2
In terminal

sudo apt-get install apache2

Now mod_wsgi

sudo apt-get install python-setuptools libapache2-mod-wsgi

Enable mod_wsgi

sudo a2enmod wsgi

# Setting up your flask application to work with apache2
Creating a flask app

In /var/www directory create a new folder sudo mkdir FlaskApp

Install git

sudo apt-get install git

move to the FlaskApp cd FlaskApp

In that direcory clone your github repository

sudo git clone https://github.com/apuroopkanda/catalog.git


Rename your repository to FlaskApp

Then rename your project file to __init__.py

Error : While accesssing the client_secrets.json file

PROJECT_ROOT = os.path.realpath(os.path.dirname(__file__))
json_url = os.path.join(PROJECT_ROOT, 'client_secrets.json')
CLIENT_ID = json.load(open(json_url))['web']['client_id']

Use json_url instead client_secrets.json in script

Reffered from stack overflow

Install and configuring postgresql for project
Install Postgres sudo apt-get install postgresql

login to postgres sudo su - postgres

postgres shell psql

create user CREATE USER catalog WITH PASSWORD 'password';

permit user to createdb ALTER USER catalog CREATEDB;

Create a db name catalog with user catalog CREATE DATABASE catalog WITH OWNER catalog;

connect to db \c catalog

revoke all permission to public REVOKE ALL ON SCHEMA public FROM public;

Give schema permission to user catalog GRANT ALL ON SCHEMA public TO catalog;

exit from db and postgres \q and exit

Change the database connection in both db_setup.py and __init__.py as engine = create_engine('postgresql://catalog:password@localhost/catalog')

Now you are ready with your applicatiom

# Configure and Enable a New Virtual Host
sudo nano /etc/apache2/sites-available/FlaskApp.conf

In this add the following code

<VirtualHost *:80>
 	ServerName 13.232.131.253
 	ServerAdmin admin@13.232.131.253
 	WSGIScriptAlias / /var/www/FlaskApp/flaskapp.wsgi
 	<Directory /var/www/FlaskApp/FlaskApp/>
 		Order allow,deny
 		Allow from all
 	</Directory>
 	Alias /static /var/www/FlaskApp/FlaskApp/static
 	<Directory /var/www/FlaskApp/FlaskApp/static/>
 		Order allow,deny
 		Allow from all
 	</Directory>
 	ErrorLog ${APACHE_LOG_DIR}/error.log
 	LogLevel warn
 	CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
Enable the virtual host sudo a2ensite FlaskApp

Disabling the default apache2 page sudo a2dissite 000-default.conf

Create the .wsgi File
```
cd /var/www/FlaskApp
sudo nano flaskapp.wsgi 
```
Add the following code

#!/usr/bin/python
 import sys
 import logging
 logging.basicConfig(stream=sys.stderr)
 sys.path.insert(0,"/var/www/FlaskApp/")

 from FlaskApp import app as application
 application.secret_key = 'BgMPNFe2g0nhCpBKjcOcbv8F'
save and exit

Deploying flask app with apache2 is referred from Digital ocean

# Installing require modules
You can either install all modules on your machine or create a virtual environment for the project and install the modules pip install flask sqlalchemy psycopg2 requests oauth2client

# Setting up your Google Oauth2
Login to your developer console and select your project and edit OAuth details as following

Javascript origin http://ip.xip.io

redirect URI

http://ip.xip.io\login

http://ip.xip.io\gconnect

http://ip.xip.io\callback

xip.io is a free DNS which will be the same as using IP address

Final Step
Restart your apache2 server

sudo service apache2 restart

go to chrome and run project as
http://13.252.131.253.xip.io  and application will run.

