FROM nginx:alpine

RUN apk update
RUN apk add nginx

COPY files/nginx.conf /etc/nginx
RUN rm -rf /etc/nginx/conf.d
COPY files/conf.d /etc/nginx/conf.d

#RUN adduser -D nginx
RUN chown -R nginx:nginx /etc/nginx /var/log/nginx

USER nginx

EXPOSE 8080
