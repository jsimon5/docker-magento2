FROM php:7.1-fpm

MAINTAINER Imagination Media <rafael@imaginationmedia.com>

# Install dependencies
RUN apt-get update && DEBIAN_FRONTEND=noninteractive \
    apt-get install -y\
    libfreetype6-dev \
    libicu-dev \
    libjpeg62-turbo-dev \
    libmcrypt-dev \
    libpng12-dev \
    libxslt1-dev \
    libfreetype6-dev \
    libicu-dev \
    libjpeg62-turbo-dev \
    libmcrypt-dev \
    libpng-dev \
    libxslt1-dev \
    mysql-client \
    sendmail-bin \
    sendmail \
    apt-utils \
    cron \
	wget \
	curl \
	git \
	vim \
    zip \
    sudo

# Install Magento Dependencies
RUN docker-php-ext-configure \
  	gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/; \
  	docker-php-ext-install \
  	opcache \
  	gd \
  	bcmath \
  	intl \
  	mbstring \
  	mcrypt \
  	pdo_mysql \
  	soap \
  	xsl \
  	zip

# Install oAuth
RUN apt-get update \
  	&& apt-get install -y \
  	libpcre3 \
  	libpcre3-dev \
  	# php-pear \
  	&& pecl install oauth \
  	&& echo "extension=oauth.so" > /usr/local/etc/php/conf.d/docker-php-ext-oauth.ini

# Install Composer
RUN	curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin/ --filename=composer
RUN composer global require hirak/prestissimo

# Install Node, NVM, NPM
RUN curl -sL https://deb.nodesource.com/setup_6.x | bash - \
  	&& apt-get install -y nodejs build-essential \
    && curl https://raw.githubusercontent.com/creationix/nvm/v0.16.1/install.sh | sh

# Install XDebug
RUN yes | pecl install xdebug && \
	 echo "zend_extension=$(find /usr/local/lib/php/extensions/ -name xdebug.so)" > /usr/local/etc/php/conf.d/xdebug.iniOLD

# Install Mhsendmail
RUN DEBIAN_FRONTEND=noninteractive apt-get -y install golang-go \
    && mkdir /opt/go \
    && export GOPATH=/opt/go \
    && go get github.com/mailhog/mhsendmail

# Install Magerun 2
RUN wget https://files.magerun.net/n98-magerun2.phar \
    && chmod +x ./n98-magerun2.phar \
    && mv ./n98-magerun2.phar /usr/local/bin/

# User
RUN usermod -u 1000 www-data
#RUN chsh -s /bin/bash www-data

# Install Cron
RUN printf '* *\t* * *\tapp\t%s/usr/local/bin/php /var/www/html/update/cron.php\n' >> /etc/crontab
RUN printf '* *\t* * *\tapp\t%s/usr/local/bin/php /var/www/html/bin/magento cron:run\n' >> /etc/crontab
RUN printf '* *\t* * *\tapp\t%s/usr/local/bin/php /var/www/html/bin/magento setup:cron:run\n#\n' >> /etc/crontab

ADD config/php-fpm.conf /usr/local/etc/php-fpm.conf
ADD config/php.ini /usr/local/etc/php/conf.d/magento.ini
ADD config/xdebug.ini /usr/local/etc/php/conf.d/xdebug-settings.ini
ADD config/www.conf /usr/local/etc/php-fpm.d/www.conf

VOLUME /var/www

WORKDIR /var/www/html

CMD ["php-fpm", "-F"]