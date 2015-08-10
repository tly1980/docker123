FROM ubuntu:14.04

RUN apt-get install nginx -y
#RUN apt-get install vim -y
RUN mkdir -p /usr/share/nginx/html/a
RUN echo "hello" > /usr/share/nginx/html/a/hello.txt
RUN echo "world" > /usr/share/nginx/html/a/world.txt
COPY my_nginx.conf /etc/my_nginx.conf