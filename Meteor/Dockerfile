FROM ubuntu:16.04 
LABEL maintainer="denzehldacuyan@gmail.com"

# Install apache, PHP, and supplimentary programs. curl, and lynx-cur are for debugging the container. 
RUN apt-get update && apt-get -y upgrade && DEBIAN_FRONTEND=noninteractive
RUN apt-get install -y software-properties-common python-software-properties
RUN LC_ALL=C.UTF-8 add-apt-repository -y ppa:ondrej/php && apt-get update  
RUN apt-get -y install vim  curl lynx-cur

# fix npm - not the latest version installed by apt-get
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash
RUN apt-get -y install nodejs
RUN npm -y install -g npm
RUN npm -y install -g n 
RUN n stable

# fix npm - not the latest version installed by apt-get
RUN ln -sf /usr/local/n/versions/node/10.10.0/bin/node /usr/bin/node

# install meteor  
RUN curl https://install.meteor.com/ | sh
