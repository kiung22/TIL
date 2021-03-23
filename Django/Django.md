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
  
  ```python
  INSTALLED_APPS = [
      # app,
      # 3rd part app,
      # django app,
  ]
  ```
  
  



## 기본 파일

### 프로젝트 폴더

- `settings.py`: 프로젝트의 모든 설정을 담당한다.
  - `LANGUAGE_CODE`: 'ko-kr'
  - `TIME_ZONE`: 'Asia/Seoul'
  - `USE_I18N`: 국제화
  - `USE_L10N`: 현지화
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



## Object-Relational Mapping(ORM)

- 객체와 관계형 데이터베이스의 데이터를 자동으로 매핑해주는 것을 말한다.



## Migrations

- 장고가 model에 생긴 변화를 반영하는 방법
  - `makemigrations`: model을 변경한 것에 기반한 새로운 마이그레이션(설계도)을 만들 때 사용
  - `migrate`: 새로 만든 마이그레이션을 DB에 적용
  - `sqlmigrate`: 마이그레이션에 대한 SQL구문을 보기 위해 사용
    - `python manage.py sqlmigrate 앱이름 마이그레이션번호`
  - `showmigrations`: 마이그레이션 파일들이 migrate 됐는지 확인하기 위해 사용



## Database API

- DB API 구문: `Article.objects.all()`

​	       `Class Name` . `Manager` . `QuerySet API`

- [Queryset API](https://docs.djangoproject.com/en/3.1/ref/models/querysets/)

- 크게 queryset으로 반환하는 메서드와 단일 객체를 반환하는 메서드로 나뉜다.
- `Field lookup`: `get()`, `filter()`, `exclude()` 에 넣을 수 있는 다양한 조건



## CRUD

- Create, Read, Update, Delete를 일컫는 말
- 대부분의 소프트웨어가 가지는 기본적인 데이터 처리 기능



## django admin site

- `admin.py`에서 관리자 페이지를 관리

  ```python
  from django.contrib import admin
  from .models import Article
  
  # Register your models here.
  class ArticleAdmin(admin.ModelAdmin):
      list_display = ('pk', 'title', 'content', 'created_at', 'updated_at')
  
  
  
  admin.site.register(Article, ArticleAdmin)    # admin site에 register 하겠다.
  ```



## form

- app 폴더에 forms.py파일을 만들어서 사용한다.
- models.py에서 데이터베이스 구조를 만들었다면 forms.py에서는 사용자에게 받을 데이터 폼을 만든다.
- [django form field](https://docs.djangoproject.com/en/3.1/ref/forms/fields/)

```python
from django import forms

class ArticleForm(forms.Form):
    title = forms.CharField()
    content = forms.CharField()
    yesorno = forms.BooleanField()
    due_date = forms.DateTimeField()
```



## view decorators

- 어떤 함수에 기능을 추가하고 싶을 떄, 함수를 수정하지 않고 기능을 연장해주는 함수
- [django view decorators](https://docs.djangoproject.com/en/3.1/topics/http/decorators/)
- GET방식이면 `@require_safe`, POST방식이면 `@require_POST`를 아니면 `@require_http_methods(['GET', 'POST'])`처럼 원하는 방식을 적어서 뷰함수 바로 위에 작성



## static

- 개발자가 만들어 놓은 img, css, js 파일 등 정적인 파일들을 한 곳에 모아서 관리
- STATIC_ROOT
  
  - 실제 배포할 때 필요
- STATIC_URL
  
  - static태그가 생성하는 url의 기본값
- STATICFILES_DIRS
  - settings.py에 static폴더 경로를 추가해 주어야 한다.(templates 폴더 경로를 추가하듯이 앱폴더를 제외한 곳에 있는 static폴더 경로만 추가하면 된다.)
  
  ```python
    STATIC_URL = '/static/'
    STATICFILES_DIRS = [BASE_DIR / 'pinterest' / 'static',]
  ```
  
    
  
- static 태그를 사용하려면 맨 위에서 `{% load static %}`로 로드해야 한다.



## media

- 사용자가 웹에서 입력한 파일들을 관리

- settings.py 맨 아래에 코드를 추가해야한다.

  ```python
  MEDIA_ROOT = BASE_DIR / 'media'
  MEDIA_URL = '/media/'
  ```

  

## Authentication System

- login, logout

- 회원가입(`UserCreationForm`), 로그인(`AuthenticationForm`), 회원정보수정(`UserChangeForm`)

- `from django.contrib.auth.decorators import login_required`

  - 비로그인일 때에 로그인 페이지로 이동시켜준다.

  ### 1. Login

  - `login()`
  - request객체과 user객체를 통해 로그인 진행
  - Django의 session framework를 통해 id를 세션에 저장

  - 세션을 Create하는 로직과 같다.

  

  ### 2. Logout

  - `logout()`
  - request 객체를 받으며 return이 없다.
  - DB의 세션 데이터를 삭제하고 클라이언트 쿠키에서도 `sessionid`를 삭제
  - 로그아웃은 세션을 Delete하는 로직과 같다.

  

  ### 3. 회원정보수정

  - `class AbstractUser`을 상속받아 form을 만든다.
  - `get_user_model()` method
    - 현재 프로젝트에서 활성화된 user model을 반한
    - 커스텀한 user model이 있을 경우는 커스텀 user model, 그렇지 않으면 User를 참조

  

  ### 4. 비밀번호 변경

  - `PasswordChangeForm` 사용
  - `from django.contrib.auth import update_session_auth_hash`
    - `update_session_auth_hash(request, form.user)`
    - 비밀번호 변경 시 세션의 값은 그대로 남게되어 로그인이 풀리게 된다. 위의 함수를 사용해서 세션의 해쉬값을 갱신해주어서 로그인 상태가 유지되게 해주어야 한다.



## HTTP

- 비연결지향: 서버는 응답 후 접속을 끊음
- 무상태: 상태를 저장하지 않음



## Cookie

- 세션 관리
  - 로그인, 아이디 자동완성, 공지 하루 안보기, 팝업체크, 장바구니
- 개인화
  - 사용자 선호, 테마 등 세팅
- 트래킹
  - 사용자 행동을 기록, 분석





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

9. `models.py` 작성

   ```python
   from django.db import models
   
   # Create your models here.
   class Article(models.Model):	# 클래스 이름은 app이름의 단수형으로!!
       title = models.CharField(max_length=10)
       content = models.TextField()
       created_at = models.DateTimeField(auto_now_add=True)
       updated_at = models.DateTimeField(auto_now=True)
   ```

10. `python manage.py makemigrations` 마이그레이션 생성

11. `python manage.py migrate` 마이그레이트

12. `python manage.py createsuperuser`로 관리자 계정 생성

13. `admin.py`에서 관리자 페이지 관리

    ```python
    from django.contrib import admin
    from .models import Article
    
    # Register your models here.
    class ArticleAdmin(admin.ModelAdmin):
        list_display = ('pk', 'title', 'content', 'created_at', 'updated_at')
    
    
    
    admin.site.register(Article, ArticleAdmin)    # admin site에 register 하겠다.
    ```

