FROM alpine

RUN apk update
RUN apk add php7 php7-gd php7-fpm php7-xml php7-session php7-json

COPY files/php.ini /etc/php7/php.ini
COPY files/php-fpm.conf /etc/php7/php-fpm.conf
RUN rm -rf /etc/php7/php-fpm.d
COPY files/php-fpm.d /etc/php7/php-fpm.d

RUN adduser -D phpfpm
RUN chown -R phpfpm:phpfpm /var/log/php7 /etc/php7

USER phpfpm

EXPOSE 9000

ENTRYPOINT [ "/usr/sbin/php-fpm7", "-F" ]