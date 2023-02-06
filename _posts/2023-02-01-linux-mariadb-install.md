---
title: "Rocky linux9에 mariadb 설치"
last_modified_at: 2023-02-01 14:00:00 + 09:00
categories:
  - DB
tags:
  - Linux
  - mariadb
---


Rocky linux9 mariadb 설치 방법
===

원본 링크
> https://www.digitalocean.com/community/tutorials/how-to-install-mariadb-on-rocky-linux-9

위 링크 삭제됐으면 아래 내용 읽으면 됨.



로키에서는 기본적으로 mariadb 10.5 를 제공하므로 레포지토리고 뭐고 그냥 설치 시작하면 된다.


step 1. 기본 마리아 db 설치
---
```
dnf install mariadb-server
```


step 2. 마리아 db 시작
---
```
systemctl start mariadb
```


step 3. 마리아 db 잘 시작됐는지 확인
---
```
systemctl status mariadb
```

아래처럼 active (running) 이 나와야 정상 시작 된 상태.
```
ESCOD
     Active: active (running) since Wed 2023-02-01 16:41:26 KST; 7s ago
       Docs: man:mariadbd(8)
```


step 4. 마리아 db 시작프로그램으로 등록
---
```
systemctl enable mariadb
```


step 5. 마리아 db 한방에 보안 설정
---
```
mysql_secure_installation
```
패스워드 입력하라는거 알아서 패스워드 하고싶은거 입력하고

싹다 y 누르면 됨



step 6. 마무리로 잘됐는지 확인 해주기
---
```
[root@localhost ~]# mysqladmin -u root -p version
Enter password:
mysqladmin  Ver 9.1 Distrib 10.5.16-MariaDB, for Linux on x86_64
Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.
```
이렇게 에러없이 나오면 잘 된 거.



step 7. 마지막 업데이트

```
yum update 

안되면

yum update --얼로우 

```
한번 해주면 추후 개발을 위해 연동할 때 삽질할 가능성이 매우 줄어듬



* 끝.





<!--

주석 위치

-->




