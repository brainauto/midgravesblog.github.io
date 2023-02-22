---
title: "리눅스 기본 사용법 모음"
last_modified_at: 2023-02-15 14:00:00 + 09:00
categories:
  - LINUX
tags:
  - Linux
---

how to use linux - basic 모음
===




윈도우에서 리눅스 파일 또는 디렉토리 가져오기
```
scp는 잘 안되고 pscp 가 잘됨

pscp -r root@100.100.100.100:/home/폴더명/폴더명 C:\desktop
```

진짜 basic
```
chmod -R 777 filename
```

소유자, 소유 그룹 변경
```
chown -R user1:user2 test.txt - user1 소유자 user2 소유 그룹, -R 하위 디렉토리 까지 전부 변경
```


만든거 실행할때 안꺼지게 실행
```
nohub ./파일명 &  - &은 백그라운드 실행 nohub는 no hang up 세션 끊겨도 실행 유지
```


ShellScript나 프로그램 실행 시 Crontab 으로 반복 실행할 시간 설정
* 첫 번째
  * 분
* 두 번째
  * 시간
* 세 번째
  * 일 별
* 네 번째
  * 월 별
* 다섯 번째
  * 요일
```
* * * * *	매일 1분마다 실행
5 * * * *	매일 매시간 05분에 실행 (1시간 간격)
*/5 * * * *	매일 5분마다 실행
*/10 * * * *	매일 10분마다 실행

0,30 10 * * 0,2,3	매주 일, 화, 수요일 17시 00분과 10시 30분에 실행
0 0 1,15 * 1	매달 1일과 15일 & 월요일 24시 00분에 실행
0 6,12 * * 0,4	일, 목요일마다 06시, 12시에 실행
0 20 * * 1-6	월 ~ 토 20시 00분에 실행
```


실행파일 실행하면서 자동으로 로그 남기기
```
nohup ./hello.out > $(date +%Y-%m-%d).log 2>&1 &

hello.out이 다음날에도 실행되고 있으면 알아서 다음날 로그파일 만들고 거기에 로그 입력

파일내부에 로그 찍는 기능 만들고 같이 쓰면 완벽함

nohup ./hello.out > /home/log/$(date +%Y-%m-%d).log 2>&1 &

로그 폴더에 생성하려면 로그가 쌓일 Ex) /home/log 경로를 미리 생성해줘야함

```


프로세스 자원 사용량 확인
```
# 11111 예시 프로세스 pid 
# pid: 프로세스 ID
# pcpu: CPU 사용률
# pmem: 메모리 사용률
# rss: 물리 메모리 사용량 
# vsz: 가상 메모리 사용량
# cmd: 커맨드
$ ps -o pid,pcpu,pmem,rss,vsz,cmd -p 11111
  PID %CPU %MEM   RSS    VSZ CMD
11111  0.0  0.5 100874 894574 프로세스이름
```

프로세스 자원 실시간 사용량 확인
```
top -p 18299

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                               
11111 root      20   0 85016 6672 5816 S  0.0  0.5 00:00.01 프로세스이름
```



<!--

주석 위치

-->




