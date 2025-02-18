# 6-3. SQL
## ✅데이터 정의 언어 - DDL
#### ▶️CREATE
```sql
//데이터베이스
CREATE DATABASE 데이터베이스_이름; //생성
SHOW DATABASES; //조회
USE 데이터베이스_이름 //사용

//테이블
CREATE TABLE 테이블_이름 (
	post_id INT [PRIMARY KEY AUTO_INCREMENT],
    user_id INT,
    title VARCHAR(50) [NOT NULL],
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    ...
    [CONSTRAINT FK_user_id] FOREIGN KEY (user_id) REFERENCES users(user_id)
); //생성
DESC 테이블_이름; //조회
SHOW TABLES; // 데이터베이스에 속한 전체 테이블 조회
```
- 특정 필드가 지켜야 할 제약 조건
  - PRIMARY KEY
  - UNIQUE(고유 키) - 중복 값 X, 여러 개 O, NULL O
  - FOREIGN KEY
  - DEFAULT 기본값
  - NULL/NOT NULL
  
#### ▶️ALTER
- ALTER문은 테이블뿐만 아니라 뷰,인덱스 등에도 적용 가능
```sql
ALTER TABLE 테이블_이름 ADD COLUMN 필드_이름 필드_타입 [제약 조건] //추가
ALTER TABLE 테이블_이름 CHANGE COLUMN 기존_필드_이름 새_필드_이름 필드_타입 [제약 조건] //수정
ALTER TABLE 테이블_이름 DROP COLUMN 필드_이름 //삭제
//제약 조건 추가
ALTER TABLE 테이블_이름 ADD FOREIGN KEY (필드_이름) REFERENCES 참조_테이블_이름(참조_필드)
ALTER TABLE 테이블_이름 ADD UNIQUE (필드_이름) 
ALTER TABLE 테이블_이름 MODIFY 필드_이름 필드_타입 NOT NULL
ALTER TABLE 테이블_이름 ADD PRIMARY KEY (필드_이름)
```
#### ▶️DROP
```sql
DROP DATABASE 데이터베이스_이름;
DROP TABLE 테이블_이름;
```
#### ▶️TRUNCATE
- 테이블의 구조 유지한 채로 테이블의 모든 레코드를 삭제
```sql
TRUNCATE TABLE 테이블_이름;
```

## ✅데이터 조작 언어 - DML
#### ▶️INSERT
```sql
INSERT INTO 테이블_이름(필드1, 필드2) VALUES 
	(값1, 값2),
    (값1, 값2)
    ...
    ; //삽입
```
- 무결성 제약 조건 지키기
  - NOT NULL - NULL 삽입X
  - UNIQUE - 중복값X
  - 외래 키 - 존재하지 않는 레코드 참조X
 
#### ▶️UPDATE와 DELETE
```sql
UPDATE 테이블_이름
	SET 필드1 = 값1, 필드2 = 값2, ...
    WHERE 조건식;
    
DELETE 테이블_이름
    WHERE 조건식;
```
- WHERE절 생략 시 모든 레코드 갱신 
- SET의 '=' → 대입 연산자
- WHETE의 '=' → 비교 연산자

🔷외래 키 참조 상황에서의 레코드 수정 및 삭제
- CREATE/ALTER TABLE문에서 제약 조건으로써 정의
  - 수정될 경우 - ON UPDATE 뒤에 명시
  - 삭제되 경우 - ON DELETE 뒤에 명시
- 제약 조건
  - CASCADE - 참조하는 데이터도 함께 수정/삭제
  - SET NULL - 참조하는 데이터를 NULL로 변경
  - SET DEFAULT - 참조하는 데이터를 DEFAULT로 변경
  - RESTRICT - 수정/삭제 허용X
  - NO ACTION - RESTRICT와 동일하게 동작 

#### ▶️SELECT
```sql
SELECT 필드1, 필드2, ...
	FROM 테이블_이름
    WHERE 조건식
    GROUP BY 그룹화할_필드
    HAVING 필터_조건
    ORDER BY 정렬할_필드
    LIMIT 레코드_제한
```

🔷패턴 검색 - 문자열에서 특정 패턴 찾기
  - LIKE '_문자열%'
    - % - 0개 이상 일치
    - _ - 정확히 1개 일치
    
🔷연산/집계 함수
- COUNT - 개수
- SUM - 총합
- AVG - 평균
- MAX - 최댓값
- MIN - 최솟값

#### ▶️GROUP BY
- 특정 필드를 기준으로 필드를 그룹화 

#### ▶️HAVING
- HAVING - 그룹화된 레코드에 대한 조건식
- WHERE - 그룹화 되긴 전 개별 레코드에 대한 조건식

#### ▶️ORDER BY
- 특정 필드 기준으로 데이터 정렬
- ASC - 오름차순 → 기본
- DESC - 내림차순

#### ▶️LIMIT
- 조회할 레코드 수 제한
- 레코드의 시작점 설정 - LIMIT 2,2: 두 번째로 떨어진 레코드부터 2개의 레코드 조회 

### SELECT문의 실행 순서
FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY → LIMIT 

## ✅트랜잭션 제어 언어 - TCL
- START TRANSACTION / BEGIN 명령 → DBMS에게 이제부터 트랜잭션이 시작됨을 알림
  - MySQL의 자동 커밋이 꺼진 상태로 실행
#### ▶️COMMIT 
- 데이터베이스에 작업 반영
  - 변경된 내용을 적용한 뒤 종료
- MySQL에서는 자동 커밋이 기본으로 됨
```sql
SET autocommint=0; //자동 커밋 off
```
#### ▶️ROLLBACK 
- 작업 이전의 상태로 되돌림
  - 변경된 내용을 적용하지 않고 종료
#### ▶️SAVEPOINT 
- 롤백의 기준점 설정
```sql
  SAVEPOINT 세이프포인트_이름 // 돌아갈 시점 지정
  ROLLBACK TO SAVEPOINT 세이프포인트_이름
```

## ✅데이터 제어 언어 - DCL
#### ▶️GRANT
- 사용자에게 권한 부여
#### ▶️REVOKE
- 사용자로부터 권한 회수

