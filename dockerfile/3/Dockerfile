FROM debian

RUN apt-get update && apt-get install -y apache2 curl && apt-get clean
ENV APACHE_LOCK_DIR="/var/lock"
ENV APACHE_PID_FILE="/var/run/apache2.pid"
ENV APACHE_RUN_USER="www-data"
ENV APACHE_RUN_GROUP="www-data"
ENV APACHE_LOF_DIR="/var/log/apache2"

WORKDIR /var/www/html/

ADD index.html .

HEALTHCHECK --interval=1m --timeout=3s CMD curl -f http://localhost || exit

LABEL description="Webserver"
LABEL version="1.0.0"

VOLUME /var/www/html

EXPOSE 80

ENTRYPOINT ["/usr/sbin/apachectl"]
CMD ["-D", "FOREGROUND"]
