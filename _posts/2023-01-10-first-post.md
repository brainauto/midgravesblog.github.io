---
title: "정보처리기사 : 소프트웨어설계"
last_modified_at: 2023-01-11 09:31:00 + 09:00
categories:
  - Certificate
tags:
  - 정보처리기사
  - 소프트웨어설계
  - 요구사항분석
---

요구사항분석 
===

대충 강조하고 싶은 소제목
---

# 글머리 1
## 글머리 2
### 글머리 3
#### 글머리 4
##### 글머리 5
###### 글머리 6

> 아웃룩 첨부 메일같은 들여쓰기 기능
> > 줄 생김


1. 요구사항이란
2. 요구사항 유형
3. 요구사항 프로세스


* "*로 글머리 기호 쓸때 뭘 쓰던 상관 없음"
  * "*로 글머리 기호 쓸때 뭘 쓰던 상관 없음"
    * "*로 글머리 기호 쓸때 뭘 쓰던 상관 없음"

+ "+로 글머리 기호 쓸때 뭘 쓰던 상관 없음"
  + "+로 글머리 기호 쓸때 뭘 쓰던 상관 없음"
    + "+로 글머리 기호 쓸때 뭘 쓰던 상관 없음"

- "-로 글머리 기호 쓸때 뭘 쓰던 상관 없음"
  - "-로 글머리 기호 쓸때 뭘 쓰던 상관 없음"
    - "-로 글머리 기호 쓸때 뭘 쓰던 상관 없음"

* "*" 혼합 사용 가능
  - "-"
      + "+"
        + "+"


텝으로 들여쓰기 테스트
---
This is a normal paragraph

    여기는 코드 넣는 부분 여기만 강조됨
    paragraph - 단락

들여쓰기 끝내면 코드 블록 강조도 끝
들여쓰기 시작과 끝 문장을 코드블록과 한줄 띄어쓰지 않으면 들여쓰기 취소됨

예시 
    여기는 코드 넣는 부분 여기만 강조됨
    paragraph - 단락
들여쓰기 테스트


페이지 나누기 용도 
---
순서대로 * * *, \*\*\*, \*****, - - -
* * *

***

*****

- - -



코드블럭 사용방법
---

예시

```
<pre>
<code>
  public class BootSpringBootApplication {
    public static void main(String[] args) {
      System.out.println("블로그 테스트");
  }
}
</code>
</pre>
```

이렇게 쓰면

웹페이지에는

<pre>
<code>
public class BootSpringBootApplication {
  public static void main(String[] args) {
    System.out.println("블로그 테스트");
  }
}
</code>
</pre>

이렇게 보임


이렇게도 쓸수 있는데 이렇게 쓰면

<pre>
<code>
```
public class BootSpringBootApplication {
  public static void main(String[] args) {
    System.out.println("Hello, Honeymon");
  }
}
```
</code>
</pre>

이렇게 보임

```
public class BootSpringBootApplication {
  public static void main(String[] args) {
    System.out.println("Hello, Honeymon");
  }
}
```

또 이렇게 언어 명시해주면 해당 언어와 똑같이 코드 강조해줌

<pre>
<code>
```JAVA
public class BootSpringBootApplication {
  public static void main(String[] args) {
    System.out.println("Hello, Honeymon");
  }
}
```
</code>
</pre>

이렇게

```JAVA
public class BootSpringBootApplication {
  public static void main(String[] args) {
    System.out.println("Hello, Honeymon");
  }
}
```


<!--
가나다라마바사아
본문 중간에 제목 넣고 글씨 강조 할 때
===

이것도 같이 되는지 테스트
본문 중간에 살짝 작은 제목 넣고 클씨 강조 할때
---

위처럼 두 줄로 쓰면 === 이것과 --- 이게 동작하지 않는다.


-->




