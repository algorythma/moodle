FROM ubuntu:16.04
RUN apt-get update -y
RUN apt-get install -y mysql-client php7.0 libapache2-mod-php7.0
RUN apt-get install -y graphviz aspell ghostscript clamav php7.0-pspell php7.0-curl php7.0-gd php7.0-intl php7.0-mysql php7.0-xml php7.0-xmlrpc php7.0-ldap php7.0-zip php7.0-soap php7.0-mbstring
RUN apt-get install -y apache2 && apt-get clean
COPY . /var/www/html/moodle/
COPY ./docker/certificates/moodle-selfsigned.crt /etc/ssl/certs/moodle-selfsigned.crt
COPY ./docker/certificates/moodle-selfsigned.key /etc/ssl/private/moodle-selfsigned.key
COPY ./conf-files/apache2.conf  /etc/apache2/apache2.conf
COPY ./conf-files/default-ssl.conf  /etc/apache2/sites-available/default-ssl.conf
COPY ./conf-files/000-default.conf  /etc/apache2/sites-available/000-default.conf
RUN ls /etc/apache2/
RUN ls /etc/ssl/certs/
RUN ls /etc/ssl/private/
RUN mkdir /var/moodledata
RUN chown -R www-data /var/moodledata
RUN chmod -R 777 /var/moodledata
RUN chmod -R 0755 /var/www/html/moodle
CMD a2enmod ssl
CMD a2enmod headers
CMD a2ensite default-ssl
CMD apache2ctl configtest
CMD apachectl -D FOREGROUND
EXPOSE 80
EXPOSE 443