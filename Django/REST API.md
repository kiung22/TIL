# REST API(Representational State Transfer)



- 웹 설계상의 장점을 최대한 활용할 수 있는 아키텍처 방법론
- 자원과 주소를 지정하는 방법

### REST 핵심 규칙

1. URI는 정보의 자원을 표현해야 한다.

2. 자원에 대한 행위는 HTTP Method로 표현한다.



## REST 구성

### 1. 자원(URI)

- URI: Uniform Resource Identifier
  - 통합 자원 식별자
  - 인터넷의 자원을 나타내는 유일한 주소
  - URL, URN의 상위개념
- URL: Uniform Resource Locator
  - 통합 자원 위치
  - 네트워크 상에 자원(HTML, CSS, 이미지 등)이 어디있는지를 알려주기 위한 약속
  - 웹 주소, 링크라고도 불림
- URL: Uniform Resource Name
  - 통합 자원 이름
  - 자원의 유일한 이름 역할
  - 자원의 위치를 옮겨도 문제없이 동작

#### URI 구조

- Scheme|Protocol/Host/Port/Path 까지 URL

- Scheme|Protocol/Host/Port/Path?Query

  `http://localhost:3000/posts/3?q=http`

- Scheme|Protocol/Host/Port/Path#fragment

  `http://getbootstrap.com/docs/4.1/layout/overview#containers`

#### URI 설계 주의사항

- 가독성을 위해 밑줄이 아닌 하이픈`-`을 사용
- 소문자를 사용(대소문자에 따라 다른 자원으로 인식)
- 파일 확장자는 포함시키지 않음



### 2. 행위(HTTP Method)

#### 1. HTTP(HyperText Transfer Protocol)

- HTML 문서와 같은 자원들을 가져올 수 있도록 해주는 프로토콜(약속)
- 비연결지향(connectionless)
  - 서버는 응답 후 접속을 끊음
- 무상태(stateless)
  - 접속이 끊어지면 클라이언트와 서버간의 통신이 끝나며 상태를 저장하지 않음(로그인 시 쿠키와 세션으로 로그인상태를 따로 보내주는 이유)

#### 2. HTTP Method

- 주어진 자원에 수행하길 원하는 행동을 나타낸다.
- 의미론적으로 행위를 규정하기 때문에 실제 그 행위 자체가 수행됨을 보장하진 않는다.
- HTTP verb

#### 3. 종류

- GET
  - 서버에서 데이터를 받는다.
- POST
  - 서버로 데이터를 전송하며, 서버에 변경사항을 만든다.
- PUT
  - 요청한 주소의 자원을 수정
- DELETE
  - 지정한 자원을 삭제



### 3. 표현(Representations)

#### 1. JSON

- JavaScript Object Notation
  - lightweight data-interchange format
  - 구조화된 데이터를 표현하기 위한 문자 기반 데이터 포맷
  - 웹 어플리케이션에서 클라이언트로 데이터를 전송할 때 사용
- 특징
  - 사람이 읽고 쓰기 쉽고 기계가 파싱(해석, 분석)하고 만들어 내기 쉬움
  - 딕셔너리로 변환할 수 있는 key-value로 이루어져 있음



## Django REST Framework(DRF)

- https://github.com/encode/django-rest-framework

- REST framework 개발에 필요한 기능을 제공



## Serialization(직렬화)

- 데이터 구조나 객체 상태를 다른 환경에 저장하거나 재구성할 수 있는 포맷으로 변환하는 과정
- DRF(Django REST framework)의 Serializer는 Queryset, Model instance와 같은 데이터를 JSON, XML 등의 유형으로 쉽게 변환할 수 있는 Python 데이터 타입으로 만들어 준다.

