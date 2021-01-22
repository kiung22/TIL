# Python

> Python의 모든 것



## 데이터 타입

### 문자열(str)

- `str()`, `''`

- `'내용'`
  - `f'{변수}'` 로 포맷팅 가능
    - `f'{pi:.3}'` => 변수pi를 3자리의 숫자까지만 보여줌(3.14)
- 시퀀스 컨테이너



### 정수(int)

- `int()`

- `123 `과 같이  `''`없이 숫자만 입력

- `'+', '-', '*', '/', '//', '%' `  사칙연산 가능

- **진수**

  - 2진수: `0b123`
  - 8진수: `0o123`
  - 10진수: `123`
  - 16진수: `0x123`




### 컨테이너

#### 시퀀스

##### 리스트(list)

- `list()`, `[]`
- `[원소1, 원소2, ...]`
- `[x for x in range(5)]` => `[0, 1, 2, 3, 4]`
  - 리스트 안에 for문을 사용하여 정의할 수 있다.
- indexing
  -  `my_list[index]`
- slicing
  - `my_list[0:2:2]`
- mutable



##### tuple

- `tuple()`, `()`

- `(원소1, 원소2, ...)`
  - 원소가 하나일 때에는 `(원소,)`
- **리스트와는 다르게 값을 수정할 수 없다.**



#### 비 시퀀스

##### 딕셔너리(dict)

- `dict()`, `{}`

- `{'key1': 'value1', 'key2': 'value2', ...}`
- `딕셔너리['key']`
  - key를 이용하여 value를 호출
- 중복된 key x
- mutable



##### 집합(set)

- `set()`

- `{값1, 값2, 값3, ...}`
- 중복된 값 x
- mutable



## 변수

- '키워드'  쓸 수 없음
- 숫자로 시작 불가능
- 이미 정의된 함수로 사용 x



## 함수
### 내장함수

- `len()`: 리스트나 문자열의 길이를 반환

- `import`: 라이브러리를 불러올 때 사용
  
  - `from import `으로도 사용가능
  
- `type()`: 데이터 타입을 반환

- `id()`: 데이터가 저장된 주소값을 반환

- `range()`: 숫자의 시퀀스를 나타내기 위해 사용

  - 기본형: `range(n)`

    > 0부터 n-1까지

  - 범위 지정: `range(n, m)`

    > n부터 m-1까지

  - 범위 및 스텝 지정: `range(n, m, s)`

    > n부터 m-1까지 +s만큼 증가

- `enumerate()`: 원소와 인덱스값을 튜플 형식으로 반환
  - `list(enumerate(iterable))` => `[(0, 원소1), (1, 원소2), ...]`
  - `enumerate(iterable, start=1)`로 1부터 시작 가능
  
- `map(함수, iterable)`: iterable의 모든 원소에 각각 함수를 적용시켜줌

  - `list(map(int, ['12', '23', '43']))` => `[12, 23, 43]`



### 함수 선언

```python
def function_name(parameter):
    # 실행 코드
    return result
```



## 예외 처리

````python
try:
    # 실행할 코드
except:
    # 에러 발생시 실행할 코드
    
    
# 특정 에러 지정
try:
    # 실행할 코드
except ZeroDivisionError:
    # ZeroDivisionError가 발생하면 실행할 코드
````



## 파일 입출력

- `open(filename, mode='r', encoding='utf-8')`: 파일 열기
  - `r`: 읽기모드
  - `w`: 쓰기모드



- `json to dict`

```python
import json

# music.json 파일을 utf-8방식으로 인코딩해서 열기
music_file = open("music.json", encoding='utf-8')
# jso파일을 파이썬에서 사용할 수 있는 데이터구조(dict)로 변환
music_dict = json.load(music_file)
```

> `.json`: list, dict로 이루어진 데이터파일