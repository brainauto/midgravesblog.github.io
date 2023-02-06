---
title: "Rocky linux9에 VSCode 설치하기"
last_modified_at: 2023-02-01 14:00:00 + 09:00
categories:
  - IDE
tags:
  - Linux
  - VSCode
---

GUI linux에 VSCode 설치 방법
===


아래 내용은 Rocky9 DVD ISO로 GUI 환경을 설치했을 사용자를 위한 내용임

출처
> https://www.linuxcapable.com/how-to-install-visual-studio-code-on-rocky-linux/


step 1. OS 최신으로 업데이트 하기
---

```
sudo dnf upgrade --refresh
```


step 2. 설치하기 전에 GPG key import 하기 
---

```
rpm --import https://packages.microsoft.com/keys/microsoft.asc
```


step 3. 레포지토리 위치 가져오기
---

```
printf "[vscode]\nname=packages.microsoft.com\nbaseurl=https://packages.microsoft.com/yumrepos/vscode/\nenabled=1\ngpgcheck=1\nrepo_gpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc\nmetadata_expire=1h" | sudo tee -a /etc/yum.repos.d/vscode.repo
```
위 내용 처음부터 끝까지 쭉 복사해서 붙여넣고 실행

그리고 오류 메시지 없이 잘 실행됐으면

* nano /etc/yum.repos.d/vscode.repo

위 명령어 실행해서 잘 들어갔는지 확인



step 4. 이제 VSCode 설치하기
---

아래가 스테이블 빌드 버전
```
sudo dnf install code -y
```

이게 인사이더 버전 
```
sudo dnf install code-insiders -y
```

둘 중 필요한 거 하나만 설치하면 된다.



step 5. 다 됐으면 설치된 VSCode 최신으로 업데이트 시도

```
dnf upgrade --refresh
```
업데이트할 거 없으면 좋고 있으면 업데이트 ㄱㄱ



* 번외 
스테이블 버전을 설치하면 안나오겠지만 설치하다가 GPG KEY 어쩌고 나오면 그냥 yes 하면 된다.



끝.





<!--

주석 위치

-->




