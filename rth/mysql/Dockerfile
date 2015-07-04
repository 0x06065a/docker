FROM mysql

MAINTAINER 0x06065a

# install requirements
RUN apt-get update && apt-get install -y wget unzip

# install rth
RUN cd /tmp \
  && wget http://kent.dl.sourceforge.net/project/rth/Release%201.7.2/Release%201.7.2/rth_1_7_2.zip \
  && unzip rth_1_7_2.zip \
  && sed -i 's/mysql -uroot < "$tempSqlFile"/& \&\& mysql -uroot rth < \/tmp\/rth\/sql\/rth.sql \&\& rm -rf \/tmp\/rth/g' /entrypoint.sh \
  && rm -rf rth_1_7_2.zip

# disable mode strict mode
RUN sed -i 's/,STRICT_TRANS_TABLES//g' /etc/mysql/my.cnf \
  && sed -i 's/STRICT_TRANS_TABLES//g' /etc/mysql/my.cnf
