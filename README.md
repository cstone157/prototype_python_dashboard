# prototype_python_dashboard
A Prototype of a dashboard using Postgresql and dash/python.  Deployed using docker.

## Pulled instructions from
##### https://dockerize.io/guides/python-django-guide

## Steps
##### 01.) $ apt install python3.10-venv -- Install venv so we can have different python enviroments
##### 02.) $ python3 -m venv django-dashboard -- Setup our virtual enviroment
##### 03.) $ source django-dashboard/bin/activate -- Activate our virtual enviroment (there will we a new directory in our working directory)
##### 04.) Make a requirements document with the line "Django==2.2.5" included
##### 05.) $ pip install -r requirements.txt
##### 06.) $ django-admin startporject mysite -- Makes the django site/project
##### 07.) $ cd mysite && python manage.py runserver -- Starts the server
##### 
##### 08.) $ python manage.py startapp hello_world -- Add the actaul app we will be modifying
##### 09.) Modify the mysite/settings.py and add "'hello_world'" into the list of the installed apps
##### 10.) Modify hello_world/views.py and add
###### from django.shortcuts import render
###### 
###### def hello_world(request):
######     return render(request, 'hello_world.html', {})
###### 
##### and add a folder "templates" in app and add a "hello_world.html" there, and modify it to include:
####### <code><h1>Hello, World!</h1></code>
###### 
###### go to the mysite/urls.py, import include from django.urls and add the path to urlpatters 'path('', include('hello_world.urls')),'
###### 
###### Add a "urls.py" to "hello_world" folder, and insert into it:
####### '''
####### from django.urls import path
####### from hello_world import views
####### 
####### urlpatterns = [
#######     path('', views.hello_world, name='hello_world'),
####### ]
####### '''
###### 
###### If you restart the server you should go to hello_world.html.
###### 
###### 
11.)  Dockerize the project by adding Dockerfile containing
'''
# Dockerfile

# The first instruction is what image we want to base our container on
# We Use an official Python runtime as a parent image
FROM python:3.7

# Allows docker to cache installed dependencies between builds
COPY requirements.txt requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

# Mounts the application code to the image
COPY . code
WORKDIR /code

EXPOSE 8000

# runs the production server
ENTRYPOINT ["python", "mysite/manage.py"]
CMD ["runserver", "0.0.0.0:8000"]
'''

BUILD
$ docker build -t python-django-app .

RUN
$ docker run -it -p 8000:8000 python-django-app

RUN and BUILD using docker-compose
docker-compose up -d --build