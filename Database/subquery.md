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

<br>

### 메인쿼리와 서브쿼리의 관계에 따른 SQL 용어
|non correlated subquery|correlated subquery |
|---|---|
|비상관 서브쿼리 <br> |상관 서브쿼리 <br>|
메인쿼리와 서브쿼리 간에 관계성이 없다. <br>| 메인쿼리와 서브쿼리 간에 관계성이 있다. <br>|
서브쿼리가 독자적으로 실행된 뒤 메인쿼리에게 그 결과를 던져준다. <br>|SELECT 절에 작성하는 스칼라 서브쿼리와 WHERE절에 작성하는 중첩 서브쿼리일 때 발생한다. <br> 메인쿼리에서 데이터를 전달받은 뒤 서브쿼리가 수행되고, 그 결과를 다시 메인쿼리로 전달한다. <br>|
`SELECT * FROM {테이블} WHERE {필드} IN (SELECT {필드} FROM {테이블} WHERE {조건});` |`SELECT * FROM {테이블} WHERE {필드} IN (SELECT {필드} FROM {테이블} WHERE {조건});` <br> |

<br>

### 반환 결과에 따른 SQL 용어
|single-row subquery|multiple-row-subquery|multiple-column subquery|
|---|---|--|
|서브쿼리 결과가 1건의 행으로 반환되는 쿼리 <br> 메인쿼리의 조건절에서는 `=, <, >`등의 연산자와 비교한다. <br> SELECT절에서 사용하는 스칼라 서브쿼리와 동일하다.|서브쿼리 결과가 여러 건의 행으로 반환되는 쿼리다. <br> 메인쿼리의 조건절에서는 IN 구문으로 서브쿼리에서 반환되는 값들을 받는다.|서브쿼리 결과가 여러 개의 열과 행으로 반환된다. <br> 메인쿼리의 조건절에서는 IN 구문과 함께 서브쿼리에서 반환될 열들을 동일하게 나열해 서브쿼리 결과를 받는다.|
