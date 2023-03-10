---
title: "jekyll 문법 대충 모음"
last_modified_at: 2023-01-11 09:31:00 + 09:00
categories:
  - blog
tags:
  - git blog
  - minimal mistakes
  - jekyll
  - HTML
  - MARKDOWN
---

git blog
===

대충 강조하고 싶은 소제목
---

```
가나다라마바사아
본문 중간에 제목 넣고 글씨 강조 할 때
===

이것도 같이 되는지 테스트
본문 중간에 살짝 작은 제목 넣고 클씨 강조 할때
---

위처럼 한줄이 아니라 두 줄로 쓰면 === 이것과 --- 이게 동작하지 않는다.
```


```
# 글머리 1
## 글머리 2
### 글머리 3
#### 글머리 4
##### 글머리 5
###### 글머리 6
```

# 글머리 1
## 글머리 2
### 글머리 3
#### 글머리 4
##### 글머리 5
###### 글머리 6



```
> 아웃룩 첨부 메일같은 들여쓰기 기능
> > 줄 생김
```


> 아웃룩 첨부 메일같은 들여쓰기 기능
> > 줄 생김



```
1. git
2. github
3. git blog
```

1. git
2. github
3. git blog


* "*로 글머리 기호 쓸때"
  * "*로 글머리 기호 쓸때"
    * "*로 글머리 기호 쓸때"

+ "+로 글머리 기호 쓸때"
  + "+로 글머리 기호 쓸때"
    + "+로 글머리 기호 쓸때"

- "-로 글머리 기호 쓸때"
  - "-로 글머리 기호 쓸때"
    - "-로 글머리 기호 쓸때"

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

````
```
public class BootSpringBootApplication {
  public static void main(String[] args) {
    System.out.println("블로그 테스트");
  }
}
```
````

이렇게 보임

```
public class BootSpringBootApplication {
  public static void main(String[] args) {
    System.out.println("블로그 테스트");
  }
}
```

또 이렇게 언어 명시해주면 해당 언어와 똑같이 코드 강조해줌

````
```JAVA
public class BootSpringBootApplication {
  public static void main(String[] args) {
    System.out.println("블로그 테스트");
  }
}
```
````

그런데 \`\`\`JAVA 이렇게 사용하면 MD파일에서는 색칠 되는데 
아래처럼 정작 웹페이지에는 색칠 안 됨.

```JAVA
public class BootSpringBootApplication {
  public static void main(String[] args) {
    System.out.println("블로그 테스트");
  }
}
```

해결하려다가 안돼서 그냥 아래처럼 사용함

```
{% highlight ruby linenos %}
 def foo
  puts 'foo'
end
{% endhighlight %}
```

{% highlight ruby linenos %}
def foo
  puts 'foo'
end
{% endhighlight %}


````
공지사항 같이 두번 강조할 때
<div class="notice--primary" markdown="1">

안에 코드블럭도 사용가능

```java
String str = "hello git blog";

public class javablock{
  public static void main(String[] args){
    system.out.println("%d", str);
  }
}
```

</div>
````



```
<details>
<summary>접기/펼치기</summary>
<div markdown="1">

|제목|내용|
|--|--|
|1|1|
|2|10|

</div>
</details>
```


<details>
<summary>접기/펼치기</summary>
<div markdown="1">

|제목|내용|
|--|--|
|1|1|
|2|10|

</div>
</details>








<!--

주석 위치

-->




