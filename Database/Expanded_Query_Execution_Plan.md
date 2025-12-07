### MySQL의 확장된 실행 계획
- 기본적인 실행 계획은 `EXPLAIN FORMAT = TRADITIONAL`이다.
  - `EXPLAIN FORMAT = TREE`
- 형식값에 `TREE` 옵션을 입력하면 트리 형태로 추가된 실행 계획 항목을 확인할 수 있다.
  - `EXPLAIN FORMAT = TREE SELECT * FROM {테이블명} WHERE {조건};`
- 형식값에 `JSON` 옵션을 입력하면 `JSON` 형태로 추가된 실행 계획 항목을 확인할 수 있다.
  - `EXPLAIN FORMAT = JSON SELECT * FROM {테이블명} WHERE {조건};`
- 실제 수행된 소요 시간과 비용을 측정하여 실측 실행 계획과 예측 실행 계획 모두를 확인하려면 `EXPLAIN ANALYZE` 키워드를 활용한다.
  - MySQL 8.0.18 이상 버전에서 `SELECT`문 대상으로 수행할 수 있다.
  - `EXPLAIN ANALYZE SELECT * FROM {테이블명} WHERE {조건};`
