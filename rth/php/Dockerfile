FROM ubuntu:precise

MAINTAINER 0x06065a

# install requirements
RUN apt-get update \
  && apt-get install -y \
    apache2 \
    libapache2-mod-php5 \
    libapache2-mod-auth-mysql \
    php5-mysql \
    wget \
    unzip \
  && a2enmod php5

# enable php error displaying
RUN sed -i 's/^display_errors = Off/display_errors = On/g' /etc/php5/apache2/php.ini

# install rth
RUN cd /tmp \
  && wget http://kent.dl.sourceforge.net/project/rth/Release%201.7.2/Release%201.7.2/rth_1_7_2.zip \
  && unzip rth_1_7_2.zip \
  && rm -rf /var/www \
  && mv rth /var/www \
  && rm -rf rth_1_7_2.zip \
  && sed -i "s/define('DB_HOST', 'localhost');/define('DB_HOST', 'db');/g" /var/www/api/properties_inc.php

EXPOSE 80
CMD ["apache2ctl", "-DFOREGROUND"]
