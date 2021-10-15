# Django Documentation

### Virtual Enviroment (LINUX)

Creating an enviroment

	$ python3 -m venv enviroment_name
Activating the virtual enviroment

	$ source enviroment_name/bin/activate
Desactive the virtual enviroment

	$ deactivate

### Installing Django

Installing a specific version (in this case version=3.2.1)

	$ pip install Django==3.2.1

Creating a new django project

	$ django-admin startproject my_project_name .
the "."  it tell django to do not create another folder with the name of project

### Anatomy of a Django Project
- __ini__.py : Indicates that the project folder is a python package
- setting.py : Setting configuration for the project
- urls.py : Entry point, basically the URL declarations for ou Django project (it's kind of like postaman). Collect the request and the look for a matching addres to delivery that request to.
- wsgi.py : (Web Server Gateway Interface)It's an entry point fo wsgi compatible web services
- manage.py : script that helps as with the management of our site. 



### Running the server:

	$ python3 manage.py runserver
or I can specified the server like this

	$ python3 manage.py runserver 8080
### Migrations

- Migrate : Applies and unapples migrations
- makemigrations: Creates new migrations based on changes you make to your models.
- sqlmigrate : Display the SQL statements for a migration
- showmigrations: list a projects migrations and their status

For defautl Django create some tables for the project so to star we need to aplied migrations
to this tables.

### Creating a Django App

	$ django-admin startapp name_of_the_app
by convention app names are plural

### Activating the App
To active the app so the project is aware of it, you need to add it to the list of installed
apps inside settings.py file.

### Anatomy if django App
- migrations: all the database migrations of the app
- __init__.py: indicates that the folder is a package
- admin.py: where you register any models that your apps has, so that it's included into the Django Administration site
- apps.py: 
