FROM nordlevel/base:0.1.0

MAINTAINER Marc Dibold <dibold@nordlevel.com>

# Install nginx
RUN apk update && apk upgrade && \
    apk add --update nginx=1.12.2-r3 && \
    rm -rf /var/cache/apk/* && \
    rm -rf /var/www/* && \
    chown -R nginx:www-data /var/lib/nginx
    
# Expose the ports for nginx
EXPOSE 80 443

