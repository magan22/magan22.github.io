---
title: "Django project [1] 장고 프로젝트 시작하기"
comments: true
categories:
- dev
tags:
- dev
- python
- Django
- project
last_modified_at: 2021-10-20T22:26:00+09:00
toc: true
---

# Django 프로젝트 시작

장고 프로젝트 문서를 바탕으로 튜토리얼을 통해 간단한 설문조사(polls) 어플리케이션을 만드는 과정을 따라해 보겠습니다.

Polls 어플리케이션은 크게 두 파트로 구성되어 있습니다.
* 사람들이 설문 내용을 보고 직접 투표할 수 있는 개방된 사이트
* 관리자가 설문을 하면 추가, 변경, 삭제 할 수 있는 관리용 사이트

## Django 버전 확인
프로젝트를 시작하기에 앞서 사용자 피씨에 장고가 미리 설치되어있다고 가정합니다. 
Django 버전은 쉘 프롬프트에서 다음과 같은 명령어를 사용하여 확인할 수 있습니다.
```
$ python -m django --version
3.2.8
```

장고가 설치되어 있다면 설치된 Django의 버전을 확인할 수 있고, 설치가 제대로 되지 않았다면 **No module named django**와 같은 에러가 발생합니다.

## 프로젝트 생성하기
Django 프로젝트 생성은 다음 명령어를 통해 수행할 수 있습니다.
```
$ django-admin startproject mysite
```

Django 프로젝트를 생성할 때는 프로젝트를 구성하는 <stong>데이터베이스 설정, Django를 위한 옵션들, 어플리케이션 설정</strong>과 같은 Django 인스턴스들이 생성되므로 초기설정에 유의해야 됩니다.

> __* 주석__  
> 프로젝트를 생설할 때, Python 또는 Django에서 사용 중인 이름은 피해야 됩니다. 특히, Django(django 자체와의 충돌)나 test(Python 패키지 이름중 하나) 같은 이름은 피해야 됩니다.  

이제 startproject를 통해 무엇이 생성되는지 확인해 봅시다.
```
mysite/
    manage.py
    mysite/
        __init__.py
        settings.py
        urls.py
        argi.py
        wsgi.py
```

* **mysite/**: 외부의 root 디렉터리는 생성한 프로젝트의 컨테이너입니다. 프로젝트 이름과는 다르게 디렉터리 이름이 Django에 영향을 주지는 않고, 사용자 임의로 이름을 변경할 수 있습니다.
* **manage.py**: Django 프로젝트와 다양한 방법으로 상호작용 하는 커멘트라인의 유틸리티입니다. 
* **mysite/**: 해당 디렉터리 내부에는 프로젝트를 위한 실제 Python 패키지들이 저장됩니다. 이 디렉토리 내의 이름을 사용하여 mysite.urls과 같이 프로젝트의 어디서나 Python 패키지들을 임포트할 수 있습니다.
* **mysite/__init__.py**: Python으로 하여금 이 디렉터리를 패키지처럼 다루라고 알려주는 용도의 단순한 빈 파일입니다. 
* **mysite/settings.py**: 현재 Django 프로젝트의  환경 및 구성을 저장합니다.
* **mysite/usls.py**: 현재 Django project의 URL 선언을 저장합니다. Django로 작성된 사이트의 **목차**라고 할 수 있습니다.
* **mysite/asgi.py**: 프로젝트를 제공하기 위한 ASGI 호환 웹 서버의 진입점입니다.
* **mysite/wsgi.py**: 현재 프로젝트를 서비스하기 위한 WSGI 호환 웹 서버의 진입점입니다.

## 개발서버 - 프로젝트 확인
startproject를 통해 프로젝트를 생성했으면 아래 명령어를 통해 프로젝트가 제대로 돌아가는지 확인할 수 있습니다.
```
~$ cd mysite
~/mysite$ python manage.py runserver 
```

서버가 정상적으로 구동됐다면 커맨드라인에 아래와 같은 출력을 볼 수 있습니다.
```
October 20, 2021 - 13:51:28
Django version 3.2.8, using settings 'mysite.settings'
Starting development server at http://127.0.0.1:8000/
```

runserver를 통해 Django 개발 서버를 시작했습니다. 개발 서버는 순수 Python으로 작성된 경량 웹 서버입니다. Django에 포함되어 있어 아무 설정 없이 바로 개발 할 수 있습니다.

> __* 주석__  
> **절때로** 개발 서버를 운영 환경에서 사용하지 마십시요. 개발 서버는 오직 개발 목적으로만 사용해야 됩니다.  

이제 서버가 동작하기 시작했으니, 자신의 웹 브라우저에서 http://127.0.0.1:8000/ 을 통해 접속할 수 있습니다. 
<img src="/assets/img/django_start_page.png" alt="django start page">

> __* 포트 변경하기__  
> 기본적으로 **runserver** 명령은 내부 IP의 8000번 포트로 개발 서버를 띄움니다. 만약 이 서버의 포트를 변경하고 싶다면, 커멘드라인에서 인수를 전달해주면 됩니다.  
> 예를 들어 이 명령어는 포트를 8080으로 서버를 시작할 것입니다.  
> ```
> $ python manage.py runserver 8080
> ```
> 서버의 IP를 변경하려면 포트와 함께 전달하면 됩니다. 예를 들어 사용 가능한 모든 공용 IP를 청취할려면 아래 명령어를 사용하면 됩니다.  
> ```
> $ python manage.py runserver 0:8000
> ```

# 설문조사 앱 만들기
이제, 애플리케이션을 만들기 위한 프로젝트 작업 환경이 만들어졌습니다.

> __* 프로젝트와 앱의 차이점__  
> 앱은 웹로그 시스템, 공공 기록 데이터베이스 또는 소규모 설문조사 앱과 같은 특정 **기능**을 수행하는 웹 애플리케이션입니다.  
> 이와 달리 프로젝트는 특정 웹사이트에 대한 구성 및 앱 모음입니다.  
> 프로젝트에는 여러 앱이 포함될 수 있으며 앱은 여러 프로젝트에 있을 수 있습니다.  

앱을 생성하기 위해 manage.py가 존재하는 디렉토리에서 다음의 명령을 입력해봅시다.
```
$ python manage.py startapp polls
```

명령어를 입력하면 아마 다음과 같은 디렉토리 구조로 polls 앱이 만들어집니다.
```
polls/
    __init__.py
    admin.py
    apps.py
    migrations/
        __init__.py
    models.py
    tests.py
    views.py
```

## 첫 번째 뷰 작성하기
첫 번째 뷰를 작성해봅시다. **polls/view.py** 를 열어 다음과 같은 파이썬 코드를 입력합니다.

```python
# polls/views.py

from django.http import HttpResponse

def index(request):
    return HttpReponse("Hello, word. You're at the polls index.")
```

이 뷰는 Django 에서 가장 간단한 형태의 1페이지 뷰입니다. 뷰를 호출하려면 이와 연결된 URL이 있어야 하는데, 이를 위해 URLconf가 사용됩니다.

polls 디렉터리에서 URLconf를 생성하려면, **urls.py**라는 파일을 생성해야 합니다. polls/urls.py 파일을 생성한 후 다음 파이썬 코드를 입력합니다.

```python
# polls/urls.py

from django.urls import path

from . import views

urlpatterns = [
    path('', views.index, name='index'),
]
```

다음 단계에서는 최상위 URLconf에서 **polls.urls** 모듈을 바라보게 설정합니다. 
**mysite/urls.py** 파일을 열고, **django.urls.include**를 import 한 후에 **urlpatterns** 리스트에 **include()** 함수를 다음과 같이 후가합니다.

```python
# mysite/urls.py

from django.contrib import admin
from django.urls import include, path

urlpatterns = [
    path('polls/', include('polls.urls')),
    path('admin/', admin.site.urls),
]
```

* __include()__: 다른 URLconf들을 참조할 수 있도록 도와줍니다. Django가 함수 include()를 만나게 되면, URL의 그 시점까지 일치하는 부분을 잘라내고, 남은 문자열 부분을 후속 처리를 위해 include된 URLconf로 전달합니다.

polls 앱에 그 자체의 URLconf(**polls/urls.py**)가 존재하는 'polls/'이 아닌 다른 경로를 root URLconf에 연결하더라도 앱을 여전히 잘 동작할 것입니다.

> * __언제 include()를 사용하나요?__  
> **admin.site.urls**를 제외한 다른 URL 패턴을 포함할 때마다 **include()**를 사용해야 합니다.  

이제 **index** 뷰가 URLconf에 연결됐습니다. 잘 작동하는지 확인하기 위해 서버 실행 후 http://127.0.0.1:8000/polls/ 에 접속해보세요.

```
$ python manage.py runserver
```

본 내용은 **[장고 프로젝트 문서](https://docs.djangoproject.com)** 를 기반으로 작성됐습니다.