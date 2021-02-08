# 카운팅 정렬(Counting Sort)

집합에 각 항목이 몇 개씩 있는지 세는 작업을 하여 정렬하는 알고리즘



## 제한사항

- 모든 값들이 정수일때만 사용가능하다.
- 집합내의 가장 큰 정수를 알아야 한다.



## 시간 복잡도

- O(n + k)
- n은 리스트의 길이, k는 정수의 최댓값



## 과정

1. 가장 큰 정수값을 길이로 가진 count배열을 만든다.
2. 리스트의 값들을 카운팅을 하여 count배열에 저장한다.
3. count배열의 값을 누적값으로 바꾸어 준다.
4. count배열의 숫자를 하나씩 줄이면서 리스트의 뒤부터 정렬을 한다.
   - 뒤에서부터 정렬하는 이유는 동일한 값이 있을 때 순서를 지키기 위해서이다. => 안정정렬(stable sort)



## 코드

```python
def counting_sort(arr, k):
    # arr는 정렬을 할 리스트
    # k는 가장 큰 정수
    count = [0] * k
	
    # 카운팅
    for n in arr:
    	count[n] += 1
    # 누적합
    for i in range(1, len(count)):
        count[i] += count[i-1]
    # 정렬
    result = [0] * len(arr)
    for n in arr[::-1]:
        count[n] -= 1
        result[count[n]] = n
    return result
```

