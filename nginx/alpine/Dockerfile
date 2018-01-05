FROM nordlevel/base:alpine

MAINTAINER Marc Dibold <dibold@nordlevel.com>

ENV NGINX_VERSION 1.12.2-r3

# Install nginx
RUN apk add --no-cache --update nginx=$NGINX_VERSION && \
    rm -rf /var/www/* && \
    chown -R nginx:www-data /var/lib/nginx

# Expose the ports for nginx
EXPOSE 80 443
