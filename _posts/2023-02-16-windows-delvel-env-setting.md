---
title: "기타 윈도우 개발 환경 세팅"
last_modified_at: 2023-02-16 14:00:00 + 09:00
categories:
  - Windows
tags:
  - Windows
---

기타 윈도우 개발 환경 세팅
===


오라클 ODAC 64Bit 설치
---

* 당연히 C:\app\Administrator\product\11.2.0\client_1 이 부분은 오라클 런타임이나 오라클 설치한 곳 경로
본인 경로에 맞춰서 수정하면 됨.


1. 오라클의 XCopy 버전은 명령어를 통해서 직접 설치해야함

2. 파일 다운로드 링크
 > https://www.oracle.com/database/technologies/odac-downloads.html

3. Zip 파일 풀고 cmd 관리자 권한으로 실행

4. 압축풀린 경로로 이동

5. 이동한 경로에서 명령어를 입력하여 설치
 > install.bat all C:\app\Administrator\product\11.2.0\client_1 odac

6. 다음 경로로 이동 (ODP.NET)
 > C:\app\Administrator\product\11.2.0\client_1\ODP.NET\bin\4

7. 해당경로에서 DLL 등록
 > OraProvCfg.exe /action:gac /providerpath:C:\app\Administrator\product\11.2.0\client_1\ODP.NET\bin\4\Oracle.DataAccess.dll

8. 다음 경로로 이동 (ASP.NET)
 > C:\app\Administrator\product\11.2.0\client_1\ASP.NET\bin\4

9. 해당 경로에 DLL를 등록 
 > OraProvCfg.exe /action:gac /providerpath:C:\app\Administrator\product\11.2.0\client_1\ASP.NET\bin\4\Oracle.Web.dll

CMD 닫고 윈도우 리부팅



*****


DB character set이 US7ASCII 라서 select 가져오면 한글 깨질때 세팅
---

```C#
// 환경변수 세팅 후 유니코드를 활성화 시키는 방법이 있고
Environment.SetEnvironmentVariable("NLS_LANG", "AMERICAN_AMERICA.US7ASCII");
string connectionString = "Provider=OraOLEDB.Oracle;Data Source=DBSID;User ID=ID;Password=PW;Unicode=True;";
// 환경변수 세팅 없이 하는 아래같은 방법이 있다.
string connectionString = "Provider=OraOLEDB.Oracle;Data Source=DBSID;User ID=ID;Password=PW;Unicode=True;Charset=KO16KSC5601;";
```

당연히 한글 지원 안하는 character set 인데 어떻게 한글이 저장되고 이용할 수 있는지 설명이 쉽게 정리된 블로그 링크

 > https://manord.tistory.com/19

혹시 블로그 삭제 될 것 대비해서 중요 내용은 발췌 해옴
```
"
캐릭터셋은 US7ASCII지만, 실제로 "완성형 + 한글 윈도우즈 코드" 페이지(KO16MSWIN949)의 데이터를 저장해 온 경우
데이터는 현재 상태에서 가공하지 않은 채, 딕셔너리에 있는 캐릭터셋 정보만을 강제로 KO16MSWIN949로 변환하는 방식으로 활용 할 수 있다.
US7ASCII 데이터베이스에 한글을 저장하게 될 경우, 한 글자당 2바이트로 저장된다.  
일반적으로 사용하는 클라이언트는 대부분 Windows-949(한글 Windows OS)나 KSC5601 완성형(UNIX계열)이고
이들은 모두 2바이트이다.
"

쁧/뷣/톩/똠 등  같은 일반적이지 않은 한글을 제외하고 정상적인 완성형 한글은 모두 US7ASCII 에서 KO16KSC5601 로 가져올 수 있다.

```



*****



VS 에서 exe 파일에 DLL, 리소스 등을 merge 해서 빌드
---

1. nuget에서 Costura.Fody 검색 후 설치 그리고 같이 설치되는 패키지들 최신 스테이블 버전으로 업데이트 하면 끝
2. 이제 릴리즈 할때 알아서 기타 파일들을 알아서 merge 해주니 신경 쓸게 줄어든다.


*****



윈폼 UI 깔끔한 버전 
---

1. nuget에서 MetroModernUI 설치 
2. public partial class Form1 : MetroFramework.Forms.MetroForm //모양 바꿀 폼 상속 클래스를 메트로UI로 변경하기

이제 저장하고 디자인.cs 를 보면 form 모양이 그나마 나아진걸 볼수 있음.




*****










<!--

주석 위치

-->




