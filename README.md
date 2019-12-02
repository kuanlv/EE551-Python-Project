# EE551-Python-Project
## Introduction:
This project is about developing a web application which uses django as its framwork and postgresql as database. 

The application is designed for a real estate company(in this project its called KLre) so the company can post imformation about houses that are avaliable and also information about realtors who are working in this company. So this app is targeted at users who want to buy a house.

**Note**: This project doesn't include the design of the user interface, so the main focus is on backend.

**Reference:** I finished this project by following this [online tutorial](https://www.udemy.com/course/python-django-dev-to-deployment/) 

### Folder structure:
**KLre**: the main application in project.

**accounts, contacts, listings, pages, realtors**: They are all applications.

**templates**: Include all the template html file catagorized by each applications and a base template file.

## How to import the project:
### Step 0:
I assumed you have Python3 installed and you know how to setup virtual enviroment.

### Step 1:
Clone this repo into your local machine and in your terminal type:
```bash
cd EE551-Python-Project
cd DJANGO
cd project
```
Then set up your virtual enviroment
```bash
mkvirtualenv env
```
```bash
workon env
```
And next you need to install all the dependencies and libaries which I used
```bash
pip install -r requirements.txt
```
### Step 3: Set up database
Install [postgresql](https://www.postgresql.org/download/ "click here to install it") if you don't have it. Also install [Pgadmin](https://www.pgadmin.org/download/ "click here to install pgadmin") if you need a user interface for the database.

Next open postgres by clicking the little elephant icon and initailize the database. Then double click the database icon which is called postgres and now your terminal should be opened(not the one in virtual envirament).
```bash
The default interactive shell is now zsh.
To update your account to use zsh, please run `chsh -s /bin/zsh`.
For more details, please visit https://support.apple.com/kb/HT208050.
Users-MBP:~ Users$ /Applications/Postgres.app/Contents/Versions/12/bin/psql -p5432 "postgres"
psql (12.1)
Type "help" for help.

postgres=# 
```


Now navigate to KLre folder and open settings.py in that folder and on line 82 you should see 
```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'klre',
        'USER': 'postgres',
        'PASSWORD': '1023',
        'HOST': 'localhost'
    }
}
```
Now swich to terminal and type:
```bash
postgres=# \password postgres
```
and
```bash
postgres=# CREATE DATABASE klre OWNER postgres;
CREATE DATABASE
```
### Step 4:
In your virtual enviroment type in terminal(make sure you are in project folder):
```bash
python manage.py migrate
```
Now you can open PgAdmin and check your database that all the tables and fields have already been created.

Then you can start your server by typing
```bash
python manage.py runserver
```
And if you go to http://localhost:8000 you should see the beautiful UI but without any listing.

### Step 5:
To make the application officailly yours, you need to have access to the admin area. Go to localhost:8000/admin and you will see a login form. 

In your terminal, stop the server first if it's running by cmd/ctrl + c and type:
```bash
python manage.py createsuperuser
```
and then give it a username and a password then restart the server. At this point you are all set!

Log in to the admin area and post your first listing and realtor there!





