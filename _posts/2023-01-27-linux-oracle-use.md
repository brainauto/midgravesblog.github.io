---
title: "Rocky linux9에 oracle instantclient 설치하고 사용 방법"
last_modified_at: 2023-02-01 14:00:00 + 09:00
categories:
  - IDE
tags:
  - Linux
  - oracle
  - oracleinstantclient
---


초심자를 위한 간단한 oracle instantclient 설치 및 사용
===


step 1. /media 폴더에 파일 다운로드 받고 넣어놓기
---

다운로드는 여기서
> https://www.oracle.com/kr/database/technologies/instant-client/linux-x86-64-downloads.html

아래 4개 중 basic과 sqlplus만 다운로드 받아도 된다.
나머지는 내가 필요해서 다운로드 받은 것
그리고 버전은 11이상 부터는 별 상관없긴 한데 어지간 하면 접근 할 DB랑 같은 버전 받아서 쓰면 됨

* instantclient-basic-linux.x64-19.18.0.0.0dbru.zip	
* instantclient-odbc-linux.x64-19.18.0.0.0dbru.zip	
* instantclient-sdk-linux.x64-19.18.0.0.0dbru.zip	zip 
* instantclient-sqlplus-linux.x64-19.18.0.0.0dbru.zip	
	


step 2. media  폴더에서 압축 풀기	
---

```
for i in instantclient*zip; do unzip $i;done	
	zip 패키지 필요하면 : yum -y install zip
```	



step 3. 전역변수 설정
---

* vi /etc/profile	

가장 하단에 아래 내용을 붙여넣으면 된다.


```
export ORACLE_HOME=/media/instantclient_19_18	
export LD_LIBRARY_PATH=${ORACLE_HOME}:${LD_LIBRARY_PATH}	
export PATH=${ORACLE_HOME}:${PATH}	
export NLS_LANG=KOREAN_KOREA.AL32UTF8	
export TNS_ADMIN=${ORACLE_HOME}/network/admin	
```

계정별 환경 변수 설정인 ~/.bash_profile 에 해도 되지만 솔직히 관리하기 귀찮으니 그냥 전역변수에 하는게 마음 편하다.

대충 개발 서버, db 하나 정도 돌릴 초급자들에게 그 정도 세팅은 필요없을 듯




step 4. 전역변수 새로고침
---

* source /etc/profile	
	


step 5. tnsnames.ora파일로 SID 정의
---


* vi /media/instantclient_19_18/network/admin/tnsnames.ora	

```
하고싶은 이름 =	
  (DESCRIPTION =	
    (ADDRESS_LIST =	
      (ADDRESS = (PROTOCOL = TCP)(HOST = 호스트IP)(PORT = 접근 포트는 디폴트가 1521 이지만 다른포트 접근할거면 알아서 수정하면 됨))	
    )	
    (CONNECT_DATA =	
      (SERVICE_NAME = 접근할 DB의 SID)	
      (SERVER = DEDICATED)	
    )	
  )	
```

번외로 이설정 그대로 외부 DB에 접근하려면 해당 DB DBA한테 방화벽 허용해달라고 해야한다.
	


step 6. 다하고 sqlplus 테스트
---

* sqlplus 접근할계정@SID  

이렇게 테스트 하다가 라이브러리 에러 뜨면

* yum install libnsl

요거 해주면 된다.

위 패키지는 보통 개발환경 구축할 때 다 쓰니 이미 설치 돼있겠지만

설치한지 얼마 안돼서 환경 구축 중이면 해야할 것.





<!--

주석 위치

-->




