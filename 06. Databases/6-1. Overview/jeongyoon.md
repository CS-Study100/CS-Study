## 6-1. 데이터베이스의 큰 그림

### 1️⃣ 데이터베이스와 DBMS

- 데이터베이스(database): 원하는 기능을 동작시키기 위해 마땅히 저장해야 하는 정보의 집합
- 데이터베이스 관리 시스템(DBMS): 데이터베이스를 관리하기 위한 프로그램
- DBMS의 종류

  1. 관계형 데이터에비스 관리 시스템(RDBMS)
  2. NoSQL 데이터베이스 관리 시스템(NoSQL DBMS)

- 서버로서의 DBMS
  - DBMS 클라이언트는 DBMS에 쿼리를 보냄
  - SQL(Structured Query Language): RDBMS에서 데이터를 조작하고 관리하기 위한 언어
  - DDL(데이터 정의), DML(데이터 조작), DCL(데이터 제어), TCL(트랜잭션 제어)

### 2️⃣ 파일 대신 데이터베이스를 이용하는 이유

1. 데이터 일관성 및 무결성 제공
2. 불필요한 중복 저장 제거
3. 데이터 변경 시 연관 데이터 변경 용이
4. 정교한 검색
5. 백업 및 복구 용이

### 3️⃣ 데이터베이스의 저장 단위와 트랜잭션

- 엔티티(entity): 독립적으로 존재할 수 있는 객체
- 속성(attribute): 엔티티의 특성
- 도메인(domain): 엔티티의 속성이 가질 수 있는 값의 집합
- 릴레이션(relation): RDBMS에서 표현되는 이차원 테이블 형태의 엔티티 집합
- 컬렉션(collection): NoSQL DBMS에서 표현되는 엔티티 집합
- 레코드(record): 데이터베이스에 기록된 각각의 엔티티
- 필드(field): 데이터베이스에 저장된 엔티티 속성

- 스키마(schema): 데이터베이스에 저장되는 레코드의 구조와 제약 조건을 정의한 것
- RDBMS ➡️ 스키마 정의 / NoSQL ➡️ 스키마-리스 데이터베이스

- 트랜잭션(transaction): 데이터베이스와의 논리적 상호작용의 단위
- 트랜잭션이 지켜야 하는 성질(ACID)
  1. 원자성(Atomicity): 하나의 트랜잭션 결과가 모두 성공하거나 모두 실패하는 성질
  2. 일관성(Consistency): 트랜잭션 전후로 데이터베이스가 일관된 상태를 유지하는 성질
  3. 격리성(Isolation): 동시에 수행되는 여러 트랜잭션이 서로 간섭하지 않도록 보장하는 성질
  4. 지속성(Durability): 트랜잭션이 성공적으로 완료된 후에 그 결과가 영구적으로 반영되는 성질
