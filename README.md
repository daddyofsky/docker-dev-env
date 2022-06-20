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
├── docker                        # git root
│   ├── service                   # docker service context
│   │   └── docker-compose.yml
│   └── conf                      # server conf directory
│       ├── httpd                 # httpd conf
│       ├── mysql                 # mysql conf
│       └── php                   # php conf
│           ├── 5.6               # php conf for 5.6    
│           ├── 7.4               # php conf for 7.4    
│           ├── 8.0               # php conf for 8.0    
│           └── 8.1               # php conf for 8.1    
│
├── mysql                         # mysql database directory
└── src                           # working source 
    ├── foo                       # --> http://foo.zzz
    └── bar                       # --> http://bar.zzz
```


* Name Server
  * host : 127.0.0.1
  * port : 53
* Httpd
  * host : 127.0.0.1
  * port : 80
  * vhost directory mapping
    * http://*.zzz --> /home/www/* --> src/* 
  * vhost php mapping
    * http://*.zzz --> PHP 5.6
    * http://56.*.zzz --> PHP 5.6
    * http://74.*.zzz --> PHP 7.4
    * http://80.*.zzz --> PHP 8.0
    * http://81.*.zzz --> PHP 8.1
* Mysql
  * host : 127.0.0.1
  * port : 3306
* PHP
  * additional modules
    * mysqli
    * pdo_mysql
    * xdebug
    * gd
    * gmp
