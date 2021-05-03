# JavaScript



## 1. Document Object Model(DOM)

### 1-1. DOM

- 문서를 구조화하고 구성 요소를 하나의 객체로 취급하여 다루는 트리 모델
  - 구조화: 브라우저가 문자열(문서)를 해석(Parsing)하여 DOM Tree로 만드는 과정
- 속성 접근, 메서드 활용이 가능하고 프로그래밍 언어적 특성을 활용하여 조작이 가능하다.
- 주요 객체
  - `window`: DOM을 표현하는 창, 가장 최상위 객체, 생략이 가능
  - `document`: 페이즈 콘텐츠의 Entry Point 역할





### 1-2. DOM 조작

#### 1) DOM 선택

- `Document.querySelector()`
  - 제공한 CSS selector를 만족하는 첫번째 element객체를 반환, 없으면 null 반환

- `Document.querySelectorAll()`
  - 유효한 CSS selector를 인자로 받아서 만족하는 NodeList(static Collection)를 반환



##### Live Collection

- 문서가 바뀔 때 실시간으로 업데이트
- DOM의 변경사항을 실시간으로 반영한다.

- HTMLCollection
  - name, id, 인덱스 속성으로 접근 가능
- NodeList
  - 인덱스로만 접근이 가능
  - HTMLCollection과 달리 배열에서 사용하는 for each 함수 및 다양한 메서드를 사용이 가능



##### Static Collection

- DOM이 변경되어도 collection 내용에는 영향을 주지 않는다.
- `querySeletorAll()`이 반환하는 NodeList는 Static Collection이다.



#### 2) 변경

##### 생성

- `Document.createElement()`
  - 주어진 태그명으로 HTML 요소를 만들어 반환
- `ParentNode.append(childNode1, childNode2, ...)`
  - 부모 노드의 자식노드 리스트에 Node 객체나 DOMString을 삽입(여러 개 추가 가능)
- `ParentNode.appendChild(childNode)`
  - 부모 노드의 자식노드 리스트에 Node 객체를 삽입(하나만 추가 가능)

##### 삭제

- `Node.remove()`
  - 특정 객체를 제거
- `ParentNode.removeChild(childNode)`
  - 부모노드에서 특정 자식노드를 제거하고 반환

##### 속성

- `Node.innerText`
  - 노드와 그 자손의 텍스트 컨텐츠(DOMString)을 표현
  - 줄 바꿈을 인식하고 숨겨진 내용을 무시하는 등 최종적으로 스타일링이 적용된 모습을 표현
- `Node.innerHTML`
  - 요소내에 포함된 HTML 마크업을 반환
  - XSS공격(Cross-Site Scripting)에 취약함

##### 메서드

- `Element.setAttribute(name, value)`
  - 속성이 이미 존재하면 수정, 없으면 새 속성 추가
- `Element.getAttribute(name)`
  - 해당 속성을 반환





## 2. Browser Object Model(BOM)

- 자바스크립트가 브라우저와 소통하기 위한 모델
- 버튼, URL 입력창, 타이틀 바 등 브라우저 윈도우 및 웹페이지의 일부분을 제어 가능

- 인쇄 창

```
window.print()
```

- 탭 창

```
window.open()
```

- 대화상자 창

```
window.confirm()
```





## 3. Event

- 네트워크 활동, 사용자와의 상호작용(클릭 등) 같은 사건의 발생을 알리기 위한 객체
- 이벤트 처리기(Event-handlers)
  - `addEventListener()`
  - `removeEventListener()`

- addEventListener

```
target.addEventListener(type, listener)
```

- preventDefault: 이벤트에 의해 작동하는 기본동작을 중단시켜준다.

```
event.preventDefault()
```





## 4. AJAX

- Asynchronous Javascrpt And XML(비동기식 js, xml)
- 서버와 통신하기 위해 XMLHttpRequest 객체를 활용
  - 동기식, 비동기식 통신을 모두 지원하기 때문
- 페이지 전체를 reload하지 않고서 필요한 일부분만 업데이트되는 비동기성



### XMLGttpRequest

- 이름과 달리 XML뿐만아니라 모든 종류의 데이터를 받아오는데 사용 가능
- 전체페이지의 새로고침 없이 URL로부터 데이터를 받아옴



### 동기(Synchronous)와 비동기(Asynchronous)

- 동기식 
  - 순차적, 직렬적 태스크 수행
  - 요청을 보낸 후 응답을 받아야만 다음 동작이 이루어짐(blocking)
- 비동기
  - 병렬적 태스크 수행
  - 요청을 보낸 후 응답을 기다리지 않고 다음 동작이 이루어짐(non-blocking)



#### 비동기를 사용하는 이유

- 데이터의 크기가 굉장히 크다면 동기식 코드의 경우 데이터가 모두 로드한 뒤에야 앱이 실행되기 때문이다.
- 동기식 요청은 코드 실행을 차단(blocking)하여 화면이 멈추고 응답하지 않는 사용자 경험을 만들게 된다.



### Concurrency model

#### 1. Call Stack

- 요청이 들어올 때마다 해당 요청을 순차적으로 처리하는 Stack 형태의 자료 구조



#### 2. Web API(Browser API)

- 브라우저 영역에서 제공하는 API
- setTimeout(), DOMevents, AJAX로 데이터를 가져오는 시간이 소요되는 일들을 처리



#### 3. Task Queue

- 콜백함수가 대기하는 Queue 형태의 자료구조
- main thread가 끝난 후 실행되어 후속 JavaScript 코드가 차단되는 것을 방지



#### 4. Event Loop

- Call Stack이 비어 있는지 여부를 확인
- 비어 있는 경우 Task Queue에서 실행 대기중인 콜백이 있는지 확인
- Task Queue에 대기중인 콜백이 있다면 가장 앞에 있는 콜백을 Call Stack으로 push



### Promise

#### Promise object

- 비동기 작업의 최종 완료 또는 실패를 나타내는 객체
- `.then()`
  - 이전 비동기작업이 성공했을 때 수행할 작업을 나타내는 콜백함수
  - 이전 비동기작업의 결과가 콜백함수의 인자로 들어감
  - chaining으로 연쇄적인 작업을 수행할 수 있다.
- `.catch()`
  - .then이 하나라도 실패하면 동작
  - 이전 작업의 실패로 인해 생성된 error객체는 catch의 콜백함수에서 사용할 수 있다.
- `.finally()`
  - 성공과 실패에 상관없이 마지막에 무조건 실행되며 인자는 받지 않는다.
- 반환값이 반드시 있어야 연쇄적으로 작업을 수행할 수 있으므로 주의!!!



#### Axios

- [Axios gitjub](https://github.com/axios/axios) 

- 브라우저를 위한 Promise 기반의 클라이언트
- promise 객체를 반환
- async & await: .then chaining이 많이 되어있으면 가독성이 떨어지므로 이를 방지하게 해준다.

