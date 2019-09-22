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
