---
title: "정보처리기사 필기 2과목 소프트웨어개발 4"
last_modified_at: 2023-01-17 14:00:00 + 09:00
categories:
  - Certificate
tags:
  - Engineer Information Processing
---

데이터 입출력 구현 D SQL
===


SQL
---

* DDL - 스키마 정의, 수정, 삭제
 * create, drop, alter

* DML - 데이터 삽입, 삭제, 갱신, 검색
 * insert, delete, update, select

* DCL - 접근 권한
 * grant, revoke, commit, rollback



* 데이터 접속 (Data Mapping)
 * SQL Mapping - jdbc odbc, JPA/Hibernate, Mybatis 등 
 * ORM (Object Relational Mapping) - Node.js, django 등 

ORM의 예시

아래 두 코드는 동일한 값을 반환. 대충 select, from 같은 구절을 생략하게 해줌

```python
파이썬에 장고 라이브러리 사용
User.objects.filter(is_active=True)
```

```sql
SELECT * FROM User WHERE is_active = 1
```


* 트랜잭션(Transaction) - DB 연산 작업 단위
 * 원자성(atomic) - 트랜잭션은 모두 실행되던지 실패하면 모두 실행되지 않아야 함
 * 일관성(consistency) - 트랜잭션이 성공했다면 DB는 일관성을 유지 해야한다. 특정한 조건을 두고 그 조건을 만족 하는지 검사 
 * 독립성(Isolation) - 트랜잭션 도중에는 다른 연산이 끼어들지 못한다.
 * 영속성(Durability) - 트랜잭션이 성공적이라면 그 결과는 완전히 반영 되어야 한다. 완전 반영 후에는 로그가 남아 로그를 이용해 트랜잭션 수행 전으로 되돌릴 수 있어야 한다. 

* 따라서 트랜잭션은 로그저장이 완료된 시점에서 종료가 되어야한다.



절차형 SQL
---


* 절차형 SQL - 반복하는 SQL
 * 프로시저 - 특정 기능을 수행하는 트랜잭션 언어로서 호출을 통해 저장해둔 sql 작업을 수행
 * 트리거 - 데이터 입력, 갱신, 삭제 등 이벤트가 발생하면 작업을 자동 수행
 * 사용자 정의함수 - 프로시저와 유사하며 호출되면 작업하고 결과값을 return 으로 반환

* 절차형 SQL의 테스트와 디버깅 - 문장 그대로임 show 로 오류 확인 하는것만 기억하면 될 듯

* 쿼리 성능 최적화 - 옵티마이즈 스킬(최적 경로 서칭 모듈) 등을 말함


* ATM - 성능 관리를 위해 접속자, 자원현황, 트랜잭션 수행내역, 장애진단 등을 모니터링을 제공하는 도구




