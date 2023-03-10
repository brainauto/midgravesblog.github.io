---
title: "정보처리기사 필기 2과목 소프트웨어개발 3"
last_modified_at: 2023-01-17 14:00:00 + 09:00
categories:
  - Certificate
tags:
  - Engineer Information Processing
---

데이터 입출력 구현 C 데이터베이스
===


DBMS
---

* 정의 기능 - DB를 생성하며 저장 구조를 정의

* 조작 기능 - 데이터 검색, 삽입, 삭제, 갱신 - 데이터 공동 이용 제공

* 제어 기능 - 데이터 접근 권한을 제어해 보안 제공, 공동 이용을 하더라도 정확성을 유지 시킴



스키마
---

정의 - DB 구조와 제약조건을 기술하는 것

1) 스키마는 데이터 사전(Data Dictionary)에 저장.

* 데이터 사전 : 시스템 전체에서 나타나는 데이터 항목들에 대한 정보를 지정한 중앙 저장소로, 이 정보에는 항목을 참조하는데 사용되는 식별자, 항목에 대한 엔티티의 구성요소, 항목이 저장되는 곳, 항목을 참조하는 곳 등을 포함

2) 현실 세계의 특정한 한 부분의 표현으로서 특정 데이터 모델을 이용해서 만들어지게 된다.

3) 시간에 따라 불변인 특성을 갖는다. (시불변성)

4) 데이터의 구조적 특성을 의미

5) 인스턴스에 의해 규정




스키마의 구조
<img src="/assets/images/schema.png" width="80%" height="80%" title="스키마의 구조" alt="이미지 보여줄 수 없을때 보일 텍스트"/>



* 외부 스키마 - 사용자의 관점
 * 데이터들을 어떤 형식, 구조, 배치 화면을 통해 사용자에게 보여줄 것인가
 * 전체 데이터 베이스의 한 논리적 부분 -> 서브 스키마
 * 하나의 데이터베이스에는 여러 개의 외부스키마가 존재가능 & 하나의 외부스키마를 여러 개의 응용프로그램이나 사용자가 공용 가능
 * 같은 데이터베이스에 대해서도 서로 다른 관점을 정의할 수 있도록 허용
 * 일반 사용자는 질의어를 이용 DB를 쉽게 사용


* 개념 스키마 - 조직체 전체를 관장하는 입장에서 DB를 정의한 것 (데이터 베이스의 전체적인 논리적 구조)

 * 따라서 조직의 모든 응용시스템에서 필요로 하는 개체 관계, 그리고 제약조건들을 포함하고 있다.
 * DB를 효율적으로 관리하는데 필요한 접근권한, 보안정책, 무결성 규칙등에 관한 사항들도 추가적으로 포함.
 * DB전체를 기술한 것이기 때문에 한 개밖에 존재할 수 없음.


* 내부 스키마 - 물리적인 저장장치 입장에서 DB가 저장되는 방법을 기술한 것
 
 * 구체적으로 개념 스키마를 디스크 기억장치에 물리적으로 구현하기 위한 방법을 기술한 것으로서 주된 내용은 실제로 저장될 내부레코드 형식, 내부레코드의 물리적 순서, 인덱스의 유/무 등에 관한 것.
 * DB는 내부 스키마에 의해서 곧바로 구현되는 것이 아니라 내부 스키마에 기술한 내용에 따라 운영체제의 파일시스템에 의해 물리적 저장장치에 기록 됨.
 * 실무적으로 내부스키마에 의해 DB의 실행 속도가 결정적으로 영향을 받기 때문에 DB의 구축목적에 따라 내부 스키마를 결정해야할 필요가 있다.




데이터 베이스 설계
---

1. 요구조건 분석 - 사용자의 조건 파악(명세 기술 문서화)
2. 개념적 설계 - 다이얻그램 등 개념적으로 설계도를 그려보는 것
3. 논리적 설계 - 모델링(스키마 설계)
4. 물리적 설계 - 필드의 데이터 타입, 인덱스, 테이블 저장 방법 등 정의
5. 데이터베이스 구현



