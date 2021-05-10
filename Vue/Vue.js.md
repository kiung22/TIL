# Vue.js

- 대표적인 프론트엔드 프레임워크
  - Vue.js, React, Angular

- Single Page Application(SPA)
  - 단일 페이지 애플리케이션
  - 서버로부터 처음에만 페이지를 받아오고 이후에는 새로운 페이지를 받아오는 것이 아닌 동적으로 페이지를 구성
  - 스마트폰이 등장하면서 모바일 최적화에 대한 필요성이 생기게 되면서 CSR, SPA가 등장
- Client Side Rendering(CSR)
  - 최초 요청 시 서버에서 빈 문서를 응답하고 이후 클라이언트에서 데이터를 요청해 데이터를 받아 DOM을 렌더링하는 방식
  - SSR(Server Side Rendering)보다 초기 전송되는 페이지의 속도는 빠르지만 서비스에서 필요한 데이터를 클라이언트(브라우저)에서 추가로 요청하여 재구성해야 하기 때문에 전체 페이지 완료시점은 SSR보다 느리다.
  - SPA가 사용하는 렌더링 방식
  - 장점
    - 서버와 클라이언트 간의 트래픽 감소
      - 웹 어플리케이션에 필요한 모든 정적 리소스를 최초에 한번 다운로드
    - 사용자 경험 향상
      - 전체 페이지를 다시 렌더링하지 않고 변경되는 부분만을 갱신
  - 단점
    - SEO(검색엔진 최적화) 문제가 발생할 수 있음



## MVVM Pattern

1. Model

- Vue에서 Model은 JavaScript의 Object

2. View

- Vue에서 View는 DOM(HTML)

3. View Model

- Vue에서 View Model은 모든 Vue instance



## SFC

### Component

- 재사용 가능한 코드를 캡슐화하여 반복적인 코드를 작성하지 않게 도움을 준다.
- Vue 컴포넌트 = Vue 인스턴스



### SFC(Single File Component)

- Vue 컴포넌트 기반 개발
- 하나의 컴포넌트를 .vue라는 하나의 파일 안에 작성
- 싱글 파일 컴포넌트를 통해 개발하는 방식



## Vue CLI

- vue-cli 설치

```
$ npm install -g @vue/cli
```

- 버전확인

```
$ vue --version
```

- 프로젝트 생성

```
$ vue create <프로젝트 이름>
```

- run server

```
$ npm run serve
```



## Babel

- 자바스크립트의 신버전 코드를 구버전으로 번역/변환 해주는 도구
- 파편화와 표준화의 영향으로 최신 문법을 사용해도 브라우저의 버전별로 동작하지 않는 상황이 발생
- 원시코드(최신 버전)를 목적코드(구 버전)으로 옮기는 번역기



## Pass Props & Emit Events

- 부모는 자식에게 데이터를 전달(Pass Props)
- 자식은 부모에게 이벤트를 전달(Emit Events)



### Props

- 상위 컴포넌트의 정보를 하위 컴포넌트에 전달하기 위한 사용자 지정 특성
- 단방향 데이터 흐름
  - 자식 요소가 의도치 않게 부모 요소의 상태를 변경시키는 것을 방지하기 위함
- 상위 컴포넌트에서 props의 값을 줄 때는 html문서에서 작성하므로 kebab-case로 작성
- 하위 컴포넌트에서 props의 값을 받을 때는 javascipt에서 작성하므로 camelCase로 작성



### Events

- $emit(event)
  - 현재 인스턴스에서 이벤트를 트리거
  - 추가 인자는 리스너의 콜백 함수로 전달

- 이벤트 이름은 kebab-case로 작성, 자동으로 소문자로 변환되기 때문에 camelCase로 작성하면 안된다.



## Vue Router

- SPA상에서 라우팅을 쉽게 개발할 수 있는 기능을 제공
- router-link
  - index.js 파일에서 정의한 경로에 등록한 특정한 컴포넌트와 매핑
  - HTML5 히스토리 모드에서 router-link는 클릭 이벤트를 차단하여 브라우저가 reload하지 않게 함
- router-view
  - 실제 컴포넌트가 DOM에 부착되어 보이는 자리
  - router-link를 클릭하면 해당 경로와 연결되어 있는 index.js에 정의한 컴포넌트가 위치



### History mode

- HTML histiory API를 사용해서 브라우저의 히스토리는 남기지만 실제 페이지는 이동하지 않게 router를 구현



### Vue Router가 필요한 이유

1. SPA 등장 이전에는 서버가 모든 라우팅을 통제하고 요청 경로에 맞는 HTML을 제공했다면 SPA 등장 이후에는 서버는 index.html하나만 제공하고 요청에 대한 처리를 더이상 서버가 하지 않는다.
2. SSR: 라우팅의 결정권을 서버가 가진다.
3. CSR: 라우팅에 대한 결정권을 클라이언트가 가지며 주소가 변경되면 주소에 맞는 컴포넌트를 렌더링



### .vue 구조

- App.vue
  - 최상위 컴포넌트
- views/
  - router(index.js)에 매핑되는 컴포넌트를 모아두는 폴더
- components/
  - router에 매핑된 컴포넌트 내부에 작성하는 컴포넌트를 모아두는 폴더

