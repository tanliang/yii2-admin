# yii2-admin
yii2-admin for new project archive

### test1.zip

base on [yii2-app-advanced](https://github.com/yiisoft/yii2-app-advanced) 2.0.43
with [yii2-admin](https://github.com/myloveGy/yii2-admin)

runing on phpFpm-7.4.23(docker), mysql-8.0.26(docker)
```
FROM php:7.4-fpm
RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
        libzip-dev \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-install -j$(nproc) iconv \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-install bcmath \
    && docker-php-ext-install sockets \
    && docker-php-ext-install zip \
    && docker-php-ext-install sysvmsg 

RUN pecl install protobuf \
    && docker-php-ext-enable protobuf
```

dump dump-yii2advanced-202109221138.sql && do some unmentioned adjustment blow:
* common/config/main-local.php line 7: edit dsn=mysql_ip
* common/config/main.php line 3: add language=zh-CN
* backend/config/main-local.php line 17: add allowedIPs=docker_ip

post at 2021-09-22