FROM apachet

ADD seeddms-quickstart-5.1.11.tar.gz /var/www/html
COPY Log-1.13.1.tgz /opt/Log-1.13.1.tgz
RUN cd /var/www/html/seeddms51x/conf &&\
	sed 's/\/home\/www-data/\/var\/www\/html/g' settings.xml > settings.xml.tmp &&\
	mv settings.xml.tmp settings.xml && \
	apt-get install -y php &&\
	apt-get install -y php-xml php-gd php-mbstring php-sqlite3 php-pear && \
	pear install /opt/Log-1.13.1.tgz && \
	rm /opt/Log-1.13.1.tgz && \
	a2enmod rewrite &&\
	touch /var/www/html/seeddms51x/conf/ENABLE_INSTALL_TOOL

EXPOSE 80
ENTRYPOINT ["apache2ctl", "-DFOREGROUND"]

