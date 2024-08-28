## Garbage Collector
- ***heap*** 영역에서 사용하지 않는 객체들을 제거하는 작업
- 참조되지 않은 객체들을 탐색 후 삭제 ➡️ 삭제된 객체의 메모리 반환 ➡️ ***heap*** 메모리 재사용
- ***GC***의 동작 방식은 가장 간단한 ***Serial GC*** 방식으로 설명할 수 있다.
- ***GC***는 ***Minor GC***, ***Major GC***로 구분할 수 있다.
- ***Minor GC***는 young 영역, ***Major GC***는 old 영역에서 일어난다.
- ***GC***를 수행할 때 ***GC***를 수행하는 스레드 이외의 스레드는 모두 정지한다. 👉 ***stop-the-world***

<br>

## heap 영역 구조
- young: 비교적 젊은 reference가 살아있다.
- eden: 방금 막 생성된 것들이 있다.
- survivor: eden에서 있던 것들이 당분간 생존해 있다.
- old: 특정 횟수 이상을 살아남은 reference가 있다.
- permanent: ***Method Area***의 Meta 정보가 기록되어있다.
![Group 65](https://github.com/user-attachments/assets/5aeab236-bee0-4a64-b7eb-dcd4f44c7712)

<br>

## Mark-Sweep-Compact 알고리즘
- ***Minor GC***는 Eden 영역이 가득 참에서부터 시작한다.
- Eden 영역에서 참조가 남아있는 객체를 mark하고 survivor 영역으로 복사하고, Eden 영역을 비운다.
- Survivor 영역도 가득 차면 같은 방식으로 다른 Survivor 영역에 복사하고 비운다.
- 계속해서 살아남는 객체는 old 영역으로 이동한다.
- ***Major GC***는 old 영역에서 일어난다. 위와 반대로 삭제되어야 하는 객체를 mark하고 지운다.
- 메모리는 단편화된 상태이므로 한군데 모아주는 것은 ***Compaction*** 또는 ***Compact***라고 한다.
- ***Mark-Sweep-Compact 알고리즘***이 중요한 이유는 ***GC*** 수행 시 시스템이 멈추기 때문에 의도치 않은 장애의 원인이 될 수 있다.
- 이를 위해 ***heap*** 영역을 조정하는 것을 ***GC 튜닝***이라고 한다.
- ***JVM*** 메모리는 절대 마음대로 조정하면 안 된다.

<br>

## 📚 참고
https://velog.io/@recordsbeat/Garbage-Collector-%EC%A0%9C%EB%8C%80%EB%A1%9C-%EC%95%8C%EA%B8%B0
