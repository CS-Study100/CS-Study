## 5-3. 네트워크 계층 - IP

### 1️⃣ IP의 목적과 특징

- 주소 지정과 단편화

  - 라우터(router): 전달받은 패킷을 목적기까지 전달하는 역할을 수행
  - 라우팅(routing): 라우터가 IP 패킷을 전달할 최적의 경로를 결정하고 해당 경로로 패킷을 내보내는 과정
  - <img width="426" alt="Image" src="https://github.com/user-attachments/assets/38b05c29-49b5-4bf3-8700-f87b96332a01" />
  - MTU(Maximum Transmission Unit): 최대 전송 단위
  - 단편화: 식별자, 플래그, 단편화 오프셋
    1. 식별자(identifier): 특정 패킷이 어떤 데이터에서 쪼개진 패킷인지 식별하기 위한 용도
    2. 플래그(flag): 3비트 필드
    3. 단편화 오프셋(fragment offset): 특정 패킷이 초기 데이터에서 얼마나 떨어져 있는지 명시된 필드

- 신뢰할 수 없는 통신과 비연결형 통신

  - 신뢰할 수 없는 프로토콜(unreliable protocol): 패킷이 수신지까지 제대로 전송됐다고 보장하지 않는 프로토콜
  - 비연결형 프로토콜(connectionless protocol): 패킷을 주고받기 전에 사전 연결 과정을 거치지 않음

  📍 경로 MTU 발견(Path MTU discovery): 주고받을 수 있는 경로 MTU를 구하고 해당 크기만큼만 송수신하여 IP 단편화를 회피하는 기술

### 2️⃣ IP 주소의 구조

- IP 주소: 네트워크 주소와 호스트 주소
  - 네트워크 주소: 호스트가 속한 네트워크를 특정하기 위해 사용
  - 호스트 주소: 네트워크에 속한 호스트를 특정하기 위해 사용
- 클래스풀 주소 체계

  - 클래스: 네트워크의 크기에 따라 유형별로 IP 주소를 분류하는 기준
    <img width="255" alt="Image" src="https://github.com/user-attachments/assets/1b141703-4d64-43a4-ba75-fa404c698fb2" />

- 클래스리스 주소 체계와 서브넷 마스크
  - 서브넷 마스크(subnet mask): IP 주소상에서 네트워크 주소를 1로 표기하고, 호스트 주소를 0으로 표기한 비트열
  - 서브네트워크(subnetwork): IP 주소에서 네트워크 주소로 구분할 수 있는 네트워크의 부분집합
  - 서브네팅(subnetting): 서브넷 마스크를 이용해 원하는 크기로 클래스를 더 잘게 쪼개어 사용하는 것

### 3️⃣ 공인 IP 주소와 사설 IP 주소

- 공인 IP 주소(public IP address): 전 세계에서 고유한 IP 주소, ISP나 공인 IP 주소 할당 기관을 통해 할당받음
- 사설 IP 주소(private IP address): 사설 네트워크에서 사용하기 위한 IP wnth

### 4️⃣ IP 주소의 할당

- 정적 할당: 직접 수작업으로 IP 주소를 부여하는 방식
- 동적 할당-DHCP: 프로토콜을 통해 자동으로 IP 주소를 부여하는 방식

### 5️⃣ IP 전송 특징의 보완: ICMP

1. 신뢰할 수 있는 연결형 통신을 지원하는 상위 계층의 프로토콜을 이용하는 것
2. 네트워크 계층의 프로토콜인 ICMP를 이용

- ICMP(Internet Control Message Protocol): IP 패킷 전송 과정에 대한 피드백 메시지를 얻기 위해 사용하는 프로토콜
- 전송 과정에서 발생한 오류, 네트워크에 대한 진단 정보

### 6️⃣ IP 주소와 MAC 주소의 대응: ARP

- ARP(Address Resolution Protocol): IP 주소와 MAC 주소를 함께 활용하는 통신 과정에서 동일 네트워크 내에 있는 송수신 대상의 IP 주소를 통해 MAC 주소를 알아내는 프로토콜
- ARP 요청 메시지는 브로드캐스트 메시지
