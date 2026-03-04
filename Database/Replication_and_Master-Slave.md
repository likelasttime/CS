### 레플리케이션(Replication)
- 데이터베이스의 데이터를 여러 서버에 복제하여 저장하는 기술
- 원본 데이터를 여러 곳에 복사본으로 보관해서 하나의 서버에 문제가 생겨도 서비스가 중단되지 않도록 한다.

<br>

### Master-Slave
- 가장 일반적인 구조
- Master(Primary)는 쓰기(INSERT, UPDATE, DELETE) 작업을 처리하는 원본 서버
- Slave(Replica)는 Master의 데이터를 복제받아 읽기(SELECT) 작업을 처리하는 복제 서버이며, Master에서 데이터가 변경되면 자동으로 Slave에 동기화된다.
- 성능 향상(읽기 작업을 여러 Slave에 분산시켜 부하를 줄인다.)
- 고가용성(Master 장애 시 Slave를 Master로 승격시켜 서비스를 계속 유지할 수 있다.)
- 백업(복제본이 있어서 데이터 유실 위험이 줄어든다.)
- MySQL, PostgreSQL 같은 RDBMS뿐만 아니라 MongoDB, Redis와 같은 NoSQL에서도 레플리케이션을 지원한다.
- 보통 읽기가 많은 서비스(SNS, 뉴스 사이트 등)에서 Master 1대, Slave 여러 대를 운영하는 방식으로 사용한다.
