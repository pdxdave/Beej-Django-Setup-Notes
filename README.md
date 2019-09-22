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
Again, this inside of the project.  The app is called notes. Make sure you're in the root folder. This does not go inside the djorg folder.
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
Migrations are the glue b/t the Django models and the SQL underneath them. The data in Django will be represented in a SQL database.  We need SQL commands to set that database up based on what our models look like. The models will be objects with fields in them.  The fields in the model get translated by Django into SQL statements that build tables. The fields that are objects become columns in our table. We need a little piece of software to make that happen. That software is migrations.
```
./manage.py showmigrations
```
Will show what migrations exists and if they've been applied. 'X' in the box means they've been applied.
```
admin
 [ ] 0001_initial
 [ ] 0002_logentry_remove_auto_add
 [ ] 0003_logentry_add_action_flag_choices
auth
 [ ] 0001_initial
 [ ] 0002_alter_permission_name_max_length
 [ ] 0003_alter_user_email_max_length
 [ ] 0004_alter_user_username_opts
 [ ] 0005_alter_user_last_login_null
 [ ] 0006_require_contenttypes_0002
 [ ] 0007_alter_validators_add_error_messages
 [ ] 0008_alter_user_username_max_length
 [ ] 0009_alter_user_last_name_max_length
 [ ] 0010_alter_group_name_max_length
 [ ] 0011_update_proxy_permissions
contenttypes
 [ ] 0001_initial
 [ ] 0002_remove_content_type_name
sessions
 [ ] 0001_initial
 ```

### Create a model
In the Notes folder (e.g.,our app) look for the models.py file.  The model will represent our data.    
```
from django.db import models
from uuid import uuid4

# Create your models here.

class Note(models.Model):
    id = models.UUIDField(primary_key=True, default=uuid4, editable=False)
    title = models.CharField(max_length=200)
    content = models.TextField(blank=True)
```

#### Tell Django what apps are installed
Now we need to tell Django what apps are installed. This is done in the project folder inside of the settings.py file.  In the INSTALLED_APPS array add 'notes'
```
INSTALLED_APPS = [
    'notes',
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
]
```
### Setup Migrations
Finally the migrations need to be setup.  It will appear in the notes > migrations folder. In the root folder type:
```
./manage.py makemigrations
```
You'll get an Operations to perform notification with the notes listed.

Next, type in the following to migrate the notes:
```
./manage.py migrate
```
