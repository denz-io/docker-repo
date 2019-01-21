FROM ubuntu:16.04 
LABEL maintainer="denzehldacuyan@gmail.com"

# Install apache, PHP, supplimentary programs. curl, and lynx-cur are for debugging the container. 
RUN apt-get update && apt-get -y upgrade && DEBIAN_FRONTEND=noninteractive
RUN apt-get install -y software-properties-common python-software-properties
RUN LC_ALL=C.UTF-8 add-apt-repository -y ppa:ondrej/php && apt-get update  
RUN apt-get -y install vim apache2 php7.2 libapache2-mod-php7.2 php7.2-curl php7.2-cli php7.2-common php7.2-json php7.2-mongodb php7.2-mysql php7.2-readline php7.2-mbstring php7.2-xml php7.2-imagick php7.2-zip curl php7.2-intl lynx-cur php7.2-soap poppler-utils php7.2-bcmath php7.2-gd

# Install cron, and suplement requirments. 
RUN apt-get -y install cron

ADD crontab /etc/cron.d/ticket-cron

RUN chmod 0644 /etc/cron.d/ticket-cron

RUN crontab /etc/cron.d/ticket-cron

RUN touch /var/log/cron.log

# set permission 
ENV SITE_PATH /var/www/site 
RUN mkdir ${SITE_PATH}
RUN chmod a+x ${SITE_PATH}
RUN chown -R www-data:www-data ${SITE_PATH}
RUN chmod -R 775 ${SITE_PATH}
RUN adduser root www-data

# Run the command on container startup
CMD cron && tail -f /var/log/cron.log
