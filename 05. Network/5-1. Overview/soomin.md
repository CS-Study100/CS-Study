# 5-1. 네트워크의 큰 그림 
## ✅네트워크의 기본 구조
- 네트워크는 그래프의 형태라고 할 수 있다.
  - 네트워크 기기 = 노드
  - 네트워크 기기 간에 정보를 주고받는 유무선의 통신 매체 = 간선
- 네트워크 토플로지 : 네트워크 상의 노드와 노드 사이의 연결 구조 
- 네트워크가 어떻게 배치되는지에 따라 ⇒ 망형, 트리형, 링형, 성형, 버스형(선형)


- 호스트
  - 네트워크의 가장자리에 위치
  - 정보를 최초 송신 & 최종 수신 
  - 노트북 웹브라우저로 구글 홈페이지에 접속  
    = 노트북과 구글 서버 컴퓨터가 호스트
    1. 노트북이 구글의 서버 컴퓨터에게 웹 페이지를 가져다 달라고 요청
    2. 구굴의 서버 컴퓨터가 노트북에게 웹 페이지로 응답 
- 클라이언트 : 요청을 보내는 호스트 (노트북)
- 서버 : 응답을 보내는 호스트 (구글 서버 컴퓨터)


- 중간 노드의 역할은 호스트가 주고 받는 정보를 원하는 수신지까지 안정적으로 전송하는 것
  - 중간 노드로써의 역할을 수행하는 네트워크 장비들 : 스위치, 라우터, 공유기
  

### ▶️LAN과 WAN
- 네트워크의 규모에 따라 LAN과 WAN 구분
- **Local Area Network**
  - 가정이나 기업처럼 비교적 가까운 거리를 연결하는 한정된 공간에서의 네트워크 
  - 공유기로 모든 네트워크 기기가 통신한다면 LAN이 공유기를 기준으로 구축된 거
    - 해당 공유기와 연결된 네트워크 기기들은 모두 같은 네트워크에 속해 있음
  - 모든 네트워크 기기들이 같은 LAN에서만 정보를 주고 받는건X
  - LAN간의 통신도 빈번함
- **Wide Area Network**
  - WAN을 통해 LAN간의 통신이 이루어짐
  - 인터넷을 가능하게 하는 네트워크 
  - ISP라는 인터넷 서비스 업체가 구축하고 관리 
  - 국내 ISP : KT, LG유플러스, SK브로드밴드 

### ▶️패킷 교환 네트워크
- 서로 다른 NW에 있는 두 호스트가 통신 매체를 통해 100GB 주고받는다면 
  - 호스트는 100GB를 한 번에 전송할 수 있을까? X
  - 여러 데이터로 쪼개서 송수신됨
  - 패킷 : 송수신되는 데이터의 단위 
- 오늘날 패킷 교환 네트워크를 대부분 사용
  - 패킷 단위로 정보를 쪼개서 송수신하고 수신지에서 재조립 


- 패킷 : 페이로드 + 헤더 (+ 트레일러)
  - 페이로드 : 패킷에서 송수신하고자 하는 데이터 = 택배 물품
  - 헤더 & 트레일러 : 패킷에 추가되는 부가 정보 = 택배 송장
  

### ▶️주소의 개념과 전송 방식 
- 네트우크상의 두 호스트가 패킷을 주고 받으려면?
- 주소 : 패킷의 헤더에 명시 (IP주소, MAC주소)
- 수신지 유형의 종류
  - **유니캐스트** : 일대일
  - **브로드캐스트** : 네트워크상의 모든 호스트에게 MSG 전송
    - 브도드캐스트 도메인: 전송되는 범위 
    - 호스트가 같은 브로드캐스트 도메인에 속해 있으면 같은 LAN에 속해 있다고 간주 
    
  - 멀티캐스트 : 네트워크 내의 동일 그룹에 속한 호스트에게만 전송
  - 애니캐스트 : 네트워크 내의 동일 그룹 중 가장 가까운 호스트에게만 전송


## ✅두 호스트가 패킷을 주고받는 과정
- 네트워크 내의 호스트들은 서로가 주고받을 내용을 이해할 수 있어야 함
### ▶️프로토콜
- 서로 주고받는 정보를 이해하기 위한 규칙
  - 두 호스트가 서로 다른 LAN에 속해있음, 주고 받는 패킷이 NW 장비를 거쳐야함 
  - 호스트와 거쳐 갈 NW 장비는 패킷의 내용을 이해할 수 있어야 하니까 프로토콜이 필요
- NW에서 통신을 주고받는 노드 간의 합의된 규칙이나 방법
- 호스트와 NW 장비는 같은 프로토콜 이해하고, 같은 프로토콜로 통신
- 주요 프로토콜 : IP, ARP, TCP, UDP, HTTP


- 프로토콜마다 목적과 특징이 다르다 
  - IP는 NW 간의 주소를 지정
  - ARP는 IP 주소와 MAC 주소를 대응 
  - HTTPS는 HTTP에 비해 보안상 안전
  - TCP는 UDP에 비해 신뢰성이 높다 
- 프로토콜마다 패킷의 내용도 다르다 
- 프로토콜의 목적과 특징을 이해하기 위해서는 프로토콜의 패킷 헤더를 분석해 보면 된다

### ▶️네트워크 참조 모델
- 통신이 이루어지는 단계를 계층적으로 표현 
- 송신 : 상위 계층 → 하위 계층
- 수신 : 상위 계층 ← 하위 계층
- 대표적인 NW 참조 모델 : OSI 모델, TCP/IP 모델


**OSI 모델**
- 국제 표준화 기구에서 생성 
- 통신 단계를 7개의 계층으로 
 
 1️⃣물리
   - 비트 신호(0과1)를 주고 받는
   - 신호를 유무선 통신 매체를 통해 운반 
 
 2️⃣데이터 링크
   - 같은 LAN에 속한 호스트끼리 정보 주고 받기 
   - 같은 NW에 속한 호스트 식별위한 MAC주소 사용
   - 물리 계층을 통해 주고 받은 정보에 오류가 없는지 확인 
   - 1,2계층은 HW와 밀접 
   
 3️⃣네트워크
  - NW간 통신을 가능하게
  - LAN은 넘어 다른 NW와 통신을 주고받기 위한 
  - NW간 통신 과정에서 호스트를 식별할 수 있는 IP주소 사용

 4️⃣전송
  - 전송 도중 유실되거나 순서가 뒤바뀌지 않도록 신뢰성 있는 전송 보장(TCP, UDP)
  - 포트를 통해 특정 APP과의 연결 다리 역할 
 
 5️⃣세션
  - APP간의 연결 상태 유지, 생성, 끊기
  
 6️⃣표현
  - 변역기 같이 인코딩, 압축, 암호화
 
 7️⃣응용
  - 사용자와 가장 밀접하게 여러 NW 서비스 제공 (HTTP, HTTPS, DNS)
  
  
**TCP/IP 모델**
- OSI 모델 : NW의 이론적 기술에 중점 
- TCP/IP 모델 : 구현과 프로토콜에 중점
- 4계층 
  1️⃣네트워크 액세스 (링크/네트워크 인터페이스) - 데이터 링크
  
  2️⃣인터넷 - 네트워크
  
  3️⃣전송 - 전송
  
  4️⃣응용 - 세션+표현+응용

### ▶️캡슐화와 역캡슐화
- 송신할 때, 상위 계층으로부터 내려받은 패킷을 페이로드로 삼는다
- 각 계층에 포함된 프로토콜의 각기 다른 목적과 특징에 따라 헤더 혹은 트레일러를 덧붙인 다음 하위 계층으로 전달한다 
- 캡슐화 : 송신 과정에서 헤더를 추가해 나가는 과정
- 역캡슐화 : 캡슐화 과정에서 붙인 헤디러르 각 계층에서 확인한 뒤 제거
- 각 계층마다 패킷을 지칭하는 이름이 다르다 
  - 물리 : 심볼 / 비트
  - 데이터 링크 : 프레임
  - 네트워크 : 패킷 / 데이터그램
  - 전송 : TCP - 세그먼트, UDP - 데이터그램 
  - 그 이상 : 데이터 / 메시지
  
## ✅네트워크 지도 그리기 
- CH2 : 물리 계층과 데이터 링크 계층
  - 오늘날 두 계층이 공통된 기술(이더넷)을 기반으로 구현 
  - 물리 계층 → 유무선 통신 매체
  - 데이터 링크 계층 → 주고받는 프레임의 형태로 NW 장비들
  - 대표적인 NW 장비
    - NIC : NW와의 연결 다리
    - 허브 : 물리계층의 대표 HW
    - 스위치 : 데이터 링크 계층의 대표 HW

- CH3 : 네트워크 계층
  - NW 계층의 가장 중요한 프로토콜인 IP의 목적과 특징
  - IP 기반 주소 체계
  - IP의 전송 특징을 보완하는 프로토콜 ICMP & ARP
  
- CH4 : 전송 계층 
  - TCP와 UDP의 목적과 전송 특징 
    - UDP가 제공하지 않는 TCP 기능
      - 연결 수립과 종료
      - 오류•흐름•혼잡 제어
      - 상태 관리

- CH5~6 : 응용 계층 
  - DNS, URI/URL → HTTP → HTTPS → TLS/SSL
  - 클라이언트와 서버 사이에 위치한 중간 서버
  - NW 안전성 
