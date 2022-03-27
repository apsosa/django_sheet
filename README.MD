# Django Documentation

### Virtual Enviroment (LINUX)

Creating an enviroment

	python3 -m venv enviroment_name
Activating the virtual enviroment

	source enviroment_name/bin/activate
Desactive the virtual enviroment

	deactivate

### Installing Django

Installing a specific version (in this case version=3.2.1)

	pip install Django==3.2.1

Creating a new django project

	django-admin startproject my_project_name .
the "."  it tell django to do not create another folder with the name of project

### Anatomy of a Django Project
- __ini__.py : Indicates that the project folder is a python package
- setting.py : Setting configuration for the project
- urls.py : Entry point, basically the URL declarations for ou Django project (it's kind of like postaman). Collect the request and the look for a matching addres to delivery that request to.
- wsgi.py : (Web Server Gateway Interface)It's an entry point fo wsgi compatible web services
- manage.py : script that helps as with the management of our site. 



### Running the server:

	python3 manage.py runserver
or I can specified the server like this

	python3 manage.py runserver 8080
### Migrations

- Migrate : Applies and unapples migrations
- makemigrations: Creates new migrations based on changes you make to your models.
- sqlmigrate : Display the SQL statements for a migration
- showmigrations: list a projects migrations and their status

For defautl Django create some tables for the project so to star we need to aplied migrations
to this tables.

### Creating a Django App

	django-admin startapp name_of_the_app
by convention app names are plural

### Activating the App
To active the app so the project is aware of it, you need to add it to the list of installed
apps inside settings.py file.

### Anatomy of django App
- migrations: all the database migrations of the app
- __init__.py: indicates that the folder is a python package
- admin.py: where you register any models that your apps has, so that it's included into the Django Administration site
- apps.py: Configuration file for the app, basically is created to help include any application configuration for the app so you can use it to configure some of the attributes of the application. So the appplication configuration object basically stores metadata for your application. Metadata is basically data about data, information about information.
- models.py: where your models live. Constains fields and behaviour about you data.
- test.py: allow you to add an unit testing you want for your application.

### Django Porjects vs Apps

A Django app is web application that does something, 
Example: 
- a componente as a login, facebook timeline etc

A Django project is a collections of configuration and apps for a website who's can contain multiple apps.
 It could be the entire facebook it self

### Django Architecture

Django uses an MVC type of architecture. MVC stands for Model View Controller, django call these pieces by different names.
URL Patters, Views, Templates, Models, so this is Django own version of the MVC implementation.
For example:
- The URL Patterns: takes the path of a request and then  decide when the reques comes in. It takes the path of the request and then decides which views should handle the requests.So once a request comes in, he has to look at the pattern of the URL and determines which views should handle the request.
- The views: is the logic layer of the program or the app.What patterns?They are also a python functions.They take a request and return and http response.
- Models:it each of the views can use the model that we have defined in the application to query the data.
- Templates:So once the view queries use queries, the data provide by the model.He then uses the template to display the data that you can see.

### Django Admin and SuperUser
Django comes with a buit-in administrative interface page.This super user account, it gives you full access to manage the django admin site.You can add content, you can delete content, you can modify content from the django admin interface page.
To create a superuser account do the next:

	python manage.py createsuperuser

### Templates
Templates in Django can consist of static parts of the desired HTML output.
It can also contain special syntax that you can use to describe how dynamic content should be inserted so you can have a static HTML template. And within that template, you can inject dynamic content using special syntax that Django has.
Example of templates folders:
	APP_DIRECTORY(app folder)
		templates
			app directory name
				add index.html
		static
			app directory name
				add bs and CSS

### Models

In this video, I'm going to introduce you to Django module's what are Django models?
Django models are Python classes that allows us to save data inside a database table.
Now, each object is a rule in a table. So what that means is that each instance of a class can be stored as a row in a table.
A model is the single definitive source of information about your data.
So anything relating to data in your Django project will be found in the model modules contains the
essential fields and behaviour's of the data that you are storing.
Generally, each module will map to a single database table.Each module is a python class that also has subclasses, so it will have a subclass called Django DB
to modules DOT modules. So there is a difference between this module here in uppercase and this one as well.
Each attribute of the module represents a database field.

Example:

	# Create your models here.
	class Todolist(models.Model):
    	text = models.CharField(max_length=45)
    	completed = models.BooleanField(default=False)

    	def __str__(self):
        	return self.text

### Migrating Models

When you create a model, you have to do two things.
You first all have to create migration files, which creates the files that you can then run the migration on.
So the command you need to create migration files is this:

	python manage.py makemigrations
They make Migration Command will create the migration files and then you need to run another command, which is:

	python manage.py migrate
This Command is what actually creates the table inside the database with the field you have specified in the model.


### Add Model to the ADMIN site
In the admin.py file of your:
- Import your models. Example:

	from .models import Todolist
- Register your models. Example:

	admin.site.register(Todolist)


### Installing django extensions

	pip install django-extensions
and then add to the project settings in the installed apps


INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'django_extensions',
]

to active shell pluss with Ipython install first Ipython

	pip install ipython
and then add to the project settings


SHELL_PLUS = "ipython"
SHELL_PLUS_PRINT_SQL = True
SHELL_PLUS_PRINT_SQL_TRUNCATE = None

	
