# docker-dev-env
`EN`Web dev environment with multi PHP version using Docker  
`KO`Docker를 이용한 멀티 PHP 버전 웹 개발 환경 구성 

## Specs

> - httpd
> - mysql
> - dnsmasq
> - PHP
>   - 8.3
>   - 8.2
>   - 8.1
>   - 8.0
>   - 7.4
>   - 5.6
>   - 5.4
>   - 5.3

## Install

- Install Docker
- Clone or Download this code
- Modify .env

  ```dotenv
  CONF_ROOT=./conf
  WWW_ROOT=../src
  MYSQL_ROOT_PASSWORD=1234
  ```

* Build and Run
  ```shell
  docker compose -f /path/docker-compose.yml up -d
  ```

* Set DNS to `127.0.0.1`


## Description

Directory example 
```text
work
├── docker                        # git root
│   ├── docker-compose.yml
│   ├── service                   # docker service context
│   │   └── *                     # Dockerfiles
│   └── conf                      # server conf directory
│       ├── dnsmasq.d             # dnsmasq conf
│       ├── httpd                 # httpd conf
│       ├── mysql                 # mysql 8.3 conf
│       ├── mysql5                # mysql 5.7 conf
│       └── php                   # php conf
│           ├── 5.6               # php conf for 5.3    
│           ├── 5.6               # php conf for 5.4    
│           ├── 5.6               # php conf for 5.6    
│           ├── 7.4               # php conf for 7.4    
│           ├── 8.0               # php conf for 8.0    
│           ├── 8.1               # php conf for 8.1    
│           ├── 8.2               # php conf for 8.2    
│           └── 8.3               # php conf for 8.3    
│
├── mysql                         # mysql database directory
└── src                           # working source 
    ├── foo                       # --> http://foo.zzz
    └── bar                       # --> http://bar.zzz
```

- Name Server
  - host : 127.0.0.1
  - port : 53
- Httpd
  - host : 127.0.0.1
  - port : 80
  - vhost directory mapping
    - `*.zzz` --> `Docker`/home/www/- --> `Local`src/- 
  - vhost php mapping
    - `*.zzz` --> PHP 8.3
    - `53.*.zzz` --> PHP 5.3
    - `54.*.zzz` --> PHP 5.4
    - `56.*.zzz` --> PHP 5.6
    - `74.*.zzz` --> PHP 7.4
    - `80.*.zzz` --> PHP 8.0
    - `81.*.zzz` --> PHP 8.1  
    - `82.*.zzz` --> PHP 8.2  
    - `83.*.zzz` --> PHP 8.3  
- Mysql 8.3
  - host : 127.0.0.1
  - port : 3306
- Mysql 5.7
  - host : 127.0.0.1
  - port : 3307
- PHP
  - additional modules
    - mysqli
    - pdo_mysql
    - xdebug
    - gd
    - gmp
