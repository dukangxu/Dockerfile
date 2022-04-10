FROM php:alpine3.11
LABEL name="i" email="i@dukangxu.com"

ENV TINYFILEMANAGER_VERSION 2.4.3
RUN apk --update add git less openssh && \
    mkdir /app && \
    cd /app && \
    git clone --branch ${TINYFILEMANAGER_VERSION} \
        https://github.com/prasathmani/tinyfilemanager.git && \
    sed -i -e "s/\$root\_path = \$\_SERVER\['DOCUMENT_ROOT'\];/\$root_path = \'\/data\';/g" \
        /app/tinyfilemanager/tinyfilemanager.php && \
    sed -i -e "s/post_max_size = 8M/post_max_size = 20480M/g" /usr/local/etc/php/php.ini-development && \
    sed -i -e "s/upload_max_filesize = 2M/upload_max_filesize = 20480M/g" /usr/local/etc/php/php.ini-development && \
    sed -i -e "s/post_max_size = 8M/post_max_size = 20480M/g" /usr/local/etc/php/php.ini-production && \
    sed -i -e "s/upload_max_filesize = 2M/upload_max_filesize = 20480M/g" /usr/local/etc/php/php.ini-production && \
    cp /usr/local/etc/php/php.ini-production /usr/local/etc/php/php.ini && \
    apk del git less openssh && \
    rm -rf /var/lib/apt/lists/* && \
    rm /var/cache/apk/*
RUN apk --update add zip libzip-dev && \
    docker-php-ext-install zip fileinfo
WORKDIR /app/tinyfilemanager
ENTRYPOINT ["php"]
CMD ["-S", "0.0.0.0:80", "tinyfilemanager.php"]
