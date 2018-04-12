FROM nginx:1.9

MAINTAINER Imagination Media <rafael@imaginationmedia.com>

RUN usermod -u 1000 www-data

ADD config/* /etc/nginx/conf.d/

WORKDIR /var/www/html

EXPOSE 443

CMD ["nginx", "-g", "daemon off;"]