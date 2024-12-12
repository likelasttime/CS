### RESTful API
- HTTP 통신을 REST 설계 규칙을 잘 지켜서 개발한 API
- REST(REpresentational State Transfer) 설계 규칙은 1) URI는 정보의 자원만 표현 2) 자원의 상태와 행위는 HTTP Method에 명시

|HTTP Method|특징|
|--|--|
|GET|READ: 정보 요청, URI가 가진 정보를 검색하기 위해 서버에 요청|
|POST|CREATE: 정보 입력, 클라이언트에서 서버로 전달하려는 정보를 보낸다.|
|PUT|UPDATE: 정보 업데이트, 주로 내용을 갱신하기 위해 사용(데이터 전체를 바꿀 때)|
|PATCH|UPDATE: 정보 업데이트, 주로 내용을 갱신하기 위해 사용(데이터 일부만 바꿀 때)|
|DELETE|DELETE: 정보 삭제|

#### 설계 규칙
1. URI는 명사를 사용
2. 슬래시(/)로 계층 관계 표현
3. URI 마지막 문자로 슬래시(/)를 포함하지 않는다.
4. 밑줄(_)을 사용하지 않고, 하이픈(-)을 사용
5. URI는 소문자로만 구성
6. 파일 확장자는 URI에 포함하지 않는다.
