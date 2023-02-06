---
title: "Rocky linux9 VSCode 개발 환경설정"
last_modified_at: 2023-02-01 14:00:00 + 09:00
categories:
  - IDE
tags:
  - Linux
  - VSCode
  - Cpp
---

GUI linux에 VSCode 환경 설정하기
===


출처
> https://polarcompass.tistory.com/151

언제 삭제될지 몰라 백업용으로 카피. 위 링크가 삭제됐으면 아래 내용 보면 됨.



step 0. 필요하면 한국어 플러그인 설치
---

korean language pack for visual studio code 
플러그인 설치하기



step 1. C/C++ 플러그인 설치
---
플러그인 에서 C/C++ 검색하고 제일 위에있는 마소 공식 설치하기



step 2. ctrl+shift+e 눌러서 작업 폴더 설정
---

폴더 신뢰할건지 물어보면 확인 누르면 됨


step 3. c/c++ extension 설치 
---
대충 C 또는 C++ 예제 파일 하나 만들면 확장 패키지를 설치하라고 나온다.

설치하라고 나오는거 설치해주면 된다.



step 4. test.cpp로 파일 하나 만들어 준 후 아래 코드를 복붙한다 
---

```C++
#include <iostream>
#include <vector>
#include <string>

using namespace std;

int main()
{
    vector<string> msg {"Hello", "C++", "World", "from", "VS Code", "and the C++ extension!"};

    for (const string& word : msg)
    {
        cout << word << " ";
    }
    cout << endl;
}
```


step 5.  (터미널 > 기본 빌드 작업 구성 클릭
---
C/C++ g++ 활성 파일 빌드 선택

tasks.json 이 생성 될 탠데 생성되면 아래 코드를 복붙한다.

```C++
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


step 6.  launch.json 생성. 
---
Fn + F5 눌러 debug를 실행해준다

launch.json  파일 생성 되면 아래 코드 복붙한다.

```C++
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "g++ build and debug active file",
      "type": "cppdbg",
      "request": "launch",
      "program": "${fileDirname}/${fileBasenameNoExtension}",
      "args": [],
      "stopAtEntry": false,
      "cwd": "${workspaceFolder}",
      "environment": [],
      "externalConsole": false,
      "MIMode": "gdb",
      "setupCommands": [
        {
          "description": "Enable pretty-printing for gdb",
          "text": "-enable-pretty-printing",
          "ignoreFailures": true
        }
      ],
      "preLaunchTask": "g++ build active file",
      "miDebuggerPath": "/usr/bin/gdb"
    }
  ]
}
```


주의점. tasks.json 의 label 부분과

```
"label": "clang++ build active file",
```

launch.json의 preLaunchTask 부분 이름이 같아야 한다.

```
"preLaunchTask": "clang++ build active file"
```

한글로 되어있을 경우엔 되도록 영어로 바꿔 주도록 한다.




step 7. c_cpp_properties.json 파일 세팅
---

Ctrl+Shift+P 단축키로 Command Palette 열어준다.

* 선택 1. C/C++:Edit Configurations (UI) 로 UI 형태로 세팅하거나

* 선택 2. C/C++:Edit Configurations (JSON) 으로 아래 코드를 복붙 해준다. - 추천


```C++
{
  "configurations": [
    {
      "name": "Linux",
      "includePath": ["${workspaceFolder}/**"],
      "defines": [],
      "compilerPath": "/usr/bin/gcc",
      "cStandard": "c11",
      "cppStandard": "c++17",
      "intelliSenseMode": "clang-x64"
    }
  ],
  "version": 4
}
```



* 끝.

이제 test.cpp 디버그 해보면 실행이 가능한 걸 볼 수 있음.



<!--

주석 위치

-->




