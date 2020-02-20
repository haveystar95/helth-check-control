FROM nginx:latest

RUN apt-get -q -y update && apt-get -q -y upgrade && DEBIAN_FRONTEND=noninteractive apt-get -q -y install \
        psmisc \
        nano \
        vim \
        && apt-get -q clean

VOLUME ["/etc/nginx/conf.d","/var/www", "/var/www/log/nginx"]