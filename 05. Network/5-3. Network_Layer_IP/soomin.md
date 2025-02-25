# 5-3. 네트워크 계층 - IP
- 물리 계층과 데이터 링크 계층에 속한 기술은 대부분 LAN을 위한 기술
- 같은 LAN에 속한 호스트끼리만 통신을 주고받는 게 아닌, 다른 NW와 통신을 주고 받기 위해 NW 계층 이상의 기술 필요 
## ✅IP의 목적과 특징
- 목적
  - 주소 지정
  - 단편화
- 특징
  - 신뢰할 수 없는 통신
  - 비연결형 통신 
### ▶️ 주소 지정과 단편화
- 주소 지정
  - NW간의 통신 과정에서 호스트를 특징
  - IP 주소를 통해 이루어짐
- 송신지 IP 주소 & 수신지 IP 주소 필드 - IP의 주소 지정과 관련한 필드 
  - IPv4 : 총 4바이트, 0~255 범위의 10진수 4개
    - 하나의 10진수를 옥텟이라고 함 
  - IPv6 :  16 바이트 


- MAC 주소 = 택배의 수신인, 발신인
- IP 주소 = 택배 수신 주소, 발신 주소
- 패킷 송수신 과정에서 MAC 주소보다 IP 주소가 우선적으로 활용 


- 라우터 : 서로 다른 NW에 속한 두 호스트가 NW 간 통신을 수행할 때, IP 주소를 바탕으로 목적지까지 IP 패킷을 전달하는 NW 장비
- 라우팅 : IP 패킷을 전달할 최적의 경로를 결정하고 해당 경로로 패킷 내보내기 


- 단편화
  - 데이터를 여러 IP 패킷으로 올바르게 쪼개기
- MTU : 최대 전송 단위 (일반적으로 1500바이트)
  - 전송하려는 IP 패킷의 크기가 MTU보다 크면 MTU 이하의 여러 패킷으로 쪼개서 전송 
  - 쪼개서 전송된 패킷들을 수신지에서 재조합 
  - 프레임도 최대 데이터의 크기가 1500바이트, MTU는 프레임을 통해 주고받을 수 있는 최대 페이로드 크기라고 봐도 됨 

![](https://velog.velcdn.com/images/laughin/post/8798f53b-35ef-4a94-bfac-67720824398e/image.png)

- IP 패킷 헤더에서 단편화와 관련된 필드 
  - 식별자 : 어떤 데이터에서 쪼개진 패킷인지
  - 플래그 : 미사용 | Don't Fragment | More Fragment
  - 단편화 오프셋 : 초기 데이터에서 얼마나 떨어져 있는가, 패킷의 순서 

### ▶️ 신뢰할 수 없는 통신과 비연결형 통신
- IP의 이런 특징은 전송 계층의 주요 프로토콜인 TCP와 UDP의 존재 목적과도 직결됨 

- 신뢰할 수 없는 프로토콜
  - 패킷이 수신지까지 제대로 전송되었다고 보장하지 않는 프로토콜 
  - 패킷이 유실되거나 목적지에 순서대로 전송되지 않더라도 조치 X
  - 최선형 전달 = 어떠한 보장도 하지 않음
- 비연결형 프로토콜 
  - 패킷을 주고받기 전에 연결 과정을 거치치 X

#### 🔷IP 단편화 피하기 - 경로 MTU 발견
- 잦은 IP 단편화는 NW에 여러 악영향 
- IP 단편화 없이 주고받을 수 있는 최대 크기만큼만 전송 - 경로 MTU
- 주고받을 수 있는 MTU 구하고 해당 크기만큼만 송수신하여 IP 단편화를 피하는 기술 - 경로 MTU 발견

## ✅IP 주소의 구조
- IP 주요 목적인 주소 지정의 수단이 IP 주소
- NW 계층은 IP 주소를 기반으로 LAN 간의 통신 가능
- 네트워크 주소 : 호스트가 속한 NW를 특정하기 위해
- 호스트 주소 : NW에 속한 호스트를 특정하기 위해 
- NW 주소와 호스트 주소 크기가 유동적
- NW 주소 < 호스트 주소 : NW당 많은 호스트에 IP 주소 할당
- NW 주소 > 호스트 주소 : NW당 적은 호스트에 IP 주소 할당

### ▶️클래스풀 주소 체계
- 상황에 따라 NW 주소와 호스트 주소 크기 달라짐 
- IP 주소의 클래스를 통해 적절한 크기를 정함
- 클래스 : NW의 크기에 따라 유형별로 IP 주소를 분류하는 기준 
- 어떤 클래스에 속한 IP 주소인지에 따라 NW 부분과 호스트 부분이 어느 정도의 크긴이지 알 수 있음
- 클래스풀 주소 체계 : 클래스(A,B,C,D,E) 바탕으로 IP 주소를 관리하는 주소 체계


- A클래스 : 0 - 1옥텟 + 3옥텟
- B클래스 : 10 - 2옥텟 + 2옥텟
- C클래스 : 110 - 3옥텟 + 1옥텟
- 첫 옥텟의 주소만 보고도 클래스 파악 가능

#### 🔷네트워크/브로드캐스트 주소와 예약 주소
- 네트워크 주소 - 호스트 주소가 전부 0(0.0)
- 브로드캐스트 주소 - 호스트 주소가 전부 1(255.255)
- 예약된 IP 주소
  - 루프백 주소 - 자기 자신을 가리키는
    - 127.0.0.1 - 로컬호스트
    - 자기 자신을 마치 다른 호스트인 양 간주하여 패킷을 전송
  - '이 네트워크의 이 호스트' 지칭에 사용 : 0.0.0.0 ~ 0.255.255.255
    - 호스트가 IP 주소를 할당받기 전에 임시로 사용하거나 마땅히 자신을 지칭할 IP 주소가 없을 때 사용

### ▶️클래스리즈 주소 체계와 서브넷 마스크 
- 클래스풀 주소 체계는 클래스별 NW 크기가 고정되어 있음
- 고정된 크기 이외에 다른 크기의 NW를 구성할 수 없어 IP 주소가 낭비 될 수 있음
- 이를 해결하기 위해 더 정교하고 유동적인 클래스리스 주소 체계 사용


- 클래스리즈 주소 체계
  - 서브넷 마스크 : IP 주소상에서 NW 주소 - 1, 호스트 주소 - 0
    - 서브넷을 구분하는 비트열 
  - 서브네트워크(서브넷) : NW의 부분집합
  - 서브네팅 : 서브넷 마스크를 이용해 원하는 크기로 클래스를 더 잘게 쪼개어 사용
  
- **서브넷 마스크**와 **IP 주소** 간에 비트 AND 연산 수행 ⇒ IP 주소 내의 **NW 주소**를 알아낼 수 있음 

#### 🔷CIDR 표기 - 서브넷 마스크 표기법
- CIDR 표기법 : IP 주소/서브넷 마크상의 1의 개수 

## ✅공인 IP 주소와 사설 IP 주소
- 호스트의 IP 주소 확인
  - 명령어 : `ifconfig`
  - 온라인 검색
- 고유한 IP 주소 - 공인 IP 주소
- 고유하지 않은 IP 주소 - 사설 IP 주소
- 공인 IP 주소
  - 전 세계에서 고유한 IP 주소
  - NW 간 통신에서 사용 
  - ISP나 공인 IP 주소 할당 기관을 통해 할당 
- 사설 IP 주소
  - 사설 NW에서 사용하기 위한 IP 주소, 사설 NW상에서만 유효
  - 외부 NW에 공개되지 않은 NW
  - 라우터를 통해 할당
  - 라우터를 중심으로 구성된 LAN 대부분은 사설 NW에 해당
  
## ✅IP 주소의 할당
### ▶️정적 할당
- 수작업으로 IP 주소를 부여하는 방식 
- 게이트웨이 : 서로 다른 NW를 연결하는 하드웨어적/소프트웨어적 수단
- 기본 게이트웨이 : 호스트가 속한 NW의 외부로 나가기위한 첫 기본 경로
  - NW 외부와 연결된 라우터의 주소를 의미 
- IP 할당의 맥락에서 사용되는 게이트웨이라는 용어는 기본 게이트웨를 의미 
- DNS 주소 : 호스트가 도메인 네임을 토대로 IP 주소를 알아내기 위해 질의하는 서버의 주소
  - 도메인 네임 : 기억할 수 있는 문자열로 호스트 식별
  - 호스트가 도메인 네임에 해당하는 IP 주소를 알아내기 위해 <도메인 네임, IP 주소> 쌍을 저장하는 서버에 질의 - 이 서버가 DNS 서버 

### ▶️동적 할당: DHCP
- 프로토콜(DHCP)을 통해 자동으로 IP 주소를 부여
- 호스트는 DHCP 서버와 메시지를 주고받으며 동적 IP 주소를 할당받음
- DHCP 서버는 호스트에 할당 가능한 IP 주소 목록을 관리하다가, IP 주소 할당 요청을 받았을 때 IP 주소를 할당해 주는 호스트 
- 일반적으로 라우터가 DHCP 서버 역할을 수행


1. 동적 IP 주소에는 사용 가능한 기간(임대 기간)이 정해져 있다. 
   - 사용되지 않을 경우 회수, 사용 기간 끝나면 DHCP 서버로 반납
   - 임대 갱신 가능 - 자동으로 두 차례 수행, 모두 실패시 반납
2. 동적 IP 주소는 할당받을 때마다 다른 주소를 받을 수 있다.

## ✅IP 전송 특징의 보완: ICMP
- 신뢰X, 비연결형이 나쁠까? X
  - 성능에는 좋음 
  - 오류 제어와 연결 수립 및 관리는 패킷의 빠른 송수신과 배치되는 작업 
- 그럼에도 보완해야 할 때가 있음 
- 보완 방법 2가지
  1. 신뢰할 수 있는 연결형 통신을 지원하는 상위 계층의 프로토콜 이용 - TCP
  2. 네트워크 계층의 프로토콜로 ICMP 이용 


- Internet Control Message Protocol : IP 패킷의 전송 과정에 대한 피드백 메시지를 얻기 위해 사용하는 프로토콜 
  - ICMP 메시지를 통해 IP 전송의 결과 엿보기 가능 
  
- ICMP 유형
  1️⃣전송 과정에서 발생한 오류 보고
  - NW 도달 불가
  - 단편화가 필요하지만 DF가 1로 설정되어 단편화할 수 없음
  - TTL(패킷 수명) 만료
    - 홉 : 패킷이 호스트 혹은 라우터에 한 번 전달
    - TTL 필드의 값은 홉마다 1씩 감소
    - TTL을 통해 무의미한 패킷이 NW상에 지속적으로 남아있는 것을 방지 
   
  2️⃣네트워크에 대한 진단 정보 
  - `traceroute` : nw 상의 경로 확인
  - `ping` : nw 상태를 점검하기 위한 패킷 송신 명령어 
  
## ✅IP 주소와 MAC 주소의 대응: ARP
- 택배 발송에 송수신인, 송수신 주소 모두 사용하되, 주소를 우선적으로 활용
- 패킷 송수신에 MAC주소, IP주소 모두 사용하되, IP 주소를 우선적으로 활용
- ARP 프로토콜 : IP 주소와 MAC 주소를 함께 활용하는 통신 과정에서 동일 NW 내에 있는 송수신 대상의 IP 주소를 통해 MAC 주소를 알아내는 프로토콜 
  - 상대 호스트의 IP 주소는 알고, MAC 주소는 모름 
- 동작 과정
  - ARP 요청 - 브로드캐스트 메시지
    - NW 내에 있는 모든 호스트에게 보내는 메시지 
      - 호스트가 메시지의 IP 주소를 확인해서 관련 없으면 무시, 자기꺼면 응답
    - 이 IP를 가진 호스트와 통신하고 싶은데, 이 호스트의 MAC 주소는 뭐야?
  - ARP 응답 메시지 
    - 응답 메시지를 보내는 호스트의 MAC 주소 포함
- ARP 테이블 : 호스트는 알게된 <IP 주소, MAC 주소> 쌍을 기억해 둠
   - 항목들은 일정 시간이 지나면 삭제되고, 임의로 삭제 가능 
   - 확인 명령어 : `arp -a` 
   
> 사진 출처: 강민철, ⌜이것이 취업을 위한 컴퓨터 과학이다⌟, 한빛미디어, 2024
