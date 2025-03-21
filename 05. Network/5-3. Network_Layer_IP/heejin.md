# 5-3. 네트워크 계층 - IP

## ✅ IP의 목적과 특징
- **목적**: 
  - **주소 지정**: 네트워크 간 통신에서 호스트를 식별.
  - **단편화**: 데이터를 여러 IP 패킷으로 쪼개어 전송.
- **특징**:
  - **신뢰할 수 없는 통신**: 패킷 유실 시 복구 보장 없음.
  - **비연결형 통신**: 연결 설정 없이 패킷 전송.

---

## ✅ 주소 지정과 단편화
### 주소 지정
- **IP 주소**: 네트워크 간 호스트를 식별하는 주소.
- **IPv4**: 총 4바이트(0~255 범위의 10진수 4개). 예: 192.168.0.1
- **IPv6**: 총 16바이트.
- **MAC 주소**와의 비교:
  - MAC 주소: 택배 수신인/발신인 역할.
  - IP 주소: 택배의 목적지/출발지 주소 역할.

### 라우터와 라우팅
- **라우터**: 다른 네트워크 간 IP 패킷 전달 장비.
- **라우팅**: 최적의 경로를 계산해 IP 패킷을 전달.

### 단편화
- **MTU(Maximum Transmission Unit)**: 데이터 프레임의 최대 전송 크기 (일반적으로 1500바이트).
  - IP 패킷이 MTU보다 크면 단편화하여 전송.
  - 수신지에서 쪼개진 패킷을 재조합.
- IP 패킷 헤더와 단편화 관련 필드:
  - **식별자**: 데이터 출처 식별.
  - **플래그**: 단편화 상태 표시.
  - **단편화 오프셋**: 패킷의 순서 정보.

---

## ✅ 신뢰할 수 없는 통신과 비연결형 통신
- **신뢰할 수 없는 프로토콜**:
  - 패킷 전송 성공 여부를 보장하지 않음.
  - 최선형 전달 방식.
- **비연결형 프로토콜**:
  - 연결 설정 없이 패킷 전송.

### IP 단편화 피하기 - 경로 MTU 발견
- IP 단편화가 잦으면 네트워크 성능 악화.
- 경로 MTU 발견: IP 단편화 없이 전송 가능한 최대 크기 탐색.

---

## ✅ IP 주소의 구조
- **구성**:
  - **네트워크 주소**: 호스트가 속한 네트워크를 식별.
  - **호스트 주소**: 네트워크 내의 특정 호스트 식별.
- **유동적 크기**:
  - 네트워크 주소 크기 > 호스트 주소 크기: 적은 호스트.
  - 네트워크 주소 크기 < 호스트 주소 크기: 많은 호스트.

---

## ✅ 클래스풀 주소 체계
- **클래스 분류**: A, B, C, D, E로 구분.
  - A클래스: 0.x.x.x ~ 127.x.x.x (1옥텟 = 네트워크).
  - B클래스: 128.x.x.x ~ 191.x.x.x (2옥텟 = 네트워크).
  - C클래스: 192.x.x.x ~ 223.x.x.x (3옥텟 = 네트워크).
- **네트워크 주소와 브로드캐스트 주소**:
  - 네트워크 주소: 호스트 비트가 모두 0.
  - 브로드캐스트 주소: 호스트 비트가 모두 1.

### 예약된 주소
- **루프백 주소**: 127.0.0.1 (자기 자신).
- **임시 주소**: 0.0.0.0 ~ 0.255.255.255 (IP 할당 전 임시 사용).

---

## ✅ 클래스리스 주소 체계와 서브넷 마스크
- 클래스풀의 한계를 해결하기 위해 **클래스리스** 등장.
- **서브넷 마스크**:
  - 네트워크 부분 = 1, 호스트 부분 = 0으로 표현.
  - AND 연산을 통해 네트워크 주소 계산 가능.
- **CIDR 표기법**: `IP주소/서브넷 비트 수` (예: 192.168.0.1/24).

---

## ✅ 공인 IP 주소와 사설 IP 주소
- **공인 IP 주소**: 전 세계에서 고유하며, 네트워크 간 통신에 사용.
- **사설 IP 주소**: 내부 네트워크에서만 유효.
  - 라우터를 통해 NAT(Network Address Translation)으로 공인 IP 주소와 연결.

---

## ✅ IP 주소의 할당
### 정적 할당
- 수작업으로 IP 주소 지정.
- **기본 게이트웨이**: 네트워크 외부로 나가는 첫 경로.
- **DNS 주소**: 도메인 이름을 IP 주소로 변환하는 서버 주소.

### 동적 할당: DHCP
- **DHCP 서버**: IP 주소를 동적으로 할당.
  - 임대 기간이 있으며, 자동 갱신 가능.
  - 사용 종료 시 주소 반납.

---

## ✅ IP 전송 특징의 보완: ICMP
- **ICMP(Internet Control Message Protocol)**:
  - IP의 신뢰성 부족을 보완.
  - 오류 제어와 네트워크 진단에 사용.
  - 예: `ping` 명령으로 네트워크 연결 확인.
