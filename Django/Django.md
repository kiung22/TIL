# Django

- [장고 홈페이지](https://www.djangoproject.com/)

- dynamic web: 웹페이지의 요청을 받았을 때 사용자의 요청에 따라 server-side에서 다른 데이터를 가공하여 제공해주는 웹을 말한다.

- 모델-뷰-컨트롤러(Model-View-Controller, MVC): 소프트웨어 공학에서 사용되는 소프트웨어 디자인 패턴

- 장고에서는 모델-템플릿-뷰(Model-Template-View, MTV)패턴을 따른다.
  - 모델: 데이터베이스 관리
  - 템플릿: 레이아웃
  - 뷰: 중심 컨트롤러



## 명령어

- `django-admin startproject <프로젝트 이름>`: 프로젝트 생성하는 명령어, 서버가 만들어진다.

- `python manage.py runserver`: 서버활성화
- `python manage.py startapp <앱 이름>`: 앱 생성
  - `settings.py`의 `INSTALLED_APPS`에 앱 이름을 추가해주어야 한다.



## 기본 파일

### 프로젝트 폴더

- `settings.py`: 프로젝트의 모든 설정을 담당한다.
  - `LANGUAGE_CODE`: 'ko-kr'
  - `TIME_ZONE`: 'Asia/Seoul'
- `urls.py`: 사용자의 요청을 가장 먼저 만나는 파일

### 앱 폴더

- `admin.py`: 관리자 페이지를 관리하는 파일
- `models.py`: MTV에서 모델의 역할을 하는 파일
- `tests.py`: 테스트코드를 작성하는 파일
- `views.py`: MTV에서 뷰의 역할을 하는 파일

- `templates`: 템플릿파일을 저장할 templates폴더를 만들어줘야 한다. 이름을 반드시 지킬 것!!



## Django template language(DTL)

- django template에서 사용하는 built-in template system

- 조건, 반복, 변수 치환, 필터 등
- 변수: `{{ 변수 }}`으로 사용
- 필터: `{{ 변수|필터 }}`
  - `{{ name|lower }}` => name을 모두 소문자로 출력
  - `{{ variable|truncatewords:30 }}` => 필터인자 받는법
  - chained 가능
- 태그: `{% tag %}`
  - 출력 텍스트를 만들거나, 반복, 논리 수행
- 주석: `{# 주석 #}` 한줄 주석
  - 여러줄: `{% comment %}` `{% endcomment %}` 태그를 이용



## Template inheritance

- `{% extends 부모템플릿 %}`: 자식템플릿이 부모템플릿을 확장한다는 것을 알리는 태그, 반드시 템플릿 최상단에 작성
- `{% block 블록이름 %}`: 하위 템플릿에서 overriden할 수 있는 블록을 정의

- `settings.py`의 `TEMPLATES['DIRS']`에 경로를 추가해주어야 한다.

  - ```python
    'DIRS': [BASE_DIR / 'firstpjt' / 'templates']
    ```

  - app templates이 아닌 이외의 경로는 모두 추가해주자!

  - OS마다 경로를 다르게 표시하기 때문에 `pathlib`을 활용해서 경로를 표시한다.



## Django template system

- 표현(template)과 로직(view)을 분리
  - 템플릿 시스템은 표현을 제어하는 도구이자 표현에 관련된 로직일 뿐이다.
- 중복을 배제
  - 동적 웹사이트는 공통 디자인을 갖는 경우가 많다.
  - 상속을 통해 중복을 없앤다.



## 장고 작성시 주의사항

- app 이름은 `복수형`
- app 생성(startapp) 후 등록(settings.py에 추가)



## Variable routing

- 주소 자체를 변수처럼 사용

- `path('hello/<str:name>/', views.hello),`