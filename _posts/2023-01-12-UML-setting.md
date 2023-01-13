---
title: "VSCODE + plantuml + graphviz 설치법"
last_modified_at: 2023-01-12 14:00:00 + 09:00
categories:
  - Development
tags:
  - VScode
  - Plantuml
  - UML
  - graphviz
---

VSCODE + plantuml + graphviz 설치하고 UML 만들기
===


1. extensions에서 plantuml 검색하고 제일 위에있는거 인스톨
2. http://www.graphviz.org/download/ 에서 7.0.6 32비트 zip 다운로드
3. 압축 풀고 C:\Program Files (x86) 에 Graphviz 폴더 통째로 붙여넣기
4. 윈도우 시스템 속성
5. 사용자 환경변수 Path에 %programfiles(x86)%\Graphviz\bin 등록
6. 시스템 환경변수 Path에 %programfiles(x86)%\Graphviz\bin\dot.exe 추가
7. UML 사용환경 세팅 완료
8. 이제 txt 파일 하나 만들고 확장자 plantuml 로 변경 후 VScode로 열기

```
@startuml title 

나의 첫번째 시퀀스 다이어그램

 A -> B : 부르는 함수이름

@enduml 
```

9. 입력 후 저장

10. Alt + D 누르면 아래 그림처럼 UML을 사용할 수 있게 된다.

11. 그림 삽입


12. JAVA 설치 안돼있으면 JAVA 에러나는데 https://www.oracle.com/java/technologies/downloads/#jdk19-windows 에서 운영체제에 맞는거 받아서 설치
13. 설치 진행시 설치 경로는 바꾸고싶으면 바꾸고 굳이 바꿀 이유가 없어서 안바꾸고 진행함
14. 시스템 변수에서 변수이름을 "JAVA_HOME"으로 지정하고 JDK가 설치된 폴더를 지정한다.

본인 예시
```
  변수 이름 : JAVA_HOME
  변수 값 : %programfiles%\Java\jdk-19
```
16. 시스템 변수 하나 더 추가
본인 예시
```
  변수 이름 : CLASSPATH
  변수 값 : %JAVA_HOME%\lib
```
17. 시스템 환경 변수 path에  %JAVA_HOME%\bin 추가
18. 프롬프트창 열고 java, javac 가 아래 처럼 잘 나오는지 확인

```
>java -version 

java version "19.0.1" 2022-10-18
Java(TM) SE Runtime Environment (build 19.0.1+10-21)
Java HotSpot(TM) 64-Bit Server VM (build 19.0.1+10-21, mixed mode, sharing)

>javac -version

javac 19.0.1
```

19. 위처럼 안나오면 환경변수 설정간 오타있는지 확인 할 것. 
20. 이제 다시 plantuml 파일을 열어서 Alt + d 를 눌러보면
21. 그림 삽입

위처럼 잘 나올 것이다.

끝


그래픽 처리된 이미지를 저장하는 방법은 찾아보니 아래 같은 방법이 있다.
---

1. Ctrl + Shift + P 를 누른후
2. PlantUML: Export Current File Diagram 을 입력하다보면 나오는 PlantUML: Export Current File Diagram 을 선택
3. png 나 svg(벡터 그래픽)를 선택해주면 plantuml 파일이 있는 디렉토리에 자동으로 디렉토리 하나 만들어지면서 거기에 저장됨
\* PDF로 저장은 방법은 있으나 복잡하니 굳이 필요한게 아니라면 위 방법을 사용하자.










<!--

주석 위치

-->




