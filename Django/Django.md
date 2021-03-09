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



## Variable routing

- 주소 자체를 변수처럼 사용
- `path('hello/<str:name>/', views.hello),`



## 작성 순서

1. `django-admin startproject 프로젝트이름 .` 프로젝트 생성(마지막 .은 현재 폴더에 바로 생성하겠다는 의미!)
2. `python manage.py startapp 앱이름` app 생성 후 등록(settings.py => INSTALLED_APPS에 추가) (app 이름은 `복수형`으로)
3. project폴더의 `urls.py`에서 앱 path 추가

```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('articles/', include('articles.urls')),
    path('pages/', include('pages.urls')),
]
```

4. app폴더에 `urls.py`를 만든다.

```python
from django.urls import path
from . import views

app_name = 'articles'	# 템플릿에서 url태그를 사용할 때 활용된다.

urlpatterns = [
    path('index/', views.index, name='index'),
]
```

> app이 많아지면 같은 이름의 템플릿이 생기게 되기 때문에 app폴더안에서 urls.py를 만들어 관리한다.

5. app폴더의 `views.py`

```python
from django.shortcuts import render

def index(request):
    return render(request, 'articles/index.html')
```

6. `peoject폴더/templates/base.html` 생성

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.0-beta2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-BmbxuPwQa2lc/FVzBcNJ7UAyJxM6wuqIj61tLrc4wSX0szH/Ev+nYRRuWlolflfl" crossorigin="anonymous">
</head>
<body>
  <div class="container">
      
    {% block content %}
    {% endblock content %}
      
  </div>
  <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.0-beta2/dist/js/bootstrap.bundle.min.js" integrity="sha384-b5kHyXgcpbZJO/tY9Ul7kGkf1S0CWuKcCD38l8YkeH8z8QjE0GmW1gYU5S9FOnJ0" crossorigin="anonymous"></script>
</body>
</html>
```

> 모든 페이지에서 적용되는 공통 디자인을 base.html에 생성하여 중복코드를 최소화해준다.(상속)

7. `project폴더/settings.py`에서 TEMPLATES리스트에 DIRS 추가

```python
TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [BASE_DIR / 'pjt' / 'templates'],	# 여기에 경로 추가!!
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]
```

> 앱 폴더는 기본적으로 찾게 설정이 되어있지만(APP_DIRS = True) 프로젝트폴더의 템플릿폴더는 경로를 추가해주어야 한다.

8. `app폴더/templates/app이름/index.html` 생성

```django
{% extends 'base.html' %}

{% block content %}
  <h1>여기는 articles의 index입니다.</h1>
{% endblock contet %}
```

> templates안에 app폴더를 하나 더 만드는 이유는 장고가 templates폴더 안에 있는 모든 템플릿파일을 한군데로 모아서 찾게 되는데 이때 같은 이름의 템플릿끼리 충돌이 되는 것을 방지하기 위함이다.