FROM nginx:1.9

LABEL Justin Simon <contact@jsimon.me>

RUN usermod -u 1000 www-data

ADD config/* /etc/nginx/conf.d/

WORKDIR /var/www/html

EXPOSE 443

CMD ["nginx", "-g", "daemon off;"]