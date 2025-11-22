### 세그먼트 트리
- 배열의 특정 구간에 대한 연산을 매우 빠르게 처리할 수 있는 자료구조
- 구간 쿼리와 값 변경 쿼리 문제를 효율적으로 해결한다.
- 구간 합, 최솟값/최댓값 등의 구간 연산에 대해 매우 높은 처리속도로 구할 수 있다.
- 결합, 교환법칙이 성립하는 연산에 대해서도 세그먼트 트리를 적용할 수 있다.
- 전체 배열의 정보를 트리 형태로 저장하고, 각 노드는 특정 구간의 연산 결과를 담는다.
  - Root Node: 배열 전체 구간에 대한 정보
  - Child Nodes: 부모 노드가 담당하는 구간을 절반으로 나누어 각각의 정보를 담는다.
    - 만약에 루트가 0 ~ 7 구간이면, 왼쪽 자식은 0 ~ 3 구간, 오른쪽 자식은 4 ~ 7 구간
  - Leaf Node: 배열의 원소 하나하나에 대한 정보를 담는다.
- 시간 복잡도
  - 빌드 시간 복잡도: 모든 노드를 한 번씩 방문하므로 `O(N)`
    - ```java
        private T build(int root, int l, int r) {
          if (l == r) {
            return tree[root] = a[l];
          } else {
            T left = build(root * 2, l, (l + r) / 2);
            T right = build(root * 2 + 1, ((l + r) / 2) + 1, r);
            return tree[root] = function.apply(left, right);
          }
        }
  - 쿼리 시간 복잡도: 트리의 높이만큼 탐색하므로 `O(logN)`
    - ```java
        public T query(int l, int r) {
          return query(1, 0, a.length - 1, l, r);
        }

        private T query(int root, int l, int r, int lq, int rq) {
          if (rq < l || lq > r) return null;
          if (l == r) return tree[root];
          if (lq <= l && rq >= r  ) return tree[root];
          int mid = (l + r) / 2;
          T leftResult = query(root * 2, l, mid, lq, rq);
          T rightResult = query(root * 2 + 1, mid + 1, r, lq, rq);
          return function.apply(leftResult, rightResult);
        }
      ```
  - 업데이트 시간 복잡도: 트리의 높이만큼 갱신하므로 `O(logN)`
    - ```java
        public void update(int pos, T x) {
          a[pos] = x;
          update(pos, 1, 0, a.length - 1);
        }

        private T update(int pos, int root, int left, int right) {
            if (pos < left || pos > right) {
                return tree[root];
            } else if (left == right) {
                return tree[root] = a[pos];
            } else {
                int mid = (left + right) / 2;
                T leftResult = update(pos, 2 * root, left, mid);
                T rightResult = update(pos, 2 * root + 1, mid + 1, right);
                tree[root] = function.apply(leftResult, rightResult);
                return tree[root];
            }
        }
      ``` 
- 공간 복잡도: 트리 배열 크기 `4N`은 상수로 취급해서 `O(N)`       




<br>

### 동적 세그먼트 트리
- 메모리를 사용하는 방식이 세그먼트 트리와 차이가 있는 자료 구조
- 쿼리나 업데이트 시 필요한 노드만 동적으로 생성
- 전체 구간의 크기가 매우 크더라도 실제 사용하는 데이터의 개수가 적다면 효율적으로 메모리를 사용 가능

<br>

### 세그먼트 트리와 동적 세그먼트 트리 비교
|구분|일반 세그먼트 트리|동적 세그먼트 트리|
|----|-----------------|-----------------|
|메모리 복잡도|`O(N)`(N = 최대 좌표)|`O(QlogN)` (Q = 쿼리 수)|
|주요 사용처|좌표 범위가 작고 데이터가 조밀할 때|좌표 범위가 매우 크고 데이터가 희소할 때|
|구현 방식|배열(인덱스 계산)|포인터(동적 할당)|
|속도(연산)|`O(logN)`|`O(logN)`(상수 시간은 포인터 접근이 약간 더 느릴 수 있다)|
|장점| 구현이 비교적 간단하고 빠름|메모리를 극도로 효율적으로 사용, 좌표 압축이 불필요|
|단점|큰 좌표 범위에 사용 불가|포인터와 동적 할당으로 인한 구현 복잡성 증가|

<br>

### 좌표 압축(Coordinate Compression)
- 큰 좌표 문제를 일반 세그먼트 트리로 해결할 수도 있지만, 동적 세그먼트 트리는 좌표 압축 과정 없이 문제를 직접 풀 수 있게 해준다.
- Online Query 문제에서는 필수조건이다.

<br>

### 📕 Ref
https://codeforces.com/blog/entry/64971
