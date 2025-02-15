## 6-4. 효율적 쿼리

### 1️⃣ 서브 쿼리와 조인

> **서브 쿼리(subquery)**: 다른 SQL문이 포함된 SQL문

> **조인(join)**: 2개의 테이블을 하나로 합치는 것

1. 여러 테이블에 질의하기

```sql
SELECT 테이블1.필드1, 테이블1.필드2, 테이블2.필드3
	FROM 테이블1, 테이블2
	WHERE 테이블1.필드1 = 테이블2.필드2;
```

1. 서브 쿼리

- SELECT문 안에 SELECT문이 포함된 서브 쿼리
- DELETE문 안에 SELECT문이 포함된 서브 쿼리

1. 조인

<img width="492" alt="Image" src="https://github.com/user-attachments/assets/0c3c36eb-0c01-4fbe-94e3-d643fbd03712" />

- INNER 조인
  ```sql
  SELECT 필드
  FROM 테이블1 INNER JOIN 테이블2 ON 조인 조건;
  ```
- OUTER 조인
  ```sql
  SELECT 필드
  FROM 테이블1 LEFT OUTER JOIN 테이블2 ON 조인 조건;

  SELECT 필드
  FROM 테이블1 RIGHT OUTER JOIN 테이블2 ON 조인 조건;

  SELECT 필드
  	FROM 테이블1 LEFT JOIN 테이블2 ON 조인 조건
  	UNION
  SELECT 필드
  	FROM 테이블1 RIGHT JOIN 테이블2 ON 조인 조건;
  ```

1. 뷰

> SELECT문의 결과로 만들어진 가상의 테이블

```sql
CREATE VIEW 뷰_이름 AS SELECT문;
```

- 쿼리의 단순화, 재사용성을 높이기 위해 많이 사용됨
- 특정 사용자에게 테이블의 특정 데이터만을 보여주고자 할 때도 사용
- 조회를 목적으로 사용되는 경우가 많음

1. 인덱스

> 검색 속도 향상을 목적으로 만드는 하나 이상의 테이블 필드에 대한 자료구조

- 특정 필드에 인덱스를 생성한다는 것 = 해당 필드를 기준으로 레코드를 조회하는 것
- 클러스터형 인덱스(clustered index): 테이블당 하나씩 만들 수 있는 인덱스, 기본 키로 지정된 필드는 기본적으로 클러스터형 인덱스
- 세컨더리 인덱스(secondary index, 논클러스터형 인덱스): 테이블당 여러 개가 존재할 수 있지만 클러스터형 인덱스를 활용한 검색보다 일반적으로 느림

```sql
CREATE INDEX 인덱스_이름 ON 테이블_이름 (필드);

SHOW INDEX FROM 테이블_이름;

DROP INDEX 인덱스_이름 FROM 테이블_이름;
```

- 인덱스 생성과 관리에도 부작용이 따르기도 함
- 데이터가 충분히 많은 테이블, 조회가 빈번히 이루어지는 테이블 필드에 만들어 활용하는 것이 좋음
- 일반적으로 테이블당 3개 이하의 인덱스 권장
