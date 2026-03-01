### CAP 정리
- 일관성(Consistency), 가용성(Availability), 분할 내성(Partition Tolerance)중 최대 두 가지만 동시에 만족할 수 있다.
- 일관성(Consistency)는 모든 노드가 같은 시간에 같은 데이터를 보여야 한다.
- 가용성(Availability)는 모든 요청이 항상 응답을 받을 수 있어야 한다.
- 분할 내성(Partition Tolerance)는 네트워크 장애가 생겨도 시스템이 계속 동작해야 한다.
- 완벽한 네트워크는 없기 때문에 분할 내성은 필수다.
- 일관성과 가용성 중 하나를 선택해야 하는데 MongoDB나 HBase는 CP, Cassandra나 DynamicDB는 AP를 택한다.
- 금융 시스템처럼 정확성이 중요하면 CP, SNS처럼 항상 접속 가능해야 하면 AP를 선택한다.
