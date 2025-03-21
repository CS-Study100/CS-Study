## 2-5. 보조기억장치와 입출력장치

### ✔️ 보조기억장치

- 전원이 꺼져도 데이터를 **안전**하게 보관
- CPU가 필요로 하는 정보를 **빠르게** 메모리에 전달

### ✔️ RAID

데이터의 안전성 또는 성능을 확보하기 위해 여러 개의 독립적인 보조기억장치를 마치 하나의 보조기억장치처럼 사용하는 기술

### 1️⃣ RAID0

데이터를 여러 보조기억장치에 단순하게 나누어 저장하는 방식
(스트라이핑)

- 장점: 빠른 입출력 속도
- 단점: 저장된 정보가 안전하지 않음

### 2️⃣ RAID1

완전한 복사본을 만들어 저장하는 방식 (미러링)

- 장점: 복구 간단, 안전성 높음
- 단점: RAID0보다 속도 느림, 사용 가능한 용량 적어짐

### 3️⃣ RAID4

패리티(오류 검출) 정보를 저장하는 디스크를 따로 두는 방식

- 장점: 적은 디스크로 안전하게 데이터를 보관
- 단점: 패리티 저장 장치에 병목 현상 발생

### 4️⃣ RAID5

패리티를 분산하여 저장하는 방식

- 장점: RAID4의 병목 현상 보완

### 5️⃣ RAID6

서로 다른 2개의 패리티를 두는 방식

- 장점: RAID4/5에 비해 안전성 높음
- 단점: 패리티가 2개이므로 쓰기 속도는 느림

### ✔️ 입출력 기법

- 장치 컨트롤러: CPU와 입출력장치 사이의 통신을 중개
- 장치 드라이버: 장치 컨트롤러의 동작을 읽고 컴퓨터 내부와 정보를 주고 받을 수 있도록 하는 프로그램

### 1️⃣ 프로그램 입출력

프로그램 속 명령어로 입출력 작업을 수행하는 방법

### 2️⃣ 인터럽트 기반 입출력: 다중 인터럽트

인터럽트가 여러 입출력장치로부터 동시에 발생하는 경우

- 프로그래머블 인터럽트 컨트롤러(PIC): 하드웨어 인터럽트 요청의 우선순위를 판별하여 CPU가 지금 처리해야할 하드웨어 인터럽트가 무엇인지 알려주는 장치

### 3️⃣ DMA 입출력

CPU를 거치지 않고 직접 메모리에 접근할 수 있는 입출력 기능

1. CPU가 DMA 컨트롤러에게 입출력 작업 명령
2. DMA 컨트롤러는 CPU 대신 입출력 작업 수행
3. 입출력 작업이 끝난 후 CPU에게 인터럽트를 걸어 작업이 끝났음을 알림

➡️ CPU는 입출력 부담을 줄일 수 있음

- PCIe(Peripheral Component Interconnect express): 입출력 버스
  - 버전에 따라 최대 속도 다름
  - 여러 레인을 이용해 정보를 주고 받음
