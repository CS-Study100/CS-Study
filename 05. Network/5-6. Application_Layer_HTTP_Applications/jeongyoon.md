## 2-6. 응용 계층 - HTTP의 응용

### 1️⃣ 쿠키

- 쿠키(cookie): HTTP의 스테이트리스한 특성을 보완하기 위한 수단, 서버에서 생성되어 클라이언트 측에 저장되는 <이름, 값> 쌍 형태의 데이터

### 2️⃣ 캐시

- 캐시(cache): 응답받은 자원의 사본을 임시 저장하여 불필요한 대역폭 낭비와 응답 지연을 방지하는 기술

### 3️⃣ 콘텐츠 협상

- 표현(representation): 송수신 가능한 자원의 형태
- 콘텐츠 협상(content negotiation): 같은 자원에 대해 할 수 있는 여러 표현 중 클라이언트가 가장 적합한 자원의 표현을 제공하는 기술

### 4️⃣ 보안: SSL/TLS와 HTTPS

- SSL(Secure Sockets Layer)
- TLS(Transport Layer Security)
- TLS 핸드셰이크
  1. TLS 핸드셰이크를 통해 암호화 통신을 위한 키를 생성/교환할 수 있음
  2. 인증서 송수신과 검증이 이루어질 수 있음
- 인증 기관(CA: Certification Authority): 인증서의 발급과 검증, 저장 등의 역할을 수행하는 공인 기관

<img width="475" alt="Image" src="https://github.com/user-attachments/assets/8c74434a-0238-4f77-81a5-715f8c3487fd" />
