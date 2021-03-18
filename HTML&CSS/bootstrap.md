# Bootstrap

[부트스트랩 공식사이트](https://getbootstrap.com/)

- 반응형 웹 디자인: 다양한 화면크기에 맞춰서 웹 페이지를 보여주는 기술
- bootstrap grid system: 12개 column, 6개의 breakpoint가 존재
  - 12개의 column을 이용해서 레이아웃을 쉽게 짤 수 있다.
  - 6개의 breakpoint: `xs`, `sm`, `md`, `lg`, `xl`, `xxl`
  - `container` > `row` > `col`
  
- Content Delivery Network(cdn)으로 사용

## 1. Alert

- 로그인 실패, 성공 시, 등등에 뜨는 메세지



## 2. button

- a, input 태그를 사용해서 버튼을 만들어 사용할 수 있다.
  - 추가적인 기능을 가지고 있어서 더 자주 사용



## 3. card

- 카드 모양



## 4. Carousel

- 여러 이미지를 일정시간마다 혹은 버튼 클릭을 통해서 넘겨주며 보여줌



## 5. Modal

- 팝업창
- 사용시 modal의 id값과 button의 data-bs-target값을 일치시켜줘야 한다.



## 6. Nav and tab, Navbar

- 웹페이지 상단, 좌측에 있는 탭
- flexbox로 만들어져 있어서 flex기능을 사용해서 정렬시킬 수 있다.



## 7. Pagination

- 페이지 변경을 하기 위한 버튼



## 8. Form

- 설문조사, 회원가입 등 input데이터를 받을 때 사용
- aria-describedby
  - form 내부에 있는 input의 속성
  - 스크린 리더가 aria-describedby의 값을 id값으로 가지는 요소를 읽어준다.
  - 웹 접근성을 고려한 것!!
- 웹 접근성
  - [널리](https://nuli.navercorp.com/)에서 체험 가능

## 9. Icon

- 부트스트랩 icon 탭에서 cdn으로 사용 가능
- [font awesome](https://fontawesome.com/)

- i태그는 원래 이탤릭체를 쓸 때 사용하는 인라인 태그