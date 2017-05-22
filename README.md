# linux_configuration_udacity_project

The final Udacity project. In this project I configured an Ubuntu Linux server so that it hosts a web application that utilizes the Flask framework.

## Server Details

**IP Address:** 52.206.36.27

**App URL:** http://ec2-52-206-36-27.compute-1.amazonaws.com/

**App Repository:** https://github.com/kchiv/instrument_db

## Software Summary

### Updated & Installed Packages

Updated the list of available packages:
```
sudo apt-get update
```
Install the new packages:
```
sudo apt-get upgrade
```
### Other Software

- Apache 2 webserver
- mod_wsgi to host the Python web app
- Postgresql database
- Git for downloading the item catalog repository
- Pip for managing Python packages
- Flask framework for our app

### Additional Python Libraries

- httplib2
- requests
- flask-seasurf
- oauth2client
- sqlalchemy
- psycopg2

## Configurations

- Created 'grader' user and granted user 'sudo' permissions
- Changed ssh port to 2200 from 22
- Configured UFW to onlly allow connections for SSH (port 2200), HTTP (port 80), and NTP (port 123)
- Configured ssh login to use a public key and private key
- Updated all system packages to their most recent versions
- Installed apache2 and mod_wsgi in order to host the Python app
- Installed postgresql and created a database called 'catalog'
  - Python scripts were later run to create tables and populate the tables with data
- Installed git and then cloned the item catalog repository onto the server
- Configured the virtual host with the FlaskApp.conf file containing the following code:
```
<VirtualHost *:80>
        ServerName 52.206.36.27
        ServerAdmin chiverskyle@gmail.com
        ServerAlias ec2-52-206-36-27.compute-1.amazonaws.com
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
```
- Created flaskapp.wsgi file to serve the Flask app

## Resources
- https://www.youtube.com/watch?v=HcwK8IWc-a8
- https://www.digitalocean.com/community/tutorials/how-to-configure-the-apache-web-server-on-an-ubuntu-or-debian-vps
- https://www.cyberciti.biz/faq/how-do-i-update-ubuntu-linux-softwares/
- http://flask.pocoo.org/docs/0.12/deploying/mod_wsgi/
- https://www.digitalocean.com/community/tutorials/how-to-deploy-a-flask-application-on-an-ubuntu-vps
