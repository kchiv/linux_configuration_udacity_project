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
  - Python scripts
