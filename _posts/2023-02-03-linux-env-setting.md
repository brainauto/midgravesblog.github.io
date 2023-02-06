---
title: "Rocky linux9 LD_LIBRARY_PATH 여러개 사용하기"
last_modified_at: 2023-02-03 14:00:00 + 09:00
categories:
  - LINUX
tags:
  - Linux
---

LD_LIBRARY_PATH 여러개 등록하기
===


이런식으로 돼있는 걸
```
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:${ORACLE_HOME}  
```

이런 식으로 쓰면 PATH 여러개 등록 완료
```
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/lib64:/usr/lib:${ORACLE_HOME}
```

<!--

주석 위치

-->




