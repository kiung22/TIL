# 검색(Search)



## 1. 순차 검색(Sequential Search)

- 배열이나 연결리스트 등 순차구조로 구현된 자료구조에서 유용하다.
- 알고리즘이 단순하여 구현이 쉽다.
- 검색 대상이 많으면 수행시간이 급격히 증가하여 비효율적이다.
  - 하나를 찾는데 걸리는 시간 O(n)
  - m개를 찾는데 걸리는 시간 O(n * m)

### 1.1 정렬되어 있지 않은 경우

1. 첫 번째 원소부터 순서대로 찾는다.
2. 검색대상의 키 값과 동일한 키 값을 가진 원소를 찾으면 성공.
3. 마지막 원소까지 키 값이 동일한 원소를 찾지 못하면 실패.

### 1.2 정렬되어 있는 경우(오름차순이라고 가정)

1. 자료를 순차적으로 검색한다.
2. 원소의 키 값이 검색 대상의 키 값보다 크면 종료.



## 2. 이진 탐색(Binary Search)

- 자료가 정렬되어 있어야 한다.
- 자료의 가운데에 있는 원소의 키 값과 비교하며 검색 범위를 반으로 줄여나가면서 검색을 진행한다.
- 시간 복잡도 O(log<sub>2</sub>n)

### 2.1 과정

1. 자료의 중앙에 있는 원소의 값과 목표 값을 비교한다.
2. 목표 값이 더 작으면 자료의 왼쪽 반에 대해서 수행하고 목표 값이 더 크면 자료의 오른쪽 반에 대해서 수행한다.
3. 위의 과정을 반복하며 범위를 절반씩 줄여 나가면서 목표 값을 찾는다.

