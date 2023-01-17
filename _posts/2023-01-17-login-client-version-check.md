---
title: "C# 클라이언트 버전 확인하기"
last_modified_at: 2023-01-17 14:00:00 + 09:00
categories:
  - C#
tags:
  - C#
  - window form
  - FileAttributes
  - version management
---

C# 클라이언트 버전 확인하기
===


클라이언트 실행시 특정 파일들의 버전을 불러와 활용하는 기능을 구현하고자한다.

아래 예시는 MSN DOC에 있는 예시로 윈도우 기본 메모장 실행 파일의 버전정보를 불러온다.

파일을 우클릭해서 속성 -> 자세히 탭을 봤을때 볼수있는 정보.

```C#
FileVersionInfo.GetVersionInfo(Path.Combine(Environment.SystemDirectory, "Notepad.exe"));
            FileVersionInfo myFileVersionInfo = FileVersionInfo.GetVersionInfo(Environment.SystemDirectory + "\\Notepad.exe");

            // Print the file name and version number.
            MessageBox.Show("File: " + myFileVersionInfo.FileDescription + '\n' +
               "Version number: " + myFileVersionInfo.FileVersion);
```

위 예시를 참고하면 나머지는 너무 간단해서 예시만 남겨놓음



<!--

주석 위치

-->




