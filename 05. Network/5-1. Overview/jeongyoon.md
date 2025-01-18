## 5-1. 네트워크의 큰 그림

### 1️⃣ 네트워크의 기본 구조

- 네트워크 토폴로지(network topology): 네트워크 상에서 노드와 노드 사이의 연결 구조

<img width="566" alt="Image" src="https://github.com/user-attachments/assets/a356009f-6bc3-430d-95cf-1a9e03c52a76" />

- 호스트(host): 네트워크의 가장자리에 위치하면서 네트워크를 통해 주고받는 정보를 최초로 송신하고 최종 수신하는 노드
- 클라이언트(client): 요청을 보내는 호스트
- 서버(server): 응답을 보내는 호스트

- LAN과 WAN

  - LAN(Local Area Network): 근거리 네트워크
  - WAN(Wide Area Network): 원거리 네트워크 ➡️ 일반적으로 ISP(Internet Service Provider)라는 인터넷 서비스 업체가 구축하고 관리

- 패킷 교환 네트워크

  - 패킷: 네트워크를 통해 송수신되는 데이터의 단위
  - 페이로드, 헤더, 트레일러로 구성됨

- 주소의 개념과 전송 방식
  - 주소(address): 정보를 올바르게 주고받기 위해 서로를 특정할 수 있는 정보, 패킷에 헤더에 명시되는 정보
  - IP주소와 MAC주소가 있음
  - 유니캐스트(unicast): 송신자-수신자가 일대일로 메시지를 주고받는 전송 방식
  - 브로드캐스트(broadcast): 네튿워크상의 모든 호스트에게 메시지를 전송하는 전송 방식
  - 멀티캐스트(multicast): 네트워크 내의 동일 그룹에 속한 호스트에게만 전송하는 전송 방식
  - 애니캐스트(anycast): 네트워크 내 동일 그룹에 속한 호스트 중 가장 가까운 호스트에게 전송하는 전송 방식

### 2️⃣ 두 호스트가 패킷을 주고받는 과정

- 프로토콜(protocol)
  - 네트워크에서 통신을 주고받는 노드 간의 합의된 규칙이나 방법
  - 프로토콜마다 목적과 특징이 다름
- 네트워크 참조 모델(network reference model)
  - 통신이 이루어지는 단계를 계층적으로 표현한 것
  - 패킷 송신 측: 상위 계층 ➡️ 하위 계층
  - 패킷 수신 측: 하위 계층 ➡️ 상위 계층
  - <img width="574" alt="Image" src="https://github.com/user-attachments/assets/12760c96-e5f0-4555-a974-b778a6a345c4" />
  - OSI 모델
    <img width="230" alt="Image" src="https://github.com/user-attachments/assets/46a82915-b918-47d4-acf7-467163465765" />
    1. 물리 계층(physical layer): 가장 최하위 계층으로 비트 신호를 주고받는 계층/ 유무선 통신 매체를 통해 운반
    2. 데이터 링크 계층(data link layer): 같은 LAN에 속한 호스트끼리 올바르게 정보를 주고받기 위한 계층
    3. 네트워크 계층(network layer): 네트워크 간 통신을 가능하게 하는 계층, IP 프로토콜 사용
    4. 전송 계층(transport layer): 신뢰성있는 전송을 가능하게 하는 계층/ 포트를 통해 특정 응용 프로그램과의 연결 다리 역할을 수행하는 계층/ TCP와 UDP
    5. 세션 계층(session layer): 응용 프로그램 간의 연결 상태인 세션을 관리하기 위한 계층
    6. 표현 계층(representation layer): 인코딩과 압축, 암호화와 같은 작업을 수행하는 계층
    7. 응용 계층(application layer): 사용자와 가장 밀접하게 맞닿아 있어 여러 네트워크 서비스를 제공하는 계층/ HTTP, HTTPS, DNS 등
  - TCP/IP 모델
    - 구현과 프로토콜에 중점을 둔 네트워크 참조 모델
    - <img width="229" alt="Image" src="https://github.com/user-attachments/assets/271b94f3-0acf-44e3-9702-9f09150b54f0" />
- 캡슐화와 역캡슐화
  - 캡슐화(encapsulation): 송신 과정에서 헤더를 추가해 나가는 과정
  - 역캡슐화(decapsulation): 캡슐화 과정에서 붙인 헤더를 각 계층에서 확인한 뒤 제거하는 과정
  - 각 계층마다 패킷을 지칭하는 이름이 다름
    - 나머지: 데이터 or 메시지
    - 전송계층: TCP(세그먼트), UDP(데이터그램)
    - 네트워크: 패킷 or 데이터그램
    - 데이터링크계층: 프레임
    - 물리계층: 심볼 or 비트

### 3️⃣ 네트워크 지도 그리기

<img width="519" alt="Image" src="https://github.com/user-attachments/assets/5e80428c-dafd-4fa8-bd63-055dfb311045" />
