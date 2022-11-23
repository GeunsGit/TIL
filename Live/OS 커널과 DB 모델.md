## 세상 모든 OS와 DB
어플리케이션을 구성하는데는 그에 따르는 인프라 필요. 요소에는 어떤 것이 있고 필수적인 OS와 DB의 구성에 대해서 알아보자.

## Learning Goals
1. 인프라에 필요한 구성 요소와 자원들의 형태를 알 수 있다.
2. 현존하는 OS의 커널의 종류와 특징을 알 수 있다.
3. 데이터를 저장하는 방식의 종류와, 그에 대표적인 DB 제품들의 특징들을 알 수 있다.

## OS?!
**Operation System** : 시스템 소프트웨어 관리 컴퓨터 하드웨어, 소프트웨어 자원을 공통 제공 서비스를 위한 컴퓨터 프로그램.
하드웨어와 어플리케이션을 **중재**하는 역할

## Type of OS Kernel
OS 커널
- Monolithic kernel(모놀리식 커널)
  - UNIX, LINUX, MS-DOS, Windows 9x 계열(95, 98, me)
- Micro kernel(마이크로 커널)
  - Minix
- Hybrid kernel(하이브리드 커널)
  - Windows NT 계열, MacOS X 이후 버전
  
## Monolithic kernel(단일형 커널)
IO 입출력 기능, 디바이스 장치 지원 등의 운영체제에서 일어나는 모든 일을 한 개의 커널과 동일한 메모리 공간에 적재하여 커리하는 기법
- 각 기능간의 커뮤니케이션이 좋고, 시스템 호출에 의한 서비스가 빠름.
- 새로운 디바이스 추가나 기능 변경 시는 어려우며, 어느 한 기능에 불량이 생기면 전체를 새로 빌드해야 하는 단점 등이 있음.

### UNIX
HP_UX, ORACLE(SOLARIS), IBM_AIX, FreeBSD, MAC OS X

### Linux Distro (Unix-like)
debian, ubuntu, Linux Mint
Red Hat, CentOS, fedora
slackware, SUSE

## Micro kernel(마이크로 커널)
모놀리지 커널과 반대되는 디자인. 커널에는 핵심적인 디자인, 기본 프로세스 통신 등만을 포함하고 그 외의 것들은 외부 모듈화를 하여 커널의 사이즈가 작아지고, 임베디드 시스템이나 포터블한 디바이스에 사용이 유리
- 리얼타임성 시스템에 강함
- 통신은 메세지 전달을 통해서만 발생하기 때문에 전반적인 퍼포먼스는 저하

## Hybrid kernel(하이브리드 커널)
IPC는 커널에 두고 파일시스템은 유저모드에 디자인

## DATABASE?!
여러 사람이 공유하여 사용할 목적으로 체계화해 통합, 관리하는 데이터의 집합
의미 있게 구조화하여 저장된 정보

## Type of DB model
DB 모델
- Relational
- NoSQL
  - Document Store
  - Key-Value Store
  - Wide Column Store
  - Graph Database
- NewSQL

## Relational Database
- Atomicity, Consistency, Isolation, Durability
- Normalization - 1NF, 2NF, 3NF
- Scalability (Scale-up, not scale out)
- ANSI SQL 문법, JOIN 기능

## Type of NoSQL model
주로 비정형화된 데이터를 저장하기 위한 것으로 특정 스키마가 없음.
어플리케이션의 도움 없이 여러 서버 간의 데이터를 자동으로 분할하고 시스템 메모리에 데이터를 캐시하여 처리량을 높이고 성능 향상.
간단한 데이터 모델과 쿼리로 높은 확장성 제공.
단 일관성보다 가용성을 선호하기 때문에 표준화가 부족하고 데이터 노드 간의 동기화가 되지 않아 시스템 장애의 위험이 있어 은행권 등에서는 쓰이지 않음.
- Auto Balancing
- Integrated Caching
- Lack of schema
- NoSQL
  - Document Store
  - Key-Value Store
  - Wide Column Store
  - Graph Database
  
### Document Type Database
XML이나 JSON을 이용하여 데이터 저장. 스키마가 유동적이어서 레코드가 각각 다른 스키마를 가질 수 있음.
- MongoDB, Couchbase

### Key-Value Type Database
하나의 키에 하나의 값을 갖는 형태, 여러 개의 필드를 가질 수도 있음.
값을 영구히 저장하지는 않으나 휘발성을 이용하여 상태 표현이 필요한 곳에서 사용.
- Redis, Memcached

### Wide Column Type Database
모든 데이터는 로우별로 저장이 되고, 주어진 로우와 컬럼이 함께 저장.
대규모 확장성을 위해 사용. 수집할 수 있는 엄청난 데이터량을 다루는데 적합.
- cassandra, HBASE

### Graph Database
데이터를 노드로 표현. 쿼리 관계는 데이터베이스에 영구적으로 저장하기 때문에 빠름.
퍼포먼스가 좋고 유지보수에 용이한 것이 특징.
- neo4j

## NewSQL
RDB와 NoSQl의 장점을 합친 것. SQL 문법과 트랙잭션 지원. NoSQL처럼 스케일 아웃 지원. 분산 저장 형태의 DB 가능. 수평 분할 가능. 다른 트랜잭션에 영향을 미치지 않음으로서 빠른 성능.
- Partitioning/Sharding
- Concurrency Control
- Replication
- Crash Recovery
- NUODB, Cockroach DB

## DB 사이트
https://db-engines.com/en/ranking

## SUMMARY & QUIZ
1. OS 커널의 종류에는 모놀리식 커널, 마이크로 커널, 하이브리드 커널이 있다.
2. 이것은 OS 중 한 종류로 데니스 리치가 개발하여 현존 OS의 전신이 되고 있는 이 OS의 이름은 유닉스다.
3. DB에서 NoSQL 종류에는 Document 모델 타입, Key-Value 모델 타입, Wide Column 모델 타입, Graph 모델 타입이 있다.
4. 이 DB는 메모리 위에서 실행되는 Key-Value 타입의 DBMS로 가장 대표적으로 SDK가 제공되는 레디스가 있다.
5. 0.1 + 0.2 = 0.3000000004 (부동소수점)
```
Q. NewSQL의 장점이 굉장히 많아보이는데, 대표적인 단점은?
A. 아직 정식화가 되어있지 않음. 전문으로 하는 회사도 많이 없기에 제품도 많이 없음.
```
```
Q. 실시간 통계 보여줘야 하는데 어떤 DB가 가장 좋을지.
A. 저장한다면 RDB, 저장하지 않는다면 REDIS가 좋음.
```
