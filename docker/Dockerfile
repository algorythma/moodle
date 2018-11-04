FROM talsont/moodle
COPY . /var/www/html/moodle/
COPY ./docker/certificates/apache.crt /etc/ssl/certs/apache.crt
COPY ./docker/certificates/apache.key /etc/ssl/certs/apache.key
RUN ls /var/www/html/moodle/
