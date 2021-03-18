# CSS



## 1. CSS 구문

```css
h1 {
    color: blue;
    font-size: 15px;
}
```



## 2. CSS 정의 방법

1. 인라인

- 태그의 style속성을 활용



2. 내부참조

- html파일안에서 head부분에서 style태그를 활용



3. 외부참조

- 일반적으로 공통된 속성에 대해서 .css파일을 만들어 외부참조를 사용

- .css파일을 html파일의 head부분에 link태그을 활용하여 불러온다.



## 3. 선택자(Selector)

### 3.1 선택자 종류

- 특정한 요소를 선택하여 스타일링하기 위해서 선택자를 활용
- 기본 선택자
  - 전체 선택자(*), 요소 선택자
  - 클래스 선택자(.), 아이디 선택자(#), 속성 선택자
- 결합자(Combinarors)
  - 자손 결합자(부모 자손), 자식 결합자(부모 > 자식)
  - 일반 형제(~), 인접 형제 결합자(+)
- 의사 클래스/요소(pseudo class)
  - 링크, 동적 의사 클래스



### 3.2 선택자 사용법

1. class 선택자

- `.class`로 사용
- 클래스는 여러개 사용 가능, 따라서 가장 많이 사용



2. id 선택자

- `#id`로 사용
- id는 문서당 원칙적으로 한번만 사용(서로 다른 이름의 id를 사용해야 한다.)



3. 자손 결합자

- `부모 자손`으로 사용(스페이스바로 구분)
- 모든 자손들을 선택



4. 자식 결합자

- `부모 > 자식`으로 사용
- 부모의 직속 자식만 선택



5. 일반 형제 결합자

- `A~B`
- A의 형제요소 중에서 A 뒤에 있는 B요소를 모두 선택



6. 인접 형제 결합자

- `A+B`
- A의 형제요소 중에서 A 바로 뒤에 있는 B요소를 선택



### 3.3 적용 우선순위(cascading order)

0. 중요도(!important) but 사용 x

1. 인라인(인라인 방식으로 style을 직접 지정한 속성)
2. id 선택자
3. class 선택자(주로 사용)
4. 요소 선택자(태그이름)
5. 소스 순서(상위 객체에 의해 상속된 속성)
   - 상속 되는 것들: Text 관련 요소
   - 상속 되지 않는 것들: Box model 관련 요소, position 관련 요소



## 4. 단위

### 4.1 상대 크기 단위

- px (픽셀): 기기마다 픽셀의 크기가 다양하므로 요즘에는 사용하지 않는다.
- % (비율)
- em: 배수단위, 요소에 지정된 사이즈(부모에게 상속받은 사이즈)에 상대적인 사이즈를 가짐.
- rem: 최상위 요소(html)의 사이즈(16px)를 기준으로 배수 단위를 가짐.(가장 많이 사용)
- Viewport: 웹페이지를 방문한 유저에게 현재 보이는 영역
  - vw, vh



### 4.2 색상 단위

- 색상 키워드
- RGB 색상
  - Red, Green, Blue
- HSL 색상
  - 색상, 채도, 명도



## 5. Box model

1. Margin: 테두리 바깥의 외부 여백
   - 인접한 블록요소들끼리는 탑, 바텀 마진을 서로 상쇄되므로 주의!!
2. Border: 테두리
3. Padding: 테두리와 content 사이의 여백
4. Content: 내용

![What is the CSS Box Model · Front End web development - coding lead](data:image/png;base64,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)



## 6. display

- block
  - div, p, h1, li
- inline
  - span, a, img, input, label

- inline-block
  - inline처럼 content만큼 자리를 차지
  - block처럼 width, height, margin 속성을 지정할 수 있다.
- none



## 7. Position

- static: 기본값으로 top, right, bottom, left, z-index가 아무런 영향을 주지 않는다.

- relative: 자기 자신 위치(static)를 기준
  - 이동하더라고 본연의 자리를 다른 객체가 차지하지 않다.
- absolute: static이 아닌 가장 가까이 있는 부모/조상 위치를 기준
  - 자신의 static자리를 다른 객체가 차지한다.
  - 모두 static일 경우에는 body 태그를 기준으로 위치를 잡게된다.
- fixed: 화면 기준



## 8. Float

- 이미지 좌, 우측 주변으로 텍스트(인라인 요소)를 둘러싸는 레이아웃을 구현하는 데에 사용

### 8.1 속성

- none: 기본값
- left
- right



### 8.2 Float clear

- float 사용시 자기 자리가 사리지기 때문에 float하지 않은 요소들과 곂칠 수 있다.
- clearfix: 부모태그에 클래스 설정

```css
.clearfix::after {
  content: "";
  display: block;
  clear: both;
}
```

- 보이지 않는 블럭을 생성하여 다른 요소가 못 올라오게 막아준다.



## 9. Flexbox(Flexible Box Layout Module)

- 공간 배분과 1차원 정렬
- 메인축과 교차축이 존재
  - 교차축은 메인축의 수직방향의 축
- Flex Container(부모 요소), Flex item(자식 요소)

```css
.flex-container {
    display: flex;
}
```



### 9.1 속성

- 배치 방향: 메인축의 방향을 선택(행 or 열)
  - flex-direction: row, row-reverse, column, column-reverse
- 축방향 정렬
  - justify: 메인축 정렬
  - align: 교차축 정렬
    - content: 여러 줄
    - items: 한줄
    - self: flex item 개별 요소
  - justify-content, align-items, align-self




- flex-wrap
  - nowrap: 모든 요소들을 한 줄에 정렬
  - wrap: 요소들을 여러 줄에 걸쳐 정렬
  - wrap-reverse: 요소들을 여러 줄에 걸쳐 반대로 정렬
- flex-flow: flex-direction과 flex-wrap의 shorthand
- flex-grow: 주축에서 남는 공간을 요소들에게 할당

- order: 기본값은 0, 작을 순서부터 정렬

- [개구리게임](https://flexboxfroggy.com/#ko)



### 10. 미디어 쿼리

- 반응형 디자인의 핵심 구성 요소
- 쉽게 사용하기 위해 [bootstrap](https://getbootstrap.com/) 사용



### 11. Animation

- css에서 애니메이션동작을 줄 수 있다.
- [animate](https://animate.style/)로 쉽게 사용할 수 있다.



### 12. font 적용

- [구글 폰트](https://fonts.google.com/)에서 적용