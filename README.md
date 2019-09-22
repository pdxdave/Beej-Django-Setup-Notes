# Beej-Django-Setup-Notes
Beej Django Setup Notes

### Setup
In the main folder type the following:    
1. pipenv --three   // installes Pip version three    
2. pipenv shell // creates the Pip shell    
3. pipenv install django // installs django into the virtual environment    


### Start a project

The Django environment consists of a project.  Inside of the project are apps.  One project.  Potentially multiple apps.    
The following line creates a new project.  The last item in the line is the name of the project. The period at the end puts it into the current directry.
```
django-admin startproject djorg .
```

### Create an app    
Again, this inside of the project.  The app is called notes. Make sure you're inside of the djorg folder.  That's your project folder.
```
django-admin startapp notes
```

### Start the server
In the root folder there will be a file called manage.py.  Make sure you're in the root folder and type:
```
python manage.py runserver
```
It's likely you'll get a message regardging a bunch of unapplied migrations.  Stop the server. Run the the following:
```
python manage.py migrate
```

#### Migrations
Migrations are the glue b/t the Django models and the SQL underneath them. The data in Django will be represented in a SQL database.  We need SQL commands to set that database up based on what our models look like. The models will be objects with fields in them.  The fields in the model get transalted by Django into SQL statements that build tables. The fields that are objects become columns in our table. 
