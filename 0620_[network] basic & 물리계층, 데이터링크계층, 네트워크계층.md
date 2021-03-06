# Basic

## 패킷

네트워크 통신을 할 때 사용되는 작게 분할된 데이터 조각으로, 네트워크에서 전송하는 데이터의 기본 단위



## DMZ(Demilitarized Zone)

네트워크 구성 중 일반적으로 인터넷인 외부 네트워크와 내부 네트워크 사이에 위치한 중간 지대(서브넷)

네트워크의 보안 영역으로 외부 공격자가 내부 네트워크에 침투하는 것을 막는 역할을 한다.



## 프로토콜

통신을 하기 위한 규칙



## OSI 7계층과 TCP/IP 4계층

데이터를 주고받기 위한 통신 규격

### OSI 7계층

ISO 라는 국제표준화기구가 제정

- `응용계층 - 표현계층 - 세션계층` - `전송계층` - `네트워크 계층` - `데이터 링크 계층 - 물리 계층`

### TCP/IP 모델

- `응용계층` - `전송계층` - `인터넷계층` - `네트워크 접속 계층`



## 캡슐화와 역캡슐화

데이터 송신 -> 요청데이터에 계층별로 `헤더`를 하나씩 붙인다 -> 수신측 도착하면 헤더를 하나씩 뗀다

송신 측의 데이터 링크 계층에서 만들어진 데이터가 전기 신호로 변환되어 수신 측에 전송된다.



## VPN(Virtual Private Network 가상 사설망)

가상 통신 터널을 만들어 기업 본사나 지사와 같은 거점 간을 연결하여 통신하거나 외부에서 인터넷으로 사내에 접속한다.





# 1. 물리계층

데이터(0과 1의 비트열) => 전기 신호(디지털 신호 또는 아날로그 신호) => 데이터(0과 1의 비트열)



### 랜 카드

- 컴퓨터의 네트워크 연결 및 데이터 전송 담당

- 비트열을 전기  신호로 변환



### 허브

- 랜을 구성할 때, 여러 개의 포트로 가까운 거리 장비를 케이블을 사용하여 연결하는 장치

- 전기 신호를 정형하고 증폭하는 기능

- 단, 전기 신호를 모든 포트로 보내기 때문에 더미허브라고도 불린다.



# 2. 데이터 링크 계층

네트워크 '내'에서  기기 간에 데이터를 전송하고 물리주소(MAC) 을 결정

**이더넷 규칙을 기반으로 같은 네트워크 내에서 네이터를 전송한다.**



### 이더넷

- 랜에서 데이터를 정상적으로 주고받기 위한 규칙



### CSMA/CD 방식

- 이더넷에서 데이터 충돌을 막기 위한 규칙



### MAC주소

- 랜카드에 정해진 주소(컴퓨터당 1개!)



### 이더넷 헤더

- 목적지 MAC 주소 + 출발지 MAC 주소 + 유형(프로토콜 식별)



### 프레임

- 이더넷 헤더와 트레일러가 추가된 데이터



### 스위치, MAC 주소 테이블

- `MAC 주소 테이블`에 `포트번호`와 해당 포트에 연결된 컴퓨터의 `MAC 주소`를 등록
- 스위치에서 MAC 주소를 기준으로 출발지를 선택하는 것을 `MAC 주소 필터링`이라 한다.



# 3. 네트워크 계층

**IP 주소를 통해 서로 다른 네트워크 간 데이터를 전송한다.**



### 라우팅 테이블

- 경로 정보를 등록하고 관리



### IP주소

- 어떤 네트워크의 어떤 컴퓨터인지 구분할 수 있는 주소



### 라우팅

- 어떤 경로로 데이터를 보낼지 결정하는 것

### IP 프로토콜, IP 헤더,  IP 패킷

- 네트워크 계층의 프로토콜로, 네트워크 계층에서 캡슐화할 때 IP 헤더를 붙인다.

- 이렇게 IP 헤더가 붙은 데이터를 IP 패킷이라 한다.



### 공인 및 사설 IP 주소

- 인터넷 서비스 공급자(ISP)가 제공하는 공인 IP 주소 -> 라우터에 할당
- 랜 내의 컴퓨터는 라우터 DHCP 기능을 사용하여 자동으로 사설 IP 할당



### IP 주소

- 2진수 32bit(IPv4)
- 11000000 10101000 00000001 00001010 => 192.168.1.10
- 네트워크 ID(어떤 네트워크인가) 와 호스트 ID(해당 네트워크의 어느 컴퓨터인가)로 구성



### IP 주소 종류: 클래스

- A: 대규모
- B: 중형
- C: 소규모



### 네트워크 주소와 브로드캐스트 주소(자신의 IP로 설정불가)

- 네트워크 주소 : 호스트 ID가 10진수 0인 주소 => 작은 네트워크를 식별하는 네트워크 대표 주소
- 브로드캐스트 주소 : 호스트 ID가 10진수 255인 주소 => 네트워크의 모든 장비에 한 번에 데이터를 전송하는 주소



### 서브넷, 서브네팅

- A클래스의 대규모 네트워크를 작은 네트워크로 분할하여 브로드캐스트로 전송되는 패킷의 범위를 좁히는 것
- 서브네팅 : 네트워크를 분할하는 것
- 서브넷 : 분할된 네트워크
- `네트워크 ID` + `호스트 ID` => `네트워크 ID` + `서브넷 ID` + `호스트 ID`
- 서브넷 ID를 호스트 ID에서 빌린다. 



### 서브넷 마스크

- 네트워크 ID와 호스트 ID를 식별하기 위한 값
- A 클래스 : 255.0.0.0 / B : 255.255.0.0 / C : 255.255.255.0 
- 프리픽스 표기법 /28 => 네트워크 ID가 28bit(C클래스의 네트워크 ID를 기본 24에서 28로 변경시)



### 라우터

- 기본 게이트웨이 주소(ex, 192.168.1.1) IP 할당
- A 네트워크의 컴퓨터 1에서 기본 게이트웨이를 설정, A네트워크 라우터로 보낸다.
- 이후 라우팅 테이블에 적힌 경로 정보를 보고 전송한다.



### 라우팅 테이블

- 경로 정보가 등록되어 있는 테이블



### 라우팅 프로토콜

- 라우터 간에 라우팅 정보를 서로 교환하기 위한 프로토콜