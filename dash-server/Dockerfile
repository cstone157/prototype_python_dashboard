# pull the official base image
FROM python:3.9-alpine

# set the working directory
WORKDIR /app

# set enviroment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# install psycopg2 dependencies
RUN apk update & apk add postgresql-dev gcc python3-dev musl-dev

# install dependencies
COPY ./requirements.txt /usr/src/app
RUN pip install --upgrade pip
RUN pip install --no-cache-dir -r requirements.txt

# copy project
COPY . .

EXPOSE 8000

CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]