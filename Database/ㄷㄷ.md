### Profiling
- 문제가 되는 병목 지점을 찾고자 사용하는 수단이나 툴
- **slow query**나 문제가 있다고 의심되는 SQL문의 원인을 확인할 수 있다.
- MySQL은 기본적으로 프로파일링 설정값이 비활상화되어있으므로 활성화해준다.
- `show variables like 'profiling%';`
- <img width="486" height="280" alt="image" src="https://github.com/user-attachments/assets/68ef9495-45f1-488d-b2e0-12c9378d9d91" />

- `SET` 키워드로 프로파일링을 활성화 상태로 변경한다.
  - 접속한 세션에 한해서만 적용된다.
  - `set profiling = 'ON';`
  - <img width="1523" height="252" alt="image" src="https://github.com/user-attachments/assets/67e951a6-a341-46f0-95d9-0043b9645e77" />

- 프로파일링을 활성화한 뒤 프로파일링된 쿼리 목록을 확인한다.
  - `show profiles;`
  - <img width="666" height="267" alt="image" src="https://github.com/user-attachments/assets/357517e4-2551-4def-9534-59e51b6524d9" />

- 특정 쿼리 ID에 대해서만 프로파일링된 상세 내용을 확인하려면
  - `show profile for query {쿼리아이디}`
  - <img width="422" height="552" alt="image" src="https://github.com/user-attachments/assets/0936c361-f4b3-45ee-9dd0-32e50922fc27" />

<br>

### 프로파일링 항목
|항목|설명|
|----|-----|
|starting|SQL문 시작|
|checking permissions|필요 권한 확인|
|Opening tables|테이블 열기|
|After opening tables|테이블을 연 이후|
|System lock|시스템 잠금|
|Table lock|테이블 잠금|
|init|초기화|
|optimizing|최적화|
|statistics|통계|
|preparing|준비|
|executing|실행|
|Sending data|데이터 보내기|
|end|끝|
|query end|질의 끝|
|closing tables|테이블 닫기|
|Unlocking tables|잠금 해제 테이블|
|freeing items|항목 해방|
|updating status|상태 업데이트|
|cleaning up|청소|

<br>

### 프로파일링의 선택 가능한 출력정보
- `show profile` 구문 뒤에 해당 키워드를 작성한다.
  
|옵션|설명|
|----|----|
|ALL|모든 정보를 표시|
|BLOCK IO|블록 입력 및 출력 작업의 횟수를 표시|
|CONTEXT SWITCHES|자발적 및 비자발적인 컨텍스트 스위치 수를 표시|
|CPU|사용자 및 시스템 CPU 사용 기간을 표시|
|IPC|보내고 받은 메시지의 수를 표시|
|PAGE FAULTS|주 페이지 오류 및 부 페이지 오류 수를 표시|
|SOURCE|함수가 발생하는 파일 이름과 행 번호와 함께 소스코드의 함수 이름을 표시|
|SWAPS|스왑 카운트 표시|

<br>

### 확장된 프로파일링 항목
<img width="1507" height="567" alt="image" src="https://github.com/user-attachments/assets/c0c9a990-32c5-4ee5-b698-f818de03af0b" />

|항목|설명|
|--------|--------|
|QUERY_ID|Query_ID|
|SEQ|동일한 QUERY_ID를 갖는 행의 표시 순서를 보여주는 일련번호|
|STATE|프로파일링 상태|
|DURATION|명령문이 현재 상태에 있었던 시간(초)|
|CPU_USER|사용자 CPU 사용량(초)|
|CPU_SYSTEM|시스템 CPU 사용량(초)|
|CONTEXT_VOLUNTARY|자발적 컨텍스트 전환의 수|
|CONTEXT_INVOLUNTARY|무의식적인 컨텍스트 전환의 수|
|BLOCK_OPS_IN|블록 입력 조작의 수|
|BLOCK_OPS_OUT|블록 출력 조작의 수|
|MESSAGES_SENT|전송된 통신 수|
|MESSAGES_RECEIVED|수신된 통신 수|
|PAGE_FAULTS_MAJOR|메이저 페이지 폴트의 수|
|PAGE_FAULTS_MINOR|마이너 페이지 폴트의 수|
|SWAPS|스왑 수|
|SOURCE_FUNCTION|프로파일링된 상태로 실행되는 소스 코드의 기능|
|SOURCE_FILE|프로파일링된 상태로 실행된 소스 코드의 파일|
|SOURCE_LINE|프로파일링된 상태로 실행된 소스 코드의 행|
