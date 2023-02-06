---
title: "C# winform 로그인 클라이언트 UI 제작 기록"
last_modified_at: 2023-01-17 14:00:00 + 09:00
categories:
  - C#
tags:
  - C#
  - window form
  - UI
---

C# winform 로그인 클라이언트 UI 제작 기록
===


사내에서 사용할 로그인 시스템 제작 중 아무리 봐도 기본 winform은 너무 못생겨서 꾸미려고 보니 내 미적 센스가 기본 winform 디자인보다 못하다는 걸 깨달았다.

그럼 다른 사람들이 만든 모양이라도 참고해서 만들어야지 하고 검색해보면 죄다 winform 이 아니라 WPF 라서 그냥 엎어버리고 WPF로 만들어야 하나 싶었는데 아래 블로그가 구원해줌

> https://k4keye.tistory.com/159

UI 제작 과정이 상세하게 적혀있어서 그냥 보고 따라만 해도 멀쩡한 UI 하나가 뚝딱 만들어졌다.
내 프로젝트엔 MetroModernUI 가 설치돼있긴한데 딱히 설치 안했어도 도양은 똑같이 나왔을 것 같다.


물론 기본 틀로 쓰고 제작하면서 어레인지를 할 생각인데 기본 틀만 해도 나름 예쁘게 나와서 혹시 이글을 보는 사람이 있으면 링크 UI랑 아래 UI랑 같이 참고하면 좋을 듯해 캡처 첨부.

 > 에셋 이미지에 넣은 그림 삽입


그런데 border 를 none 으로 해놓으니 빌드했을때 MainForm 테두리가 자글자글해지는 문제가 생김

해결할 방법을 찾다보니 DrawBorder 기능으로 해결이 가능하다고 해서 해보니 정말 해결이 가능했다.
아래 예시처럼 만들면 원래 아무것도 없을 MainForm 속성 -> 이벤트 -> 모양 Paint 에 Form1_Paint 가 생기니 적용 시키고 빌드해보면 MainForm 테두리가 그려지는걸 볼수있다.

```C#
	private void Form1_Paint(object sender, PaintEventArgs e)
	{

		Rectangle borderRectangle = this.ClientRectangle;
		borderRectangle.Inflate(-10, -10);
		ControlPaint.DrawBorder3D(e.Graphics, borderRectangle, 
			Border3DStyle.Raised);
	}

```

그런데 나는 좀 예쁘게 해보겠다고 가장자리를 둥글게 만들었으니 적용하면 가장자리가 누락돼서 이걸로 해결못했다.

DrawBorder 로 곡선도 넣을 수 있긴한데 그건 버튼, 라벨 같은 도구에만 가능하길래 이걸로 해결하는건 포기함

아래에 DrawBorder 기능 관련 링크 첨부할테니 읽어보고 다른 방법 찾아볼 사람은 찾아보면 될 듯.

> http://msdn.microsoft.com/ko-kr/library/system.windows.forms.controlpaint(v=vs.110).aspx

이 모든게 WinForm 이 아닌 WPF 에서는 매우 간단하게 해결되니 어지간하면 그냥 WPF 쓰자.

WPF가 WinForm 보다 신경쓸게 많긴 한데 UI관련해서는 WinForm에서 뭐빠지게 구현할거 WPF 에선 그냥 구현함


***


DrawLine.Pen 으로 테두리를 그려넣었다.

아래처럼 0.0 좌표부터 그림을 그려넣고 MainForm 테두리에 볼드체로 선을 그려넣어 자글자글한 테두리도 가리고 모양도 깔끔하게 다듬었다.


```

코드삽입

```

> 그림삽입


<!--

주석 위치

-->




