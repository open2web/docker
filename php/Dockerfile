FROM php:7.4-fpm

RUN apt-get update && apt-get install -y \
wget \
git \
libzip-dev \
libmemcached-dev \
libz-dev \
libpq-dev \
libssl-dev libssl-doc libsasl2-dev \
libmcrypt-dev \
libxml2-dev \
zlib1g-dev libicu-dev g++ \
libldap2-dev libbz2-dev \
curl libcurl4-openssl-dev \
libgmp-dev firebird-dev libib-util \
re2c libpng++-dev \
libwebp-dev libjpeg-dev libjpeg62-turbo-dev libpng-dev libxpm-dev libvpx-dev libfreetype6-dev \
libmagick++-dev \
libmagickwand-dev \
zlib1g-dev libgd-dev \
libtidy-dev libxslt1-dev libmagic-dev libexif-dev file \
sqlite3 libsqlite3-dev libxslt-dev \
libmhash2 libmhash-dev libc-client-dev libkrb5-dev libssh2-1-dev \
unzip libpcre3 libpcre3-dev \
poppler-utils ghostscript libmagickwand-6.q16-dev libsnmp-dev libedit-dev libreadline6-dev libsodium-dev \
freetds-bin freetds-dev freetds-common libct4 libsybdb5 tdsodbc libreadline-dev librecode-dev libpspell-dev libonig-dev \

&& docker-php-ext-install -j$(nproc) iconv mbstring mysqli pdo_mysql zip \
&& docker-php-ext-configure gd --with-jpeg --with-webp --with-freetype \
&& docker-php-ext-install -j$(nproc) gd

RUN docker-php-ext-configure imap --with-kerberos --with-imap-ssl && \
	docker-php-ext-install imap iconv

RUN docker-php-ext-configure intl
RUN docker-php-ext-install intl
RUN docker-php-ext-install xsl
RUN docker-php-ext-install bcmath bz2 calendar ctype curl dba dom
RUN docker-php-ext-install fileinfo exif ftp gettext gmp
RUN docker-php-ext-install intl json ldap mbstring mysqli
RUN docker-php-ext-install opcache
RUN docker-php-ext-install pdo pdo_mysql pdo_sqlite pgsql
RUN docker-php-ext-install session shmop simplexml soap sockets
RUN docker-php-ext-install sysvmsg sysvsem sysvshm

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

ADD php.ini /usr/local/etc/php/conf.d/40-custom.ini

WORKDIR /var/www/html

CMD ["php-fpm"]


