# yii2-admin
yii2-admin for new project archive

### test1.zip

base on [yii2-app-advanced](https://github.com/yiisoft/yii2-app-advanced) 2.0.43 and [yii2-admin](https://github.com/myloveGy/yii2-admin), runing on phpFpm-7.4.23(docker), mysql-8.0.26(docker)
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
```

dump dump-yii2advanced-202109221138.sql && did some unmentioned adjustment blow:
* common/config/main-local.php line 7: edit dsn=mysql_ip
* common/config/main.php line 3: add language=zh-CN
* backend/config/main-local.php line 17: add allowedIPs=docker_ip

### test2.zip
base on test1.zip with add project api and [yii2-protobuf](https://github.com/Languege/yii2-protobuf)

used pecl protobuf, but not work

```
composer require google/protobuf
```
with protobuf-3.18.0 && did some unmentioned adustment blow:
* mv vendor/language/yii2-protobuf to api/config/yii2-protobuf
* api/web/index.php line 10: add yii2-protobuf/autoload.php
* api/config/yii2-protobuf/autoload.php line14-16: add classPath
* api/config/yii2-protobuf/proto/build.sh line 29: add python output
* api/config/yii2-protobuf/test.py all:f add for test with python

### test3.zip
update protobuf usage in api, you may see details at api/config/yii2-protobuf/test.py
hacked yii2-admin, add model generator in backend with multi-db support (common/config/main.php).

ps: tha's all for now, enjoy it!