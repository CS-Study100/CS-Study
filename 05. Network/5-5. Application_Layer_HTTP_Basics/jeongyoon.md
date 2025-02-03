## 2-5. 응용 계층 - HTTP의 기초

### 1️⃣ DNS와 URI/URL

- 도메인 네임(domain name): 문자열 형태의 호스트 특정 정보, 호스트의 IP 주소
- DNS 서버: 도메인 네임을 관리하는 네임 서버
  <img width="258" alt="Image" src="https://github.com/user-attachments/assets/3b0f2920-bdcf-46cd-bca6-341f2763811a" />

- 계층적 구조
  <img width="471" alt="Image" src="https://github.com/user-attachments/assets/6200f572-9481-46f1-b379-bd029264a2ca" />

- 자원(resource): 네트워크 상의 메시지를 통해 주고받는 최종 대상
- URI(Uniform Resource Identifier): 웹 상에서의 자원을 식별하기 위한 정보
  - 이름 기반 식별 ➡️ URN(Uniform Resource Name)
  - 위치 기반 식별 ➡️ URL(Uniform Resource Locator)

<img width="505" alt="Image" src="https://github.com/user-attachments/assets/c8b82a32-2fd3-49ac-b424-af3939893101" />

1. scheme: 자원에 접근하는 방법
2. authority: 호스트를 특정할 수 있는 IP 주소나 도메인 네임
3. path: 자원이 위치하고 있는 경로
4. query: URL에 대한 매개변수 역할을 하는 문자열
5. fragment: 자원의 일부분, 한 조각을 가리키기 위한 정보

### 2️⃣ HTTP의 특징과 메시지 구조

1. 요청 응답 기반 프로토콜: HTTP 요청 메시지-HTTP 응답 메시지
2. 미디어 독립적 프로토콜: 주고받을 미디어 타입에 특별한 제한을 두지 않고, 독립적으로 작동 가능
3. 스테이트리스 프로토콜: 서버는 HTTP 요청을 보낸 클라이언트 관련 상태를 기억하지 않음
4. 지속 연결 프로토콜: 하나의 TCP 연결 상에서 여러 개의 요청-응답을 주고받을 수 있는 기술

- HTTP 메시지 구조
  <img width="185" alt="Image" src="https://github.com/user-attachments/assets/aa3fbfed-251c-4ac1-85b3-caef771b1f9f" />
  1.  시작라인(start-line): 요청 라인, 상태 라인
  2.  필드라인(field-line): HTTP 헤더 명시(헤더 이름, 헤더 값)

### 3️⃣ HTTP 메서드와 상태 코드

- HTTP 메서드
  1. GET, HEAD
  2. POST
  3. PUT, PATCH
  4. DELETE
- HTTP 상태 코드
  1. 200번대: 성공 상태 코드
  2. 300번대: 리다이렉션 상태 코드
  3. 400번대: 클라이언트 에러 상태 코드
  4. 500번대 상태 코드

### 4️⃣ HTTP 주요 헤더

- 요청 메시지에서 주로 활용되는 HTTP 헤더
  1. Host: 요청을 보낼 호스트가 명시되는 헤더
  2. User-Agent: 요청 메시지를 보낸 클라이언트의 프로그램과 관련한 정보 명시
  3. Referer: 클라이언트가 요청을 보낼 때 머무르던 URL이 명시됨
- 응답 메시지에서 주로 활용되는 HTTP 헤더
  1. Server: HTTP 응답 메시지를 보내는 서버 호스트와 관련한 정보 명시
  2. Allow: 처리 가능한 HTTP 헤더 목록을 알리기 위해 사용
  3. Location: 클라이언트에게 자원의 위치를 알려주기 위해 사용
- 요청과 응답 메시지 모두에서 활용되는 HTTP 헤더
  1. Date: 메시지가 생성된 날짜와 시각에 관련된 정보를 담은 헤더
  2. Content-Length: 메시지 본문의 바이트 단위 크기를 표현
  3. Content-Type, Content-Language, Content-Encoding: 메시지 본문이 어떻게 표현되었는지 명시
  4. Connection: HTTP 메시지를 송신하는 호스트가 어떠한 방식의 연결을 원하는지 명시
