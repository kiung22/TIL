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





