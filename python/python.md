# Python

> Python의 모든 것



## 데이터 타입

### 문자열(str)

- `str()`, `''`

- `'내용'`
  - `f'{변수}'` 로 포맷팅 가능
    - `f'{pi:.3}'` => 변수pi를 3자리의 숫자까지만 보여줌(3.14)
  
- 시퀀스 컨테이너

#### 메서드

1. 조회/탐색

   - `.find(x)`: 'x'의 첫번째 위치를 반환, 없으면 -1을 반환

   - `.index(x)`: 'x'의 첫번째 위치를 반환, 없으면 에러발생

2. 값 변경
   - `.replace(old, new[, count])`: 바꿀 대상 글자를 새로운 글자로 바꿔서 반환
   - `.strip([chars])`: 특정한 문자들을 지정하면(지정하지 않으면 공백), 양쪽을 제거
     - `.lstrip()`, `.rstrip()`은 왼쪽, 오른쪽을 제거
   - `.split()`: 문자열을 특정한 단위로 나누어 리스트로 반환
   - `.join()`: iterable 요소들을 합쳐서 문자열로 반환
3. 문자 변형
   - `.capitalize()`: 앞글자를 대문자로 만들어 반환
   - `.title()`: 어포스트로피(')나 공백 이후를 대문자로 만들어 반환
   - `.upper()`: 모든 문자를 대문자로 반환
   - `.lower()`: 모든 문자를 소문자로 반환
   - `.swapcase()`: 대소문자를 바꿔서 반환
4. 검증
   - `.isalpha()`
   - `.isdecimal()`
   - `.isdigit()`
   - `.isnumeric()`
   - `.isspace()`
   - `.isupper()`
   - `.istitle()`
   - `.islower()`

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
  - `[x for x in range(5) if x % 2]`
  - `[x if x < 0 else -x for x in range(-10, 11)]`
  
- indexing
  
  -  `my_list[index]`
  
- slicing
  
  - `my_list[0:2:2]`
  
- **mutable**

  - 리스트 복사

    1. 얕은 복사
       - slice 연산자 사용 [:]

       - `list()` 활용

    2. 깊은 복사

       - `copy.deepcopy()`

       - ```python
         import copy
         a = [[1, 2, 3], 2, 3]
         b = copy.deepcopy(a)
         ```

###### 메서드

1. 값 추가 및 삭제
   - `.append(x)`: 리스트에 값을 추가할 수 있다.
   - `.extend(x)`: 리스트에 iterable값을 붙일 수 있다.
   - `.insert(i, x)`: 위치 i에 값을 추가
   - `.remove(x)`: 값이 x인 것을 삭제, x가 없으면 에러 발생
   - `.pop(i)`: 위치 i에 있는 값을 삭제하며, 그 항목을 반환
   - `.clear()`: 모든 항목을 삭제
2. 탐색 및 정렬
   - `.index(x)`: x의 index값을 반환, x가 없으면 에러 발생
   - `.count(x)`: x의 개수를 반환
   - `.sort()`: 리스트를 정렬해주고 `None`을 반환
   - `.reverse()`: 리스트를 반대로 뒤집는다. (정렬아님!!)



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
  
- `{키: 값 for 요소 in iterable}`

  ```python
  a = [1, 2, 3]
  {str(n): n for n in a}
  ```

- 중복된 key x

- **mutable**

###### 메서드

1. 조회
   - `.get(key[, default])`: key의 value를 가져옴, key가 없으면 `default`값을 반환, `default`가 없으면 `None`을 반환
2. 추가 및 삭제
   - `.pop(key[, default])`: key의 value를 제거하고 반환, key가 없으면 `default`값을 반환, `default`가 없으면 에러 발생
   - `.update()`: 값을 제공하는 key와 value로 덮어씁니다.



##### 집합(set)

- `set()`
- `{값1, 값2, 값3, ...}`
- 중복된 값 x
- **mutable**

###### 메서드

1. 추가 및 삭제
   - `.add(x)`: x를 집합에 추가
   - `.update(*iterable)`: 여러가지값을 추가
   - `.remove(x)`: x를 삭제, 없으면 KeyError발생
   - `.discard(x)`: x를 삭제, 없어도 에러가 발생하지 않는다
   - `.pop()`: 임의의 원소를 제거해 반환



## 변수

- '키워드'  쓸 수 없음
- 숫자로 시작 불가능
- 이미 정의된 함수로 사용 x



## 함수
### 내장함수

- `len()`: 리스트나 문자열의 길이를 반환

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
  - `list(map(lambda x, y: x * y, [1, 2, 3], [4, 5, 6]))`
  
- `filter(함수, iterable)`: iterable에서 함수의 반환 결과가 `True`인 것들만 구성하여 반환



### 함수 선언

1. 위치인자

```python
def function_name(parameter1, parameter2):
    # 실행 코드
    return result
```

2. 키워드인자

```python
def function_name(key1=parameter1, key2=parameter2):
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



## 모듈

- 특정 기능을 `.py` 파일 단위로 작성한 것.
- 함수, 변수, 클래스 등을 가져와 사용할 수 있다.
- 모듈이 모이면 => 패키지

- `import 모듈`: 라이브러리를 불러올 때 사용
- `dir(모듈)`: 모듈에 있는 데이터들을 확인
- 자주 사용할 함수를 변수에 할당하여 사용할 수 있다.



## 패키지

### 1. 패키지 생성

- 패키지폴더 안에 모듈 혹은 서브 패키지로 구성되어 있다.

- `__init__.py`이름의 빈 파일을 패키지 폴더 안에 생성!!



### 2. 패키지 활용

- `from 패키지 import 모듈 `
- `from 패키지.모듈 import 데이터` : 특정한 함수 혹은 어트리뷰트만 활용할 때
- `from 모듈 import *` : 해당하는 모듈 내의 모든 변수, 함수, 클래스를 가져올 때
- `from 모듈 import 데이터 as 별명` : 내가 지정하는 이름을 붙여 가져올 때



## OOP(객체 지향 프로그래밍)

### 1. 객체

> 객체는 타입(type), 속성(attribute), 조작법(method)을 가진다.

1. 타입(type)

- 공통된 속성과 조작법을 가진 객체들을 분류해 놓은 것

2. 인스턴스(instance)

- 특정 타입의 실제 예시, 실제 데이터

3. 속성(attribute)

- 객체의 데이터

4. 조작법(method)

- 객체에 적용할 수 있는 행위

| 인스턴스 |          3 + 4j          |     'apple'     |
| :------: | :----------------------: | :-------------: |
|   타입   |         complex          |       str       |
|   속성   | 3 + 4j.real, 3 + 4j.imag |                 |
|  메서드  |                          | 'apple'.split() |



### 2. 클래스

1. 클래스 생성

- `class 클래스이름:`

2. 인스턴스 생성

- `인스턴스 = 클래스()`

3. 속성(attribute), 메서드 정의

```python
class Person:
    # 생성자: 인스턴스가 생성될 때 호출되는 함수
    def __init__(selt, name, age):
        # 속성
        self.name = name
        self.age = age
        print('생성자')
        
    # 메서드
    def talk(self):
        print(f'안녕, 나는 {self.name}라고 해.')
       
    # 소멸자: 인스턴스가 소멸되기 직전에 호출되는 함수
    def __del__(self):
        print('소멸자')
```

4. 매직메서드

- 더블언더스코어`__`가 있는 메서드
- `__str__`: 객체를 출력할 때 보여줄 내용을 정의
  - 사용자가 보기 쉬운 형태로 출력

```python
class Person:
    # 생성자: 인스턴스가 생성될 때 호출되는 함수
    def __init__(selt, name, age):
        # 속성
        self.name = name
        self.age = age
        
    def __str__(self):
        return f'{self.name}, {self.age}'
```

- `__repr__`: `__str__`와 다르게 시스템이 해당객체를 인식할 수 있는 공식적인 형태로 출력

#### 2.1 상속(inheritance)

- 부모 클래스의 속성과 메서드를 자식클래스가 사용할 수 있다.
  - `class 자식클래스(부모클래스):`

- `isinstance()`: 상속 관계에 있어도 True를 반환

- 클래스 정의할 때 `super()`를 이용하여 부모클래스를 불러와서 사용 가능