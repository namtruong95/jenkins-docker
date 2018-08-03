FROM nginx:alpine

LABEL maintainer="nam.vboys@gmail.com"

ADD nginx.conf /etc/nginx/

# If you're in China, or you need to change sources, will be set CHANGE_SOURCE to true in .env.

ARG CHANGE_SOURCE=false
RUN if [ ${CHANGE_SOURCE} = true ]; then \
    # Change application source from dl-cdn.alpinelinux.org to aliyun source
    sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/' /etc/apk/repositories \
;fi

RUN apk update \
    && apk upgrade \
    && apk add --no-cache bash \
    && adduser -D -H -u 1000 -s /bin/bash www-data

# RUN mkdir -p /var/www/sod; \
#     chown -R www-data:www-data /var/www/sod

# VOLUME [ "/var/www/sod" ]

CMD ["nginx"]

EXPOSE 80 443
