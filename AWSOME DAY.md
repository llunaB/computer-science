# AWSOME DAY

# Cloud

### 클라우딩 컴퓨팅을 사용한다는 것

인프라를 하드웨어가 아닌 소프트웨어로 간주하고 사용한다는 것.

리소스에 액세스하여, DB 처리량 및 컴퓨팅 파워를 늘릴 수 있어서 비즈니스를 유연하고 민첩하게 관리.

사용한 만큼 지불하므로 비용 효율적.



### 장점

- 자본 비용을 가변비용으로 대체
- 규모의 경제로 얻게되는 이점 : 개별 인프라 소유비용 절감
- 용량 추정 불필요
- 속도 및 대응력 향상
- 데이터센터 운영 및 유지관리 비용투자 불필요
- 글로벌 인프라로 몇 분 만에 전 세계에 배포



### 클라우드 배포 모델

1. 온프레미스(프라이빗)
2. 하이브리드 : 기존 온프레미스 데이터센터와 클라우드를 함께 운영
3. 클라우드



### 리전과 가용영역

- 리전 : 서비스를 하는 지리적인 위치
- 가용영역 : 데이터센터의 클러스터(AZ), 하나의 리전은 최소 2개의 가용영역으로 구성. 실제 데이터센터인 가용영역의 위치는 비공개.
- 하나의 리전은 2개 이상의 가용 영역으로 구성되어있다. 하나의 가용영역에서 문제가 발생하면 다른 하나가 있다.



### 리전 선택기준

- 데이터 커버넌스
- 지연시간 to 엔드유저
- 비용



### 짧은 지연시간이 필요하다면 엣지인프라 사용

- 클라우드를 엔드포인트에 더 가까지 위치시킨다.



### 상호작용 방법

- AWS Management Console
- 명령줄 인터페이스 AWS CLI : cmd
- 소프트웨어 개발 키트 SDK : Rest API 로 구성, 다양한 언어로 코딩(Java, Python)

**=> 코드형 인프라(IaC) 로써 관리, 인프라를 고정된 하드웨어가 아닌 코드로 관리한다.**



## EC2: Elastic Compute Cloud

- 온프레미스의 경우, (물리서버) 트래픽, 부하 변화에 탄력적으로 반응못해 오버프로비져닝
- 가상머신 활용시 리소스를 효율적으로 사용
- EC2 인스턴스는 일회용 리소스이므로 프로비저닝하고 데이터 등 모든 정보는 외부에 저장해서 EC2 인스턴스를 일종의 Stateless하게 관리할 수 있다.
- Stateless하게 관리하면 EC2 인스턴스는 기능만 하게 되므로 인프라를 탄력적으로 확장 및 축소할 수 있다.
- 또한 EC2 인스턴스 부하를 CloudWatch 라는 모니터링 서비스로 모니터링 하고 데이터를 기반으로 인스턴스를 확장하거나 Scale Up, Scale Down, Scale Out, Scale In 을 할 수 있도록 결정할 수 있다.



예를 들어 MongoDB를 새로 도입할 경우 PoC를 위해 새 장비를 구매할 필요 없이 

추가 리소스를 프로비저닝하고, 해당 작업이 끝나면 리소스를 삭제하면 된다.

즉, 신기술 도입이나 아키텍쳐 변경 등 다양한 환경을 테스트해볼 수 있다.



### 비용, 오토스케일링

탄력적으로 실행과 종료가 가능하므로, 효율적으로 컴퓨팅 자원 사용

오토스케일링 활용시 트래픽이 몰리는 상황에서 증가, 필요하지 않으면 중단



### 오케스트레이션 서비스 : AWS AECS

- 쿠버네티스
- AWS Amazon Elastic Container Service 



### 서버리스 컴퓨팅 : AWS Lambda

서버를 관리하지 않고 애플리케이션과 서비스를 구축하고 실행한다.

- 프로비저닝하거나 관리할 서버 없다.
- 유휴 상태에 대한 비용 지불 없다. 트래픽이 없으면 비용을 청구하지 않는다.

=> 서버 또는 런타임의 관리 및 운영에 신경을 쓰는 대신 핵심 제품에 집중할 수 있다.

=> 오버헤드가 줄어들고 개발자는 제품 개발에 집중할 수 있다.

#### Lambda

- 완전 관리형 컴퓨팅 서비스로 코드만 쓰면 된다.
- 상태 비저장으로 코드를 실행한다. 람다 실행시에만 코드가 실행된다.
- 일정에 따라 또는 이벤트에 대한 응답으로 코드를 실행한다.





# Storage

### Amazon S3

- 객체 수준의 스토리지 `키-밸류` 고유 객체키 할당 => 신속한 검색
- 100%에 가까운 내구성 - 백업과 아카이브 용으로 사용가능
- 높은 수평 확장성으로 다수의 동시 트랜잭션이 가능 -> 금융 거래 분석, 클릭스트림 분석 등의 워크로드를 지원하는 빅데이터 분석용 스토리지로 유용
- 이벤트 알림기능이 있어 사용자에게 전송 또는 람다 등으로 연동가능
- 버킷에 저장할 수 있는 **객체 수에 제한이 없다.**
- 웹 어디서나 언제등 데이터 저장 및 검색이 가능하다.



### Amazon S3 Glacier

- 아카이브 및 백업 : cctv 영상, 탈퇴 유저의 정보 5년간 보호 등 오랜 기간 저렴하게 저장



### Amazon Elastic Block Store(Amazon EBS)

- 인스턴스용 영구 블록 스토리지
- 백업 및 복구를 위한 볼륨 스냅샷 생성으로 데이터 보호
- 트랜잭션 워크로드를 위한 SSD 지원 스토리지, 처리량 워크로드를 위한 HDD 지원 스토리지



#  Database

- Relational
- Key-value
- In-memory
- Document
- Wide-Column
- Graph
- Ledger
- Time Series



서버 프로비저닝, 보안패치 작업, 구성 백업 등 DB 관리 태스크 필요없음.

예비 DB 설치 관리 필요없이 원클릭으로 동기화 다중 AZ 배포 가능. 즉, DB 이중화 빠르게 할 수 있다.

백업 및 특정 시점으로 DB 복구 작업도 신경 쓸 필요 없음



### Amazon RDS

클라우드에서 관계형 데이터베이스를 설정 운영 조정한다.

여러 데이터베이스 인스턴스 유형으로 제공한다.

- SQL Server, Amazon Aurora, MaraDB, Orable, MySQL, PostgreSQL



DB 가동을 중단하지 않고 DB 컴퓨팅 및 스토리지 리소스 확장 가능하다.

다중 AZ, 가용 영역을 사용해서 DB 인스턴스를 여러 대 프로비저닝하여 DB 이중화를 손쉽게 할 수 있다.



### Dynamo DB

- NoSQL 워크로드 배포용 서비스
- 빠른 지연속도



# Network

### Amazon Virtual Private Cloud(VPC)

AWS 클라우드의 프라이빗 네트워크 공간이다.

IP주소의 범위선택, 서브넷 생성, 라우팅 테이블 및 인터넷 게이트웨이 구성 등 가상 네트워킹 환경을 제어한다.

워크로드의 논리적 격리를 제공한다.(개발과 테스트)



### Elastic Load Balancing

수신되는 애플리케이션 트래픽을 여러 Amazon EC2 인스턴스, 컨테이너, IP 주소에 분산하는 관리형 로드밸런싱 서비스



### Amazon Route 53

클라우드 Domain Name System

도메인 이름을 IP 주소로 변환한다.

지역기반 라우팅 가능



### 전체 요약

1. 사용자가 `DNS` 통해 어플리케이션에 접근
2. Route53 이 이를 `IP` 정보로 변경하여 전달
3. 전달받은 IP 정보로 트래픽을 요청
4. AWS 클라우드의 `VPC`에 연결된 `인터넷 게이트웨이` 서비스가 이를 처리
5. 트래픽은 라우팅 테이블의 트래픽 경로를 따라 `ELB`로 연결
6. `ELB` 는 뒤에 연결된 EC2 인스턴스에 적절히 부하를 분산한다.



# Security

### 모든 데이터는 데이터 계층에서 자동으로 암호화

### 고객 책임

- 플랫폼 애플리케이션 자격증명 및 액세스 관리
- 방화벽 구성
- 클라이언트측 데이터 암호화
- 서버 측 암호화(파일시스템 및 데이터)
- 네트워크 트래픽 보호



### IAM

정책을 사용자, 그룹, 역할에 연결한다.

- 사용자 : AWS 계정 `내` 의 사용자. 각 사용자는 자체 자격증명을 보유한다. 인증만 되고 서비스 권한은 따로 설정해야한다. 정책을 연결해야 한다.
- 그룹 : 동일한 권한을 가진 사용자 모음
- 역할



### IAM 정책 유형

- 자격증명 기반(사용자, 그룹, 역할)
- 리소스 기반(S3와 같이 리소스 자체에서 권한을 부여)



### S3 버킷 액세스 정책 예시 : EC2에서 S3 버킷의 객체를 조회하기

- EC2 인스턴스에 IAM 역할이 없다. 그래서 SSH에서 버킷 객체 조회하면 수행이 안된다.

- IAM 대시보드에서 Role을 생성한다.

- 신뢰하는 개체로 EC2를 선택한다.

- Role 에 정책(버킷 객체를 조회)을 연결해서 권한을 부여한다.

- 역할을 생성한다.

- 역할을 EC2 인스턴스에 연결한다. (Security-Modify IAM Role)



### AWS CloudTrail

- AWS 계정의 로그를 저장



### AWS Trusted Advisor

- 비용 절감, 성능 개선, 보안강화에 도움이 되는 지침을 제공