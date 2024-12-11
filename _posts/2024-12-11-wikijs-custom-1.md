---
title: "wiki.js git clone 해서 기본 테마 커스텀 하기"
last_modified_at: 2024-12-11 14:00:00 + 09:00
categories:
  - WINDOWS
tags:
  - wiki.js, docker
---

wiki.js 기본 테마 수정 및 dev 모드 접속 방법
===


준비물
docker (원하는 버전 아무거나)
vscode (원하는 버전 아무거나)
node (20.0.0 이상)
nvm (최신이면 좋음)
yarn (최신이면 좋음)



1. github 에서 최신 릴리즈 가져오기

그냥 git clone 하게 되면 홈에 있는 파일을 가져오는데 혹시 몰라 릴리즈 버전을 찾아서 다운로드했다.
어차피 윈도우에서 돌릴 거니까.
```
https://github.com/requarks/wiki 에 접속해서 페이지 우측 중앙에 있는 최신 릴리즈 버전을 클릭한다.
   (2024.12.11 기준으로 최신 릴리즈 버전은 v2.5.305)
```

2. 개발자가 업로드해놓은 4개의 Assets 중 Source code.zip 을 다운로드 한다.
보통 아래와 같이 4개가 업로드 되어있다.
```
wiki-js-windows.tar.gz
wiki-js.tar.gz
Source code(zip)
Source code(tar.gz)
```

3. 다운로드한 zip 파일을 압출풀기 하고 원하는 드라이브에 옮겨 넣는다.
```
나는 압축을 풀고 폴더 이름을 알아보기 쉽게 wiki로 바꾸어 D:\ 드라이브에 옮겨넣었다.
```

4. docker로 postgres DB 실행하기

vscode 터미널에서 아래 명령줄을 입력하면 wiki.js가 제공하는 샘플 config.yml을 수정없이 사용 가능하다.

docker-compose.yml 로 관리해도 되지만 어차피 실행만 시키고 기본 테마의 UI만 뜯어 고칠 용도이니 대충 사용했다.
```
docker run --name postgres-wikijs -e POSTGRES_USER=wikijs -e POSTGRES_PASSWORD=wikijsrocks -e POSTGRES_DB=wiki -v /path/to/local/data:/var/lib/postgresql/data -d -p 5432:5432 postgres
```

5. docker가 잘 실행됐으면 이제 D:\wiki 폴더로 들어가서 Package.JSON을 수정하자.

```
"name": "wiki",
  "version": "2.5.305",  -- 이 부분을 최신 릴리즈버전으로 변경!!!
  "releaseDate": "2019-01-01T01:01:01.000Z",
  "description": "A modern, lightweight and powerful wiki app built on NodeJS, Git and Markdown",
  "main": "wiki.js",
  "dev": true,  ---- 이 부분은 기본이 false 인데 true 로 변경해야 yarn으로 빌드 및 개발자 모드 실행이 가능하다.
  "scripts": {
    "start": "node server",
    "dev": "cross-env NODE_OPTIONS=--openssl-legacy-provider node dev",  ---- 이 부분은 기본이 cross-env 가 없다. 윈도우에서 cross-env 로 바꾸지 않고 yarn 으로 실행하여 하면 환경변수 오류가 생기니 반드시 고치자.
    "build": "NODE_OPTIONS=--openssl-legacy-provider webpack --profile --config dev/webpack/webpack.prod.js",
    "watch": "NODE_OPTIONS=--openssl-legacy-provider webpack --config dev/webpack/webpack.dev.js",
    "test": "eslint --format codeframe --ext .js,.vue . && pug-lint server/views && jest",
    "cypress:open": "cypress open",
    "postinstall": "patch-package"
  },
```

6. Package.JSON 의 수정이 끝나면 모듈 설치 진행.
그냥 install하면 의존성 오류가 날텐데 그냥 무시하고 설치 하자.
```
cd D:\wiki

npm install --legacy-peer-deps
```

7. yarn 으로 cross-env 를 추가
```
yarn add cross-env
```

8. vscode에서 환경변수 추가 
```
$env:NODE_OPTIONS="--openssl-legacy-provider"
```

9. 마지막으로 yarn dev 를 실행
```
yarn dev
```

10. 실행이 정상적으로 완료되고 127.0.0.1:3000 으로 접속 가능하다면 이제 wiki.js 커스텀 준비가 완료됐다.
```
이 글을 보는 사람은 wiki.js를 커스텀 하려는 사람일 테니
로컬 호스트로 접속 후 계정 생성, 로그인 까지는 설명 하지 않는다.
```


<!--

주석 위치

-->




