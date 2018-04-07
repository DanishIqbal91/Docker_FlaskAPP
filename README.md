### A Simple Flask Blog

This is a simple Flask Blog, as seen in the [Fromzero](http://fromzero.io) course.

1) DB Container
#docker run --name db -e MYSQL_ROOT_PASSSWORD=test -d -p 3306:3306 mariadb

2)Connect DB Container using Clinet
#docker run --name mysql-client -it --link db:mysql --rm mariadb sh -c 'exec mysql -uroot -ptest -hmysql'

3)Build Docker image for web using Dockerfile
#docker build -t flask_blog .

4)Link web container and db container 
#docker run -id -p 5000:5000 -v /home/user/app:/opt/flask_blog --name blog --link db:mysql flask_blog bash

5)Login to db container 
#docker exec -it db /bin/bash
#export TERM=${TERM:-dumb}
#create database
#mysql -u root -p
#create database blog;

6)login to web(blog) container
#docker exec -it blog bash
#python manage.py db init
If output Error like this(alembic.util.exc.CommandError: Directory migrations already exists)
then remove migration dir

If Error like this (alembic util command error can't find identifier) then
"https://stackoverflow.com/questions/32311366/alembic-util-command-error-cant-find-identifier"


#python manage.py db migrate 
#python manage.py db upgrade
#python manage.py runserver

Accecs on your machine IP and Port(5000)
xxx.xxx.xxx.xxx:5000/setup

