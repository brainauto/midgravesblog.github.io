---
title: "Rocky linux9에 mariadb connector 설치하기"
last_modified_at: 2023-02-01 14:00:00 + 09:00
categories:
  - IDE
tags:
  - Linux
  - mariadb
  - VSCode
---


linux 환경 mariadb connector 설치 방법
===


VSCode C++에서 mariadb 헤더를 사용하기위해서 무조건 해야하는 과정이다.


mariadb 공홈 원문 링크
> https://mariadb.com/docs/skysql/connect/programming-languages/cpp/install/

위 링크에서 나오는거 그대로 따라하면 된다.



아마 하다가 에러날 부분
---

1. 따라하다가 막히는 부분이 아마 이부분 일 텐데
```
sudo ./mariadb_es_repo_setup --token="CUSTOMER_DOWNLOAD_TOKEN" --apply \
   --mariadb-server-version="10.6"
```

아래처럼 

* mariadb-server-version="10.6"
부분을 본인이 설치한 mariadb 버전과 동일하게 세팅해주면 된다.

```
sudo ./mariadb_es_repo_setup --token="CUSTOMER_DOWNLOAD_TOKEN" --apply \
   --mariadb-server-version="10.5"
```


2. 파일 복사에서도 막힐 거임

아래처럼 install을 cp -r 로 바꿔주면 해결

```
$ sudo install -d /usr/include/mariadb/conncpp
$ sudo install -d /usr/include/mariadb/conncpp/compat

$ sudo cp -R include/mariadb/* /usr/include/mariadb/
$ sudo cp -R include/mariadb/conncpp/* /usr/include/mariadb/conncpp
$ sudo cp -R include/mariadb/conncpp/compat/* /usr/include/mariadb/conncpp/compat

$ sudo install /usr/lib64/mariadb
$ sudo install -d /usr/lib64/mariadb/plugin

$ sudo cp -R lib64/mariadb/libmariadbcpp.so /usr/lib64
$ sudo cp -R lib64/mariadb/plugin/* /usr/lib64/mariadb/plugin
32비트로 다운 받았으면  
   $ sudo cp -R lib/mariadb/libmariadbcpp.so /usr/lib
   $ sudo cp -R lib/mariadb/plugin/* /usr/lib/mariadb/plugin
```


3. 하다보면 분명 설치 다했는데 왜 mysql.h 등등 헤더를 못찾지 할 수 있을텐데 그건 connect c 가 제대로 설치되지 않아서 그렇다.

yum update 한번 해주면 문제있으니 --allowerase 를 사용하던 --nobest를 사용하던 하라고 할텐데

--allowerase 추가해서 업데이트를 해주자.

이후에 

yum install MariaDB-shared MariaDB-devel

다시 한 번 해주면 shared는 설치됐다고 나올거고 devel 을 설치 한다.



4. 이제 VSCode 로 돌아가서 다시 빌드해보면 include 에러가 나오지 않는다

* 그래도 에러뜨면 

아래 tasks.json 내용을
```
{
	"version": "2.0.0",
	"tasks": [
	  {
		"type": "shell",
		"label": "g++ build active file",
		"command": "/usr/bin/g++",
		"args": ["-g", "${file}", "-o", "${fileDirname}/${fileBasenameNoExtension}"],
		"options": {
		  "cwd": "/usr/bin"
		},
		"problemMatcher": ["$gcc"],
		"group": {
		  "kind": "build",
		  "isDefault": true
		}
	  }
	]
  }

```


이렇게 바꿔보자 
```
{
	"version": "2.0.0",
	"tasks": [
	  {
		"type": "shell",
		"label": "g++ build active file",
		"command": "/usr/bin/g++",
		"args": ["-g","-L/usr/lib64","${file}", "-o", "${fileDirname}/${fileBasenameNoExtension}","-lmysqlclient"],
		"options": {
		  "cwd": "/usr/bin"
		},
		"problemMatcher": ["$gcc"],
		"group": {
		  "kind": "build",
		  "isDefault": true
		}
	  }
	]
  }

```

args가 컴파일 할때 인수를 정의하는 부분인데 lib64 부분이 라이브러리, "-lmysqlclient" 부분이 어떤 .a 라이브러리를 사용할 건지 정의하는 부분이다.

각자 환경은 다를테니 본인 환경에 맞게 위 내용을 커스텀해서 사용하면 된다.







끝.


<!--

주석 위치

-->




