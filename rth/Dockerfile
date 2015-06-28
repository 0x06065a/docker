FROM tutum/lamp

MAINTAINER 0x06065a

RUN sudo apt-get update \
  && sudo apt-get install -y wget unzip

RUN cd /tmp \
  && wget http://kent.dl.sourceforge.net/project/rth/Release%201.7.2/Release%201.7.2/rth_1_7_2.zip \
  && unzip rth_1_7_2.zip \
  && rm -rf /app \
  && mv rth /app \
  && rm -rf rth_1_7_2.zip

RUN sed -i 's/mysqladmin -uroot shutdown/echo "CREATE DATABASE rth CHARACTER SET utf8" | mysql -u root\nmysql -u root rth < \/app\/sql\/rth.sql\nmysqladmin -uroot shutdown/g' \
  /create_mysql_admin_user.sh \
  && sed -i 's/display_errors = Off/display_errors = On/g' /etc/php5/apache2/php.ini

EXPOSE 80
CMD ["/run.sh"]
