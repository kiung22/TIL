# HTML



## 1. HTML 기본 구조



### 1.1 head

- 웹페이지에 대한 정보나 내부참조를 담고 있다.
- 웹페이지에 보여주지는 않는다.
- Open Graph Protocol(og)에서 head의 정보를 이용하여 보여준다.

### 1.2 boby

- 실제 웹페이지에서 보여지는 내용들을 작성하는 공간

### 1.3 DOM(Document Object Model) 구조

- 태그끼리 부모자식 관계를 가지고 있다.
- python처럼 들여쓰기로 구분!

![Document Object Model - Wikipedia](HTML.assets/1200px-DOM-model.svg.png)

### 1.4 요소(element)

- `<태그이름 속성=속성값>내용</태그이름>`

- `<h1>contents</h1>`

- HTML의 요소는 태그(시작태그, 종료태그)와 내용으로 구성되어있다.
- 내용이 없는 태그는 닫는태그를 쓸 필요가 없다.



### 1.5 속성(attribute)

- `<a href="https://google.com"></a>`

- HTML에서는 쌍따옴표 사용!
- 속성끼리 구분은 스페이스바로 구분
- 태그별로 사용할 수 있는 속성은 다르다.



### 1.6 시맨틱 태그

- 기존에는 아무런 의미없는 div를 사용했다면 HTML5에서 의미론적 요소를 담은 태그가 등장
- 기능에서는 차이가 없지만 의미를 명확히 전달하여 코드의 가독성을 높여줌
- 검색엔진의 효율을 높여준다.
- 대표적인 시맨틱 태그
  - header: 문저 전체나 섹션의 머릿말
  - nav: 네비게이션
  - aside: 사이드에 위치한 공간
  - section: 문서의 컨텐츠의 그룹
  - article: 문서, 페이지, 사이트 안에서 독립적으로 구분되는 영역
  - footer: 문서 전체나 섹션의 마지막
- Non semantic 요소
  - div
  - span



