---
title: "Visual Studio 2022 template 안나오는 오류 해결"
last_modified_at: 2023-01-17 14:00:00 + 09:00
categories:
  - IDE
tags:
  - Visual Studio
  - '2022'
  - template
---

Visual Studio 2022 template 안나오는 오류 해결
===


Cpp로 콘솔 프로그램을 만들려고 보니 새 프로젝트에서 Cpp 템플릿이 안보인다.

분명 설치는 잘됐는데 왜 안보이지? 하다가 StackOverFlow 에서 방법 찾아냄

> https://stackoverflow.com/questions/41189398/no-templates-in-visual-studio-2017/46895353#46895353

들어가서 보면 답변 중 내문서에있는 사용자 템플릿과 progamfiles 에 있는 템플릿 내용이 상이하면 이런다고 한다.

간단하게 해결 방법은

```

1. 비주얼 스튜디오를 코드없이 실행

2. 도구 - 옵션

3. 프로젝트 및 솔루션 (사용환경에 따라 영어로 돼있을수도있는데 그것도 똑같이 프로젝트 및 솔루션이다.)

4. 하위 탭에 -위치- 를 클릭하면 사용자 프로젝트 템플릿 위치가 내문서로 되어있을 텐데

5. C:\Program Files\Microsoft Visual Studio\2022\사용하는 버전\Common7\IDE\ProjectTemplates\ 이 경로로 바꿔주자

```


굳.



***






<!--

주석 위치

-->




