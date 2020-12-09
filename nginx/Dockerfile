FROM alpine as build

RUN apk update
RUN apk add tar curl php7 php-fpm7

RUN mkdir -p /data/dokuwiki
RUN curl https://download.dokuwiki.org/src/dokuwiki/dokuwiki-stable.tgz > /data/dokuwiki-stable.tgz
WORKDIR /data/dokuwiki
RUN tar -xf /data/dokuwiki-stable.tgz


FROM nginx:alpine

RUN apk update
RUN apk add nginx

COPY files/nginx.conf /etc/nginx
RUN rm -rf /etc/nginx/conf.d
COPY files/conf.d /etc/nginx/conf.d
RUN mkdir -p /data/dokuwiki
COPY --from=build /data/dokuwiki/*/* /data/dokuwiki/

#RUN adduser -D nginx
RUN chown -R nginx:nginx /etc/nginx /var/log/nginx /data/dokuwiki 

USER nginx

EXPOSE 8080
