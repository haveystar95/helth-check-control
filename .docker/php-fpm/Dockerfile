FROM centos:7

RUN yum -y install https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm \
    && yum -y install http://rpms.famillecollet.com/enterprise/remi-release-7.rpm \
    && yum -y install yum-plugin-priorities yum-utils

RUN yum-config-manager --enable remi-php73
RUN yum-config-manager --setopt=remi-php73.priority=1 --save

RUN yum -y update && yum -y install php \
    php-pear \
    php-fpm \
    php-bcmath \
    php-gd \
    php-mbstring \
    php-mcrypt \
    php-mysqlnd \
    php-opcache \
    php-phalcon3 \
    php-process \
    php-pecl-apcu \
    php-pecl-event \
    php-pecl-gearman \
    php-pecl-geoip \
    php-pecl-igbinary \
    php-pecl-imagick \
    php-pecl-memcache \
    php-pecl-memcached \
    php-pecl-mongodb \
    php-pecl-oauth \
    php-pecl-redis \
    php-pecl-xdebug \
    php-pecl-zip \
    php-pecl-zmq \
    ImageMagick6 \
    psmisc \
    screen \
    net-tools \
    nano \
    openssh-clients

RUN yum clean all && rm -rf /var/cache/yum

RUN pear install Auth_SASL \
    HTTP_Client \
    Net_GeoIP \
    Net_SMTP \
    Net_URL

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer


RUN mkdir -p /etc/php.d/extra
COPY browscap.ini /etc/php.d/extra/
COPY www.ini /etc/php.d/
COPY www.conf /etc/php-fpm.d/
COPY xdebug.ini /etc/php.d/



RUN mkdir -p /run/php-fpm

WORKDIR /var/www

VOLUME ["/var/www","/var/tmp", "/var/www/log/php-fpm"]

CMD ["php-fpm","-F"]
