## 6-6. NoSQL

### 1️⃣ RDBMS vs NoSQL: NoSQL의 특징

- NoSQL(Not Only SQL)

1. 키-값 데이터베이스(key-value database)

> 데이터베이스에 레코드를 키(필드)와 값의 쌍으로 저장하는 데이터베이스
> 
- Redis, Memcached는 모두 기본적으로 인메모리 데이터베이스
- 비교적 가벼운 정보를 저장하는 경우
- 다른 주요 데이터베이스의 보조 데이터베이스로써 사용되는 경우도 많음

1. 도큐먼트 데이터베이스(document-oriented database)

> 레코드를 도큐먼트라는 단위로 저장하고 관리하는 데이터베이스
> 
- 도큐먼트(document): 정형화되어 있지 않은 NoSQL 레코드의 단위(JSON이나 XML 같은 형식)
- MongoDB: 하나의 레코드를 JSON 형태의 데이터로 만들어 관리
    - 고정된 스키마가 없기 때문에 각 도큐먼트가 유연한 스키마를 가질 수 있음
    
    <img width="289" alt="Image" src="https://github.com/user-attachments/assets/08ba9c8a-4c27-40a1-9798-1a6688681e4a" />
    
- 도큐먼트가 모여 컬렉션을 이룸

1. 그래프 데이터베이스

> 데이터베이스에 저장하고자 하는 데이터를 그래프의 노드 형태로 저장하는 데이터베이스
> 
- neo4j 등
- 노드 간의 연결 관계와 방향을 표현할 수 있어, 데이터 간의 관계성이 중요한 레코드를 저장하기 위해 주로 사용됨

1. 칼럼 패밀리 데이터베이스

> 행과 열이라는 개념이 존재하고 로우 키(row key)를 통해 특정 행을 식별
> 
- Cassandra, HBase 등
- 정규화나 조인을 사용하지 않고, 스키마가 고정되어 있지 않아 자유롭게 열을 추가할 수 있음
- 동적으로 변할 수 있는 열들이 있고, 거기에 행 데이터들이 대응되어 있는 것

<img width="461" alt="Image" src="https://github.com/user-attachments/assets/a5ac5c7b-64df-4fd7-93f6-80e1d881f51d" />

- 관련 있는 열들이 모여 칼럼 패밀리 단위 형성 → 칼럼 패밀리는 키스페이스라는 단위를 형성

- NoSQL은 높은 부하를 감당하거나 대용량 데이터를 다루는 분산 환경에서 사용됨
- 성능 향상을 위해 ACID와 정규화를 엄격히 준수하지는 않음
- RDBMS에 비해 데이터 무결성과 일관성이 다소 저하될 수 있지만, RDBMS에 비해 큰 성능 향상을 얻을 수 있음

### 2️⃣ 다양한 NoSQL: MongoDB와 Redis

1. MongoDB
- 데이터베이스와 컬렉션 생성
    
    ```sql
    user 데이터베이스_이름
    db.createCollection("컬렉션_이름")
    ```
    
- 단일 레코드 삽입
    
    ```sql
    db.컬렉션_이름.insertOne({}) # JSON 형태
    db.컬렉션_이름.insertMany()
    ```
    
    - 도큐먼트 확인
        
        ```sql
        db.컬렉션_이름.find()
        ```
        
- 도큐먼트 갱신
    
    ```sql
    db.컬렉션_이름.updateOne()
    
    $set: { 변경할_필드: 변경할_내용, ... }
    
    db.컬렉션_이름.updateMany()
    ```
    
    - 특정 필드 제거
        
        ```sql
        db.컬렉션_이름.updateMany( ..., { $unset : { ... } }}
        ```
        
- 도큐먼트 삭제
    
    ```sql
    db.컬렉션_이름.deleteOne()
    db.컬렉션_이름.deleteMany()
    ```
    

1. Redis
- 문자열 타입의 값을 다룰 때 사용 가능한 명령어
    
    
    | 종류 | 설명 |
    | --- | --- |
    | SET | 문자열 값 저장 |
    | SETNX(SET if Not eXists) | 키가 존재하지 않는 경우에만 문자열 값 저장 |
    | GET | 문자열 값 조회(키를 통해 대응되는 값 조회) |
    | MGET | 여러 문자열 값 조회 |
    | DEL | 키 삭제 |
- 리스트 타입의 값을 다룰 때 사용 가능한 명령어
    
    
    | 종류 | 설명 |
    | --- | --- |
    | LPUSH | 리스트의 왼쪽(앞)에 새로운 요소 추가 |
    | RPUSH | 리스트의 오른쪽(뒤)에 새로운 요소 추가 |
    | LPOP | 리스트의 왼쪽(앞)에서 요소를 제거 후 반환 |
    | RPOP | 리스트의 오른쪽(뒤)에서 요소를 제거 후 반환 |
    | LRANGE | 지정된 범위의 요소들을 반환 |
    | LLEN | 리스트 길이 반환 |