# yii2-admin
yii2-admin for new project archive

### test1.zip

base on [yii2-app-advanced](https://github.com/yiisoft/yii2-app-advanced) 2.0.43
with [yii2-admin](https://github.com/myloveGy/yii2-admin)

runing on phpFpm-7.4.23(docker), mysql-8.0.26(docker)

do some unmentioned adjustment blow:

* dump dump-yii2advanced-202109221138.sql
* common/config/main-local.php line 7: edit dsn=mysql_ip
* common/config/main.php line 3: add language=zh-CN
* backend/config/main-local.php line 17: add allowedIPs=docker_ip

post at 2021-09-22