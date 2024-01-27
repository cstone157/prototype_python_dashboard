# prototype_python_dashboard
A Prototype of a dashboard using Postgresql and dash/python.  Deployed using docker.

## Pulled instructions from
### https://dockerize.io/guides/python-django-guide

## Steps
01.) $ apt install python3.10-venv -- Install venv so we can have different python enviroments
02.) $ python3 -m venv django-dashboard -- Setup our virtual enviroment
03.) $ source django-dashboard/bin/activate -- Activate our virtual enviroment (there will we a new directory in our working directory)
04.) Make a requirements document with the line "Django==2.2.5" included
05.) $ pip install -r requirements.txt
06.) $ django-admin startporject mysite -- Makes the django site/project
07.) $ cd mysite && python manage.py runserver

08.) ()