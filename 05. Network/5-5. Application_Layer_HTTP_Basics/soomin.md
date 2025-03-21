# 5-5. 응용 계층 - HTTP의 기초
## ✅DNS와 URI/URL
### ▶️도메인 네임과 DNS
- NW상 호스트 식별은 IP
- IP만으로는 특정 호스트의 특징 알 수X & 호스트의 IP 주소는 언제든 바뀜
- 도메인 네임은 문자열 형태의 호스트 특정 정보로 호스트의 IP 주소와 대응
- 도메인 네임과 그에 대응하는 IP 주소는 네임 서버에서 관리
- 도메인 네임을 관리하는 네임 서버 = DNS 서버
- 도메인 네임을 풀이(resolve)한다 / 리졸빙한다
  - 호스트 → 네임서버 : 특정 도메인 네임을 가진 호스트의 IP 주소가 뭐야? 


- 도메인 네임의 계층적 구조
- 도메인 네임을 관리하는 네임 서버의 계층적 구조 
  - 네임 서버는 분산되어 관리
  - 도메인 네임에 대한 관리 체계는 도메인 네임 시스템


- 호스트 → 로컬 네임 서버 : 도메인 네임 질의
- ISP에서 할당해 주는 공개 DNS 서버 이용 가능 

### ▶️자원과 URI/URL
- URI : 웹 상에서의 자원을 식별하기 위한 정보
  - URN : 이름으로 자원 식별
  - URL : 위치로 자원 식별
  

- 오늘날 URL 사용
- URL 구조 이해하기
1. scheme - 사용할 프로토콜
2. authority - 호스트 특정할 수 있는 IP 주소나 도메인 네임
3. path - 자원이 위치한 경로
4. query - 매개변수 역할 <?키=값&>
5. fragment - 자원에서 특정 부분 


## ✅HTTP의 특징과 메시지 구조
- HTTP 목적 : APP의 다양한 자원을 NW 통해 송수신 

### ▶️HTTP의 특징
#### 1️⃣요청 응답 기반 프로토콜 
#### 2️⃣미디어 독립적 프로토콜 
- 미디어 타입 = MIME 타입
  - HTTP를 통해 송수신하는 자원의 종류
  - 형식: 타입-데이터의 유형/서브타입-세부 유형
#### 3️⃣스테이트리스 프로토콜
- WHY?
  - 많은 클라이언트와 동시 상호작용, 모든 상태 유지는 서버에 큰 부담
  - 클라이언트가 특정 서버에 종속되면, 서버에 문제가 발생시 통신 내역 잃어버림
- HTTP의 중요한 설계 목표 : 확장성과 견고성
  - 서버의 추가나 대체가 쉬워짐
#### 4️⃣지속 연결 프로토콜
- 지속 연결 OR 킵 얼라이브
  - 하나의 TCP 연결 상에서 여러 개의 요청-응답을 주고받을 수 있는 기술 
  - 빠른 속도로 여러 HTTP의 요청과 응답 처리 가능 

#### 🔷HTTP 버전별 특징
- HTTP 1.1 - 현재까지 널리 사용
  - 평문 기반
- HTTP 2.0
  - 바이너리 데이터 기반 송수신
  - 헤더 압축
  - 서버 푸시
  - HTTP 멀티플렉싱 기법 
- HTTP 3.0
  - UDP기반으로 구현된 QUIC 프로토콜 기반으로 동작 
  - 속도 측면 큰 개선 

### ▶️HTTP 메시지 구조 
- 시작 라인
  - 요청인지 응답인지 구분
  - 요청 → 요청 라인
  - 응답 → 상태 라인
  - 중요 정보
    - 메서드 - 클라이언트가 서버의 작업에 수행할 작업의 종류
    - 상태 코드 - 요청에 대한 결과 3자리 정수
    - 이유 구문 - 상태 코드에 대한 설명 
- 필드 라인 - 0개 이상
  - HTTP 헤더 명시
    - 메시지 전송과 관련한 부가 정보이자 제어 정보
    - 헤더 이름 : 헤더 값
- 메시지 본문 - 선택적

## ✅HTTP 메서드와 상태 코드 
- 시작 라인 
  - 요청 라인 = **메서드** | 요청 대상 | HTTP 버전
  - 상태 라인 = HTTP 버전 | **상태 코드** | **이유 구문**(선택적)

### ▶️HTTP 메서드
#### GET과 HEAD
- GET - 자원을 습득하기 위한
  - HOST 헤더 + 요청 대상 = 요청을 보내는 전체 URL
- HEAD - GET과 동일하나, 헤더만을 응답 받는
  - 응답 메시지에 메시지 본문 포함X
#### POST
- 서버로 하여금 특정 작업을 처리하게끔 하는 
- 클라언트가 서버에 새로운 자원을 생성하고자 할 때 
- 응답
  - Location - 생성된 자원의 위치
  - 메시지 본문 - 생성된 자원
#### PUT과 PATCH
- PUT - 자원을 대체하기 위한 (덮어쓰기)
- PATCH - 자원에 대한 부분적 수정을 위한 (부분적 수정)
#### DELETE
- 자원을 삭제하기 위한 

### ▶️HTTP 상태 코드 
- 유사한 결과는 같은 백의 자릿수 공유
#### 100번대 : 정보성
#### 200번대 : 성공
#### 300번대 : 리다이렉션
- 클라이언트가 요청한 자원이 다른 곳에 있을 때 다른 곳으로 요청을 이동시킴
- 응답 메시지의 Location 헤더로 요청한 자원의 위치한 URL 안내
- 301/8 : 영구적 리다이렉션
  - 자원이 완전히 새로운 곳으로 이동
  - 경로가 영구적으로 재지정
  - 요청을 보낸 기존 URL은 기억할 필요 없어짐
- 302/3/7 : 일시적 리다이렉션
  - 자원의 위치가 임시로 변경
  - 요청을 보낸 기존 URL 기억
#### 400번대 : 클라이언트 에러
- 401 : 요청 자원에 대한 유효한 인증이 없음 
  - **인증(Authentication) 요구** - 자신이 누구인지를 증명하는 작업
- 403 : 요청이 서버에 의해 거부됨 
  - **권한/인가(Authorization) 요구** - 인증된 주체에게 허용된 작업
#### 500번대 : 서버에게 잘못이 있음
- 500 : 요청을 처리할 수 없음
- 502 : 중간 서버의 통신 오류 

## ✅HTTP 주요 헤더
### ▶️요청 메시지에서 주로 활용되는 HTTP 헤더
#### Host
- 요청을 보낼 호스트가 명시되는
#### User-Agent
- HTTP 요청을 시작하는 클라이언트 측의 프로그램
#### Referer
- 클라이언트가 요청을 보낼 때 머무르던 URL 명시
- 클라이언트의 유입 경로 파악

### ▶️응답 메시지에서 주로 활용되는 HTTP 헤더
#### Server
- 서버 호스트와 관련된 정보 명시
#### Allow
- 처리 가능한 HTTP 헤더 목록을 알리기 위해
#### Location
- 자원의 위치를 알려 주기 위해
- 주로 리다이렉션이나 새로운 자원이 생성되었을 때

### ▶️요청과 응답 메시지 모두에서 활용되는 HTTP 헤더
#### Date
- 메시지가 생성된 날짜와 시각
#### Content-Length
- 메시지 본문의 바이트 단위 크기
#### Content-Type, Content-Language, Content-Encoding
- 메시지 본문이 어떻게 표현 되었는지 - 표현 헤더
- Type - 본문에서 사용된 미디어 타입
- Language - 본문에 어떤 자연어가 사용되었는지
  - ko-KR
  - 첫 번째 서브 태그 - 특정 언어(소문자)
  - 두 번째 서브 태그 - 특정 국가(대문자)
- Encoding 
  - 메시지 본문을 압축하거나 변환
  - 어떻게 압축/변환 되었는지 알아야 수신지 측에서 해제 가능
#### Connection
- 송신하는 호스트가 어떠한 방식으로 연결을 원하는지
- ex) keep-alive, close

