### JVM(Java Virtual Machine)
- 시스템 메모리를 관리하면서 자바 기반 애플리케이션을 위해 이식 가능한 실행 환경 제공
- JVM은 자바 클래스 로더(Class Loader)와 자바 실행 엔진(Execution Engine)에 의존
- Java 프로그램이 어디에서든 실행될 수 있도록 한다.
- 프로그램 메모리를 관리하고 최적화하는 것

<br>
  
#### JVM 자바 클래스 로더
- 클래스를 메모리에 로드하고 실행을 위해 사용할 수 있게 만드는 JVM의 일부
- 클래스 로딩(Class Loading)을 최대한 효율적으로 수행하기 위해 지연 로딩(Lazy-loading)과 캐싱(Caching) 같은 기법을 활용

<br>

#### JVM 실행 엔진
- 클래스 로더가 클래스를 로딩하는 작업을 마치면, JVM은 각 클래스에 있는 코드를 실행하기 시작
- JVM 실행에 실행 엔진은 필수적이다.
- 파일 시스템 액세스, 네트워크 입출력을 위한 리소스를 관리

<br>

#### Garbage Collector
- Java 프로그램에서 사용되지 않는 메모리를 지속적으로 찾아내서 제거
- 실행 중인 JVM 내부에서 일어난다.

<br>

#### Garbage Collector 종류
- Serial GC
  - GC를 처리하는 스레드가 1개
  - CPU 코어가 1개만 있을 때 사용하는 방식
  - Mark-Compact collection 알고리즘 사용
- Parallel GC
  - GC를 처리하는 스레드가 여러 개
  - Serial GC보다 빠르게 객체를 처리
  - Parallel GC는 메모리가 충분하고 코어의 개수가 많을 때 사용하면 좋음
- Concurrent Mark Sweep GC(CMS GC)
  - stop-the-world 시간이 짧다.
    - stop-the-world는 GC를 실행하기 위해 JVM이 어플리케이션 실행을 멈추는 것
  - 애플리케이션의 응답 시간이 빨라야 할 때 CMS GC를 사용한다.
  - 다른 GC 방식보다 메모리와 CPU를 더 많이 사용
  - Compaction 단계가 제공되지 않는다.
- G1 GC
  - 각 영역을 Region 영역으로 나눈다.
  - GC가 일어날 때, 전체 영역(Eden, Survival, Old generation)을 탐색하지 않는다.
  - stop-the-world 시간이 짧다.
- Stack
  - 정적으로 할당한 메모리 영역
  - 원시 타입의 데이터가 값과 함께 할당, Heap 영역에 생성된 Object 타입의 데이터의 참조 값 할당
- Heap
  - 동적으로 할당한 메모리 영역
  - 모든 Object 타입의 데이터가 할당
  - Heap 영역의 Object를 가리키는 참조 변수가 Stack에 할당

<br>

#### Code 영역(Text Segment)
- 실행할 코드가 저장되는 곳
- 프로그램의 실행 코드(기계어) 저장
- 읽기 전용(Read-Only) - 실행 중 변경 불가
- 프로그램 시작 시 크기 결정
- 여러 프로세스가 같은 코드를 공유 가능

<br>

#### Data 영역
- 전역 변수, 정적 변수가 저장되는 곳
- 초기화된 전역 변수, 정적 변수 초기값이 파일에 저장된다.
- `int glovalVar = 100;  // Data 영역(초기화된 전역 변수)`
- `static int staticVar = 50;  // Data 영역(초기화된 정적 변수)`

<br>

#### BSS 영역(Block Started by Symbol)
- 초기화 안 된 전역 변수, 정적 변수
- 실행 시 자동으로 0으로 초기화
- 파일 크기 절약(초기값 저장 안 함)
- 프로그램 시작 시 할당
- 프로그램 종료 시 해제
- `int unitGlobal;  // BSS 영역(초기화 안 된 전역 변수)`
- `static int unitStatic;  // BSS 영역(초기화 안 된 정적 변수)`

<br>

#### Stack 영역
- 함수 호출 시 지역 변수, 매개변수가 저장되는 곳
- 함수 호출마다 Stack Frame이 생성된다.
- LIFO(Last In First Out) 구조
- 함수 호출 시 자동 할당
- 함수 종료 시 자동 해제(가비지 컬렉션 불필요)
- 빠른 할당 및 해제
- 보통 1 ~ 8MB의 크기 제한이 있다.
- 재귀호출이 많으면 스택 오버플로우 위험이 있다.

<br>

#### Heap 영역
- 동적으로 할당되는 메모리가 저장되는 곳
- 프로그래머가 직접 할당 및 해제
- 런타임에 크기 결정 가능
- 상대적으로 느린 할당 및 해제
- 크기 제한 큼
- 해제를 안 했을 때 메모리 누수 위험
- 가비지 컬렉션 대상이다.

<br>

#### Garbage Collector 실행 과정
1. [Mark] Garbage collector가 Stack의 모든 변수를 스캔하면서 각각 어떤 객체를 참조하고 있는지 찾아서 마킹
2. [Mark] Reachable Object가 참조하고 있는 객체도 찾아서 마킹
3. [Sweep] 마킹되지 않은 객체를 Heap에서 제거
