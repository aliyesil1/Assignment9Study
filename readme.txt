# Compose and Django
# This quick-start guide demonstrates how to use Docker Compose to set up and run a simple Django/PostgreSQL app.
# For this project, you need to create a Dockerfile, a Python dependencies file, and a docker-compose.yml file. (You can use either a .yml or .yaml extension for this file.)
# 1- Create an empty project directory.
# 2- Create a new file called Dockerfile in your project directory.
# 3- Add the following content to the Dockerfile. 
#     FROM python:3
#     ENV PYTHONDONTWRITEBYTECODE=1
#     ENV PYTHONUNBUFFERED=1
#     WORKDIR /code
#     COPY requirements.txt /code/
#     RUN pip install -r requirements.txt
#     COPY . /code/
# 4- Save and close the Dockerfile.
# 5- Create a requirements.txt in your project directory.
# 6- Add the required software in the file.
#     Django>=3.0,<4.0
#     psycopg2>=2.8
# 7- Save and close the requirements.txt file.
# 8- Create a file called docker-compose.yml in your project directory and add the following configuration to the file.
#     services:
#   db:
#     image: postgres
#     volumes:
#       - ./data/db:/var/lib/postgresql/data
#     environment:
#       - POSTGRES_DB=postgres
#       - POSTGRES_USER=postgres
#       - POSTGRES_PASSWORD=postgres
#   web:
#     build: .
#     command: python manage.py runserver 0.0.0.0:8000
#     volumes:
#       - .:/code
#     ports:
#       - "8000:8000"
#     environment:
#       - POSTGRES_NAME=postgres
#       - POSTGRES_USER=postgres
#       - POSTGRES_PASSWORD=postgres
#     depends_on:
#       - db
# 9- Save and close the docker-compose.yml file.
# 10- Run the docker compose run command. 