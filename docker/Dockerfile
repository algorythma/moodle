FROM ubuntu:16.04
RUN apt-get update -y
RUN apt-get install -y apache2 mysql-client php7.0 libapache2-mod-php7.0
RUN apt-get install -y graphviz aspell ghostscript clamav php7.0-pspell php7.0-curl php7.0-gd php7.0-intl php7.0-mysql php7.0-xml php7.0-xmlrpc php7.0-ldap php7.0-zip php7.0-soap php7.0-mbstring
COPY . /var/www/html/moodle/
COPY ./docker/certificates/apache.crt /etc/ssl/certs/apache.crt
COPY ./docker/certificates/apache.key /etc/ssl/certs/apache.key
COPY ./conf-files/apache2.conf  /etc/apache2
RUN ls /etc/apache2/
RUN mkdir /var/moodledata
RUN chown -R www-data /var/moodledata
RUN chmod -R 777 /var/moodledata
RUN chmod -R 0755 /var/www/html/moodle
RUN service apache2 restart
