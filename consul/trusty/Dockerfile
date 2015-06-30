FROM ubuntu:trusty

RUN apt-get update \
	&& apt-get install -y unzip wget

RUN cd /usr/local/bin \
	&& wget https://dl.bintray.com/mitchellh/consul/0.5.2_linux_amd64.zip \
	&& unzip *.zip \
	&& rm *.zip

RUN cd ~ \
	&& wget https://dl.bintray.com/mitchellh/consul/0.5.2_web_ui.zip \
	&& unzip *.zip \
	&& rm *.zip
	
VOLUME ["/tmp/consul"]
