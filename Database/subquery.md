### 서브쿼리
- 쿼리 안의 보조쿼리
- 가장 바깥쪽의 SELECT문인 main query를 기준으로 내부에 SELECT문을 추가로 작성해서 서브쿼리를 생성한다.
- scalar subquery
  - 메인쿼리의 SELECT절 내부에 하나의 숫자나 문자, 기호 등을 출력하는 SELECT문
  - 출력 데이터와 스칼라 서브쿼리의 결과 건수가 일치해야 한다. 👉 스칼라 서브쿼리의 결괏값은 1행 1열 구조다.
  - max, min, avg, sum, count 등과 같은 집계함수를 자주 사용한다.
  - `SELECT {필드명}, (SELECT COUNT(*) FROM {테이블명} WHERE {조건}) {필드명} FROM {테이블명};`
- inline view
  - 메인쿼리의 FROM절 내부에 작성한 SELECT문
  - FROM절 내부에서 일시적으로 뷰를 생성하는 방식
  - 인라인 뷰의 결과는 내부적으로 메모리 또는디스크에 임시 테이블을 생성하여 활용
  - `SELECT {필드명} FROM (SELECT * FROM {테이블명} WHERE {조건}) {테이블 별칭};`
 
- nested subquery
  - 메인쿼리의 WHERE절 내부에 작성한 SELECT문
  - WHERE절에서 단순한 값을 비교 연산하는 대신 서브쿼리를 추가하여 비교 연산하기 위해 사용한다.
  - `=, <, >, <=, >=, <>, !=`와 같은 비교 연산자와 `IN, EXISTS, NOT IN, NOT EXITS`문을 많이 사용한다.
  - `SELECT * FROM {테이블명} WHERE {필드명} = (SELECT MAX({필드명}) FROM {테이블명});`
