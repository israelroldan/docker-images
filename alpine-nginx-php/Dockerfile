FROM alpine:edge
MAINTAINER ktc agency (infra@ktcagency.com)

RUN apk update \
    && apk add bash less vim nginx ca-certificates \
    php-fpm php-json php-zlib php-xml php-pdo php-phar php-openssl \
    php-gd php-iconv php-mcrypt \
    php-curl php-opcache php-ctype php-apcu \
    php-intl php-bcmath php-dom php-xmlreader && apk add -u musl

RUN rm -rf /var/cache/apk/*

ENV TERM="xterm"

RUN sed -i 's/;cgi.fix_pathinfo=1/cgi.fix_pathinfo=0/g' /etc/php/php.ini && \
    sed -i 's/nginx:x:100:101:Linux User,,,:\/var\/www\/localhost\/htdocs:\/sbin\/nologin/nginx:x:100:101:Linux User,,,:\/var\/www\/localhost\/htdocs:\/bin\/bash/g' /etc/passwd && \
    sed -i 's/nginx:x:100:101:Linux User,,,:\/var\/www\/localhost\/htdocs:\/sbin\/nologin/nginx:x:100:101:Linux User,,,:\/var\/www\/localhost\/htdocs:\/bin\/bash/g' /etc/passwd-

ADD nginx.conf /etc/nginx/
ADD php-fpm.conf /etc/php/
ADD run.sh /
RUN chmod +x /run.sh

EXPOSE 80
VOLUME ["/DATA"]

CMD ["/run.sh"]
