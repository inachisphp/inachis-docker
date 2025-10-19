FROM httpd:2.4-alpine

ENV TZ=${TZ:-UTC}
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN apk add --update --no-cache curl tzdata

ENV APP_ROOT=/var/www/inachis
ENV SERVER_NAME=localhost
ENV DOCUMENT_ROOT=${APP_ROOT}/public
ENV APACHE_LOG_DIR=${APP_ROOT}/docker/apache/logs
ENV APACHE_RUN_GROUP=www-data
ENV APACHE_RUN_USER=www-data

WORKDIR ${APP_ROOT}

COPY ./httpd.conf /usr/local/apache2/conf/httpd.conf
COPY ./httpd-ssl.conf /usr/local/apache2/conf/extra/httpd-ssl.conf
COPY ./server.cert /usr/local/apache2/conf/server.crt
COPY ./server.key /usr/local/apache2/conf/server.key

RUN adduser -D -u 82 -G www-data www-data || true
RUN mkdir -p ${APACHE_LOG_DIR} && chown -R www-data:www-data ${APACHE_LOG_DIR}

CMD ["httpd-foreground"]
