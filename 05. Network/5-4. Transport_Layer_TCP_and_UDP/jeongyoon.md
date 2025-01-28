## 5-4. 전송 계층 - TCP와 UDP

### 1️⃣ TCP와 UDP의 목적과 특징

- 포트를 통한 프로세스 식별
  - 포트 번호: 네트워크 상에서 호스트가 실행하는 프로세스를 식별하는 번호
  - <IP 주소: 포트번호> 형식
  - <img width="569" alt="Image" src="https://github.com/user-attachments/assets/1de6b21b-85a4-4ad4-a2d1-23bad579b710" />
- (비)신뢰성과 (비)연결형 보장
  - 패킷의 유실 없는 송수신 ➡️ TCP
  - 빠른 송수신 ➡️ UDP
  - 순서 번호(sequence number): TCP 패킷의 올바른 송수신 순서를 보장하기 위해 세그먼트 첫 바이트에 매겨진 번호
  - 확인 응답 번호(acknowledgement number): 상대 호스트가 보낸 세그먼트에 대한 응답, 다음으로 수신하길 기대하는 순서 번호
  - 제어 비트(control bit): 현재 세그먼트에 대한 부가 정보를 나타내는 정보
    - ACK, SYN, FIN

### 2️⃣ TCP의 연결부터 종료까지

three-way handshake 수행

1. 송신자 SYN 세그먼트 전송
2. 수신자 SYN + ACK 세그먼트 전송
3. 송신자 ACK 세그먼트 전송
   <img width="357" alt="Image" src="https://github.com/user-attachments/assets/2ec254ec-1644-4d10-8502-aed22feec289" />

- TCP의 오류, 흐름, 혼잡 제어

1. 재전송을 통한 오류 제어
   - 중복된 ACK 세그먼트가 도착하거나, 타임아웃이 발생했을 때
2. 흐름 제어
   - 송신 호스트가 수신 호스트의 처리 속도를 고려하여 송수신 속도를 균일하게 맞추는 기능
3. 혼잡 제어
   - 송신 호스트가 주체적으로 얼마나 네트워크가 혼잡한지를 판단하여 세그먼트의 전송량을 조절하는 것
   - 혼잡 제어 알고리즘(AIMD): AIMD는 세그먼트를 보내고 그 응답이 오기까지 혼잡이 감지되지 않으면 혼잡 윈도우를 1씩 선형적으로 증가, 혼잡이 감지되면 혼잡 윈도우를 절반으로 떨어뜨림

- TCP의 종료

1. 송신자 FIN 세그먼트
2. 수신자 ACK 세그먼트
3. 수신자 FIN 세그먼트
4. 송신자 ACK 세그먼트
   <img width="384" alt="Image" src="https://github.com/user-attachments/assets/527e0a9e-2f36-4d43-8b98-c943bbb74d1a" />

### 3️⃣ TCP의 상태 관리

TCP는 상태를 유지하고 관리하는 프로토콜

1. 연결이 수립되지 않았을 때 주로 활용되는 상태
2. 연결 수립 과정에서 주로 활용되는 상태
3. 연결 종료 과정에서 주로 활용되는 상태
