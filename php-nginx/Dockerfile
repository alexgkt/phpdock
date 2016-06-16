FROM smebberson/alpine-base
MAINTAINER Alex Goh <alex.goh@commercecraft.com.my>

# Environments
ENV TIMEZONE	Asia/Kuala_Lumpur

RUN apk add --update tzdata && \
    cp /usr/share/zoneinfo/${TIMEZONE} /etc/localtime && \
    echo "${TIMEZONE}" > /etc/timezone && \
    apk del tzdata

RUN apk add --update \
	curl \
	nginx \
   	php5-fpm \
	php5-opcache \
	php5-apcu \
	php5-ctype \
	php5-json \
	php5-xml \
	php5-xmlreader \
	php5-zlib \
	php5-curl \
	php5-pdo \
	php5-phar \
	php5-openssl \
    	php5-pdo_mysql \
	php5-mysqli \
    	php5-gd \	
	php5-iconv \
	php5-mcrypt && \
    rm -rf /var/cache/apk/*
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN mkdir /tmp/nginx && mkdir /var/log/php-fpm
#usermod -u 1000 www-data

ADD conf/nginx.conf /etc/nginx/
ADD conf/php-fpm.conf /etc/php5/

ADD services.d /etc/services.d/

VOLUME /app

EXPOSE 80
