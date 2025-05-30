### Tree
- 비선형 자료구조

<br>

|개념|의미|
|----|----|
|Node|트리를 구성하는 요소|
|Edge|노드와 노드를 연결하는 선|
|Root Node|최상위 노드|
|Leaf Node|하위에 다른 노드가 없는 노드|
|Internal Node|Leaf Node를 제외한 모든 노드로 루트 노드를 포함|

<br>

### Binary Tree
- 루트 노드를 중심으로 두 개의 서브 트리로 나뉘어진다.

  
![image](https://github.com/user-attachments/assets/f8af6307-a07a-423e-8b4d-374b005f5b00)





<br>

### Perfect Binary Tree
- 포화 이진 트리
- 모든 레벨이 꽉 찬 이진 트리

<br>

### Complete Binary Tree
- 완전 이진 트리

<br>

### BST(Binary Search Tree)
- 이진 트리의 일종
- 이진 탐색 트리의 노드에 저장된 키는 유일하다.
- 부모의 키가 왼쪽 자식 노드의 키보다 크다.
- 부모의 키가 오른쪽 자식 노드의 키보다 작다.
- 왼쪽과 오른쪽 서브 트리도 이진 탐색 트리다.
- `O(lon n)` 시간 복잡도
- 한쪽으로만 노드가 추가되면, 최악의 경우 `O(n)` 시간 복잡도

<br>

### Red Black Tree
- BST를 기반으로 하는 트리 형식
- BST의 삽입, 삭제 연산 과정에서 발생할 수 있는 문제점을 해결하기 위해 만들어진 자료구조
- 탐색, 삽입, 삭제의 시간 복잡도는 `O(log n)`
- 각 노드는 Red 또는 Black의 색깔을 가진다.
- Root Node는 Black이다.
- 각 Leaf Node는 Black이다.
- 어떤 노드의 색깔이 red라면, 두 자식 노드의 색깔은 Black이다.
- Root Node부터 Leaf Node까지의 모든 경로 중 최소 경로와 최대 경로의 크기 비율은 2보다 크지 않는 balanced 상태다.
