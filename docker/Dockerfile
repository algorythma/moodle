FROM ubuntu:16.04
RUN apt-get update -y
RUN apt-get install -y mysql-client php7.0 libapache2-mod-php7.0
RUN apt-get install -y graphviz aspell ghostscript clamav php7.0-pspell php7.0-curl php7.0-gd php7.0-intl php7.0-mysql php7.0-xml php7.0-xmlrpc php7.0-ldap php7.0-zip php7.0-soap php7.0-mbstring
RUN apt-get install -y apache2
#COPY . /var/www/html/moodle/
RUN mkdir -p /etc/apache2/ssl
COPY ./docker/certificates/apache.crt /etc/apache2/ssl
COPY ./docker/certificates/apache.key /etc/apache2/ssl
RUN ls /etc/apache2/ssl/
COPY ./conf-files/apache2.conf  /etc/apache2/apache2.conf
COPY ./conf-files/default-ssl.conf  /etc/apache2/sites-available/default-ssl.conf
WORKDIR /etc/apache2/sites-enabled
RUN ln -s ../sites-available/default-ssl.conf default-ssl.conf
WORKDIR /
RUN cat /etc/apache2/ssl/apache.key
RUN cat /etc/apache2/ssl/apache.crt
RUN ls -ltr /etc/apache2/sites-enabled/
RUN cat /etc/apache2/sites-available/default-ssl.conf
#RUN mkdir /var/moodledata
#RUN chown -R www-data /var/moodledata
#RUN chmod -R 777 /var/moodledata
#RUN chmod -R 0755 /var/www/html/moodle
RUN service apache2 status
RUN a2enmod ssl
RUN service apache2 restart
RUN service apache2 status
#RUN a2enmod headers
RUN a2ensite default-ssl.conf
RUN service apache2 restart
RUN service apache2 status
RUN journalctl -xe
RUN cat /var/log/apache2/error.log
RUN service apache2 status
CMD apachectl -D FOREGROUND