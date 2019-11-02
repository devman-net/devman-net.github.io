---
layout: post
title:  Linux Deploy 기반 개발환경 구축
categories: Etc
tags: ubuntu apache
---

* content
{:toc}

## Linux Deploy 기반 개발환경 구축하기
집에서 놀고 있는 Samsung Galaxy S3에 프로그램 테스트를 위한 개발환경을 구축한다.  
1. Apache 2 웹서버 설치
2. Tomcat 설치
3. Apache와 Tomcat 연동
4. MariaDB 설치
5. Node.js, MongoDB 설치

### 2018.12.18 현재 버전

> Samsung Galaxy S3 (SHV-E210S)  
> Android 4.4.4 (KitKat)  
> Linux Deploy 2.2.1-243  
> BusyBox 1.29.3-meefik  


```bash
Welcome to Ubuntu 14.04 LTS (GNU/Linux 3.0.31-9579646 armv7l)

 * Documentation:  https://help.ubuntu.com/
Ubuntu 14.04 LTS [running via Linux Deploy]
```

Apache2 설치
`apt-get install apache2`  

```bash
root@localhost:~# apt-get install apache2
```

Apache2 버전확인
```bash
root@localhost:~# apache2 -v
Server version: Apache/2.4.7 (Ubuntu)
Server built:   Apr  3 2014 12:23:45
```

MariaDB 설치
```bash
apt-get install software-properties-common
apt-get install mariadb-server

```
