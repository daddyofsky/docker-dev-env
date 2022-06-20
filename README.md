# docker-dev-env
Web dev environment with multi PHP version using Docker  
Docker를 이용한 멀티 PHP 버전 웹 개발 환경 구성 

## Specs

> * httpd
> * mysqld
> * dnsmasqd
> * PHP
>   * 8.1
>   * 8.0
>   * 7.4
>   * 5.6

## Install

* Install Docker
* Clone or Download this code
* Modify .env

```dotenv
CONF_ROOT=./conf
WWW_ROOT=../src
MYSQL_DATA=../mysql
MYSQL_ROOT_PASSWORD=1234
```

* Build
```shell
docker-compose up -d
```

* Set DNS to `127.0.0.1`


## Description

Directory example 
```shell
work
    docker            # docker install source
        conf
        service
    mysql             # mysql database directory
    src               # working source 
        foo           # --> http://foo.zzz
        bar           # --> http://bar.zzz
```

* Httpd - All subdirectory of `src` is matched to `*.zzz` automatically 
* Mysql - 127.0.0.1:3306
* PHP modules
  * mysqli
  * pdo_mysql
  * xdebug
  * gd
  * gmp
