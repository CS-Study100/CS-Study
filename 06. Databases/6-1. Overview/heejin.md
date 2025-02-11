# 6-1 데이터베이스의 큰 그림

## ✅ 데이터베이스와 DBMS
- **데이터베이스(Database)**: 여러 사람이 공유하여 사용하는 체계화된 데이터의 집합.
- **DBMS(Database Management System)**: 데이터를 효율적이고 안전하게 관리하기 위한 소프트웨어.
- **기능**: 동시 처리, 데이터 저장 및 관리, 보안 제공.

## ✅ DBMS의 종류
### 관계형 데이터베이스 관리 시스템(RDBMS)
- 테이블(표) 형태로 데이터를 저장
- 대표적인 RDBMS: MySQL, Oracle, PostgreSQL, SQL Server, MariaDB

### NoSQL 데이터베이스
- 비정형 데이터 관리에 강점
- 대표적인 NoSQL DB: MongoDB, Redis

## ✅ 데이터베이스에서 SQL의 역할
- **DDL(Data Definition Language)**: `CREATE`, `ALTER`, `DROP`, `TRUNCATE`
- **DML(Data Manipulation Language)**: `SELECT`, `INSERT`, `UPDATE`, `DELETE`
- **DCL(Data Control Language)**: `GRANT`, `REVOKE`
- **TCL(Transaction Control Language)**: `COMMIT`, `ROLLBACK`, `SAVEPOINT`

## ✅ 파일 대신 데이터베이스를 이용하는 이유
- **데이터 무결성 제공**
- **불필요한 중복 저장 방지**
- **데이터 변경 시 연관 데이터 유지 가능**
- **정교한 검색 가능**
- **백업 및 복구 용이**

## ✅ 데이터베이스의 저장 단위
- **엔터티(Entity)**: 독립적으로 존재하는 개체
- **속성(Attribute)**: 엔터티가 가진 데이터
- **레코드(Record)**: 한 개의 엔터티 인스턴스
- **릴레이션(Relation)**: 테이블 형태로 엔터티 저장

## ✅ 트랜잭션과 ACID 원칙
- **트랜잭션(Transaction)**: 데이터베이스에서 하나의 작업 단위
- **ACID 원칙**
  - **원자성(Atomicity)**: 모든 작업이 성공하거나 모두 실패해야 함 (All or Nothing)
  - **일관성(Consistency)**: 트랜잭션 완료 후 데이터 무결성 유지
  - **격리성(Isolation)**: 동시 실행되는 트랜잭션 간 간섭 방지
  - **지속성(Durability)**: 성공한 트랜잭션은 영구적으로 저장됨

## ✅ 관계형 데이터베이스 vs NoSQL
- **RDBMS**: 정형 데이터를 테이블 구조로 저장
- **NoSQL**: 비정형 데이터를 다양한 방식으로 저장 (문서, 그래프, 키-값 등)
- **대표적인 NoSQL DB**: MongoDB(문서형), Redis(키-값 저장소)

