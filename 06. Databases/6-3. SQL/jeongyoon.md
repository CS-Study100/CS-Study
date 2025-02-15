## 6-3. SQL

### 1️⃣ 데이터 정의 언어(DDL)

> Data Definition Language
> 

| 종류 | 설명 |
| --- | --- |
| CREATE | 데이터베이스 혹은 데이터베이스 객체 생성 |
| ALTER | 데이터베이스 객체 갱신
ex) 테이블에 필드 및 제약 조건을 추가/삭제 |
| DROP | 데이터베이스 객체 삭제
ex) 테이블이나 데이터베이스를 삭제 |
| TRUNCATE | 테이블 구조를 유지한 채 모든 레코드 삭제 |
1. CREATE

```sql
CREATE DATABASE 데이터베이스_이름;
```

```sql
CREATE TABLE 테이블_이름 (
		필드_이름1 필드_타입,
		필드_이름2 필드_타입,
		필드_이름3 필드_타입,
		...
);
```

- 필드_타입 우측 or 하단에 특정 필드가 지켜야 할 제약조건을 명시
    
    
    | 키워드 | 제약 조건 |
    | --- | --- |
    | PRIMARY KEY | 특정 필드를 기본 키로 지정 |
    | UNIQUE | 특정 필드가 고유한 값을 갖도록 지정 |
    | FOREIGN KEY | 특정 필드를 외래 키로 지정 |
    | DEFAULT 기본값 | 기본값 지정 |
    | NULL/NOT NULL | 특정 필드에 NULL 값을 허용/허용하지 않음 |

```sql
CREATE TABLE 테이블_이름 (
		필드_이름1 필드_타입,
		필드_이름2 필드_타입,
		필드_이름3 필드_타입,
		...
		[CONSTRAINT 제약_조건_이름] PRIMARY KEY (필드_이름),
		[CONSTRAINT 제약_조건_이름] FOREIGN KEY (필드_이름) REFERENCES 테이블_이름2 (필드_이름),
		[CONSTRAINT 제약_조건_이름] UNIQUE (필드_이름),
);
```

1. ALTER

```sql
-- 새로운 필드 추가
ALTER TABLE 테이블_이름 ADD COLUMN 필드_이름 필드_타입 [제약 조건];

-- 기존 필드 수정
ALTER TABLE 테이블_이름 CHANGE COLUMN 기존_필드_이름 새_필드_이름 필드_타입 [제약_조건];

-- 기존 필드 삭제
ALTER TABLE 테이블_이름 DROP COLUMN 필드_이름;

-- 외래키 제약 조건 추가
ALTER TABLE 테이블_이름 [ADD CONSTRAINT 제약_조건_이름]
	ADD FOREIGN KEY (필드_이름) REFERENCES 참조_테이블_이름 (참조_필드);
```

1. DROP

```sql
DROP DATABASE 데이터베이스_이름;
DROP TABLE 테이블_이름;
```

1. TRUNCATE

```sql
TRUNCATE TABLE 테이블_이름;
```

### 2️⃣ 데이터 조작 언어(DML)

> Data Manipulation Language
> 

| 종류 | 설명 |
| --- | --- |
| SELECT | 테이블의 레코드 조회 |
| INSERT | 테이블에 레코드 삽입 |
| UPDATE | 테이블의 레코드 수정 |
| DELETE | 테이블의 레코드 삭제 |

1. INSERT

```sql
INSERT INTO 테이블_이름(필드1, 필드2) VALUES (값1, 값2);
```

- 무결성 제약 조건을 지켜야 함

1. UPDATE와 DELETE

```sql
UPDATE 테이블_이름
	SET 필드1 = 값1, 필드2 = 값2, ...
	WHERE 조건식;
	
DELETE 테이블_이름
	WHERE 조건식;
```

<img width="494" alt="Image" src="https://github.com/user-attachments/assets/940e071e-b2f6-4c7d-8701-f8e4db01a76d" />

- 외래 키 제약 조건 (ON UPDATE, ON DELETE)
    
    
    | 제약 조건 | 설명 |
    | --- | --- |
    | CASCADE | 참조하는 데이터도 함께 수정/삭제 |
    | SET NULL | 참조하는 데이터를 NULL로 변경 |
    | SET DEFAULT | 참조하는 데이터를 기본값으로 변경 |
    | RESTRICT | 수정/삭제를 허용하지 않음 |
    | NO ACTION | (MySQL)사실상 RESTRICT와 동일하게 동작 |

1. SELECT

```sql
SELECT 필드1, 필드2, ...
	FROM 테이블_이름
	WHERE 조건식
	GROUP BY 그룹화할_필드
	HAVING 필터_조건
	ORDER BY 정렬할_필드
	LIMIT 레코드_제한
```

- 연산/집계 함수
    
    
    | 함수 | 설명 |
    | --- | --- |
    | COUNT | 조회된 레코드 개수 반환 |
    | SUM | 조회된 레코드 총합 반환 |
    | AVG | 조회된 레코드 평균 반환 |
    | MAX | 조회된 레코드 최대값 반환 |
    | MIN | 조회된 레코드 최소값 반환 |
- GROUP BY: 특정 필드를 그룹화
- HAVING: GROUP BY절로 그룹화된 결과에 조건을 적용
- ORDER BY: 특정 필드를 기준으로 데이터를 정렬
- LIMIT: 조회할 레코드 수를 제한

`FROM ➡️ WHERE ➡️ GROUP BY ➡️ ****HAVING ➡️ SELECT ➡️ ORDER BY ➡️ LIMIT`

### 3️⃣ 트랜잭션 제어 언어(TCL)

> Transaction Control Language
> 

| 종류 | 설명 |
| --- | --- |
| COMMIT | 데이터베이스 작업 반영 |
| ROLLBACK | 작업 이전 상태로 되돌림 |
| SAVEPOINT | 롤백의 기준점 설정 |

```sql
SAVEPOINT 세이브포인트_이름;

ROLLBACK TO SAVEPOINT 세이브포인트_이름;
```

### 4️⃣ 데이터 제어 언어(DCL)

> Data Control Language
> 

| 종류 | 설명 |
| --- | --- |
| GRANT | 사용자에게 권한 부여 |
| REVOKE | 사용자로부터 권한 회수 |