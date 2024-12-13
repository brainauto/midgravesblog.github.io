---
title: "wiki.js git clone 해서 기본 테마 커스텀 하기 2"
last_modified_at: 2024-12-12 14:00:00 + 09:00
categories:
  - WINDOWS
tags:
  - wiki.js, docker
---

wiki.js 기본 테마 수정
===

기본 테마 커스텀하기 1번에서 dev 모드 설정을 완료 했다면 이제 진짜 기본 테마 수정 준비가 끝났다.

이번 포스트에서는 wiki.js의 못생긴 sidebar의 생김새를 변경하고 HIDE/SHOW 버튼을 만들어 

User의 임의대로 sidebar를 토글시키는 방법을 설명한다.



1. sidebar의 템플릿이 정의되어있는 파일 찾기.

찾는 방법은 yarn dev 로 실행 시킨 후 브라우저에서 개발자모드를 켜 찾아도 되지만 그냥 아래 위치를 찾으면 됨.
```
wiki\client\themes\default\components
```
wiki.js는 Vue를 사용하므로 해당 폴더의 .vue 확장자인 파일 중 nav-sidebar 라는 파일을 vscode로 열어보자.




2. 파일을 찾았으면 이제 vscode로 열어서 내용을 확인해보자.

대충 아래와 같은 템플릿 코드와 js코드가 포함되어 있다.
```
<template lang="pug">
  div
    .pa-3.d-flex(
    v-if='navMode === `MIXED`',
    :class='$vuetify.theme.dark ? `grey darken-5` : `blue darken-3`',
    style='position: relative;'
  )
    ---대충 버튼 템플릿 ~~~~
    ~~~~~~~
</template>
```

```
 기존 .pa-3.d-flex 설정에는 style=position: relative 부분이 포함 되어있지 않은데
 파일 수정하다가 버튼 위치가 원하는 곳으로 가지 않을 걸 대비하여 미리 추가해주자.
```


3. 이제 vue 파일을 수정해서 정말 ui가 변경되는지 새파란 사이드바 우상단에 "Hide" 버튼을 추가해보자.
```
<template lang="pug">
  div
    .pa-3.d-flex(
    v-if='navMode === `MIXED`',
    :class='$vuetify.theme.dark ? `grey darken-5` : `blue darken-3`',
    style='position: relative;'
  )
// 이 부분에 아래 코드를 복붙하면 된다.
    v-btn(
      depressed
      :color='$vuetify.theme.dark ? `red darken-4` : `red lighten-2`'
      style='position: absolute; top: 0px; right: 0px; min-width: 0;'
      @click='hideSidebar'
      :aria-label='$t(`common:sidebar.hide`)'
    )
      v-icon(size='20') mdi-eye-off
```

여기까지 복붙을 완료 했다면 파일을 저장해보자.
dev 모드로 실행된 서버가 자동으로 컴파일을 진행 후 wiki.js에 적용시켜 준다.


4. 제대로 실행됐다면 아래와 같은 버튼이 생긴다.
   실행은 문제없이 됐는데 hide 버튼이 보이지 않는다면 ctrl + F5 버튼으로 새로고침 해보자.

![예제 이미지](./image/wiki-custom-screenshot-1.png)


버튼이 사이드바가 사라진 이후에도 보여야 하니 우측으로 빼볼까?
```
style='position: absolute; top: 0px; right: -20px; min-width: 0;'
```

![예제 이미지](./image/wiki-custom-screenshot-2.png)

sidebar의 영역을 벗어나니 버튼이 짤린다. 그럼 z-index를 높여보면?
```
style="position: absolute; top: -10px; right: -10px; min-width: 0; z-index: 1000;"
```

![예제 이미지](./image/wiki-custom-screenshot-3.png)

어림도 없는 걸 볼 수 있다.

구조도 제대로 모르는데 sidebar 바깥에 버튼을 만들려고 시도하느니 그냥 메인 컨텐츠가 로드되는 페이지에 버튼을 만들어 sidebar옆에 붙여놓기로 했다.


5. wiki.js 페이지의 기본 구성을 담당하는 파일을 열어보자 nav-sidebar.vue 파일이 있는 폴더에 page.vue 파일이 존재한다.


6. page.vue 파일을 열면 대충 아래처럼 길~~게 템플릿 구성이 정의되어있다.

```
<template lang="pug">
  v-app(v-scroll='upBtnScroll', :dark='$vuetify.theme.dark', :class='$vuetify.rtl ? `is-rtl` : `is-ltr`')
    nav-header(v-if='!printView')
    v-navigation-drawer(
      v-if='navMode !== `NONE` && !printView'
      :class='$vuetify.theme.dark ? `grey darken-4-d4` : `primary`'
      dark
      app
      clipped
      mobile-breakpoint='600'
      :temporary='$vuetify.breakpoint.smAndDown'
      v-model='navShown'
      :right='$vuetify.rtl'
      )
      vue-scroll(:ops='scrollStyle')
        nav-sidebar(:color='$vuetify.theme.dark ? `grey darken-4-d4` : `primary`', :items='sidebarDecoded', :nav-mode='navMode')
        ........
        ........
        .....
        .....
        ......

```






<!--

주석 위치

-->



