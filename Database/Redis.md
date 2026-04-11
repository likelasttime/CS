### Redis(Remote Dictionary Server)
- 메모리 기반의 Key-Value 저장소
- 디스크가 아닌 메모리(RAM)에 데이터를 저장하기 때문에 매우 빠르고, 다양한 자료구조를 제공해서 단순 캐시 이상의 역할을 한다.
- Connection Pool을 통해 효율적으로 연결을 관리하고, Replication으로 고가용성을 확보할 수 있다.
- 캐시로 시작했지만, 세션 저장소, 실시간 랭킹, 메시지 큐 등 다양한 용도로 활용할 수 있다.
- 단일 값은 String, 여러 필드가 있는 객체는 Hash 사용
  - `HSET user:1000 name "피카츄" age 30` 개별 필드 수정 가능
- 만료 시간(TTL 설정): 메모리 관리를 위해 캐시는 항상 만료 시간 지정
  - 1시간 후 자동 삭제 `SET chache:product:500 "데이터" EX 3600`
- 원자성(Atomic) 연산: Redis는 모든 명령이 원자적으로 실행돼서 동시성 문제 해결
  - `INCR view:count` 조회수 증가 - Race Condition 없음     

<br>

### 핵심 자료구조
- String
  - 가장 기본적인 자료구조
  - 텍스트, 숫자, JSON 등을 저장
  - 세션 정보 저장(`SET user:1000:session "abc123"`)
  - 조회수 카운팅(`INCR post:100:views`)
  - 간단한 캐싱(`SET product:500 "{json data}" EX 3600`)
- List
  - 순서가 있는 문자열 목록
  - 양쪽 끝에서 push/pop 가능
  - 최근 검색어 기록(`LPUSH user:1000:recent "검색어"`)
  - 실시간 알림 큐(`RPUSH notifications "새 알림"`)
  - SNS 타임라인(최근 게시물 목록)
-  Set
    - 중복되지 않는 문자열 집합
    - 순서 없음
    - 좋아요 누른 사용자 목록(`SADD post:100:likes user:1000`)
    - 중복 방지(이미 처리한 작업 ID 저장)
    - 태그 시스템(`SADD post:100:tags "백엔드" "Redis"`)
- Hash
  - Field-Value 쌍으로 이루어진 객체
  - 자바의 HashMap과 유사
  - 사용자 정보 저장(`HSET user:1000 name "김사랑" age 25`)
  - 상품 상세 정보(`HSET product:500 name "노트북" price 150000`)
  - 설정값 관리
    
-  Sorted Set
    - 각 값에 점수(score)가 있는 집합
    - 점수로 자동 정렬
    - 실시간 랭킹(`ZADD ranking 9500 user:1000`)
    - 우선순위 큐(점수가 우선순위)
    - 일정 관리(타임 스탬프를 점수로 사용)  
