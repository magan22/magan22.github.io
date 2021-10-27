---
title: "Django - settings.py 살펴보기"
comments: true
categories: dev
tags:
- dev
- python
- Django
- project
toc: true
---

장고 setting.py 파일에 대애 알아봅시다.

# settings.py

**mysite/setting.py** 파일은 Django 설정을 모듈 변수로 표현한 보통의 Python 모듈입니다.

## TIME_ZONE
프로젝트 설정을 할 때 **settings.py** 파일의 **TIME_ZONE** 항목에서 시간대 설정을 할 수 있습니다.

```python
TIME_ZONE = 'UTC'
```

## INSTALLED_APPS
**settings.py** 파일의 위쪽에 있는 이 항목은 현재 Django 인스턴스에서 활성화된 모든 Django 애플리케이션들의 이름을 담고있습니다. 앱들은 다수의 프로젝트에서 사용될 수 있고, 다른 프로젝트에서 쉽게 사용될 수 있도록 패키징하여 배포할 수 있습니다.

```python
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
]
```


기본적으로는, **INSTALLED_APPS**는 Django와 함께 딸려오는 다음의 앱들을 포함합니다.

| * **[django.contrib.admin](https://docs.djangoproject.com/ko/3.2/ref/contrib/admin/#module-django.contrib.admin)** | 관리용 어드민 사이트 |
| * **[django.contrib.auth](https://docs.djangoproject.com/ko/3.2/topics/auth/#module-django.contrib.auth)** | 인증 시스템 |
| * **[django.contrib.contenttypes](https://docs.djangoproject.com/ko/3.2/ref/contrib/contenttypes/#module-django.contrib.contenttypes)** | 컨텐츠 타입을 위한 프레임워크 |
| * **[django.contrib.sessions](https://docs.djangoproject.com/ko/3.2/topics/http/sessions/#module-django.contrib.sessions)** | 세션 프레임워크 |
| * **[django.contrib.messages](https://docs.djangoproject.com/ko/3.2/ref/contrib/messages/#module-django.contrib.messages)** | 메세징 프레임워크 |
| * **[django.contrib.staticfiles](https://docs.djangoproject.com/ko/3.2/ref/contrib/staticfiles/#module-django.contrib.staticfiles)** | 정적 파일ㅇ르 관리하는 프레임워크 |

이 애플리케이션들은 일반적인 경우에 사용하기 편리하도록 기본으로 제공됩니다.

본 내용은 **[장고 프로젝트 문서](https://docs.djangoproject.com)**를 기반으로 작성됐습니다.
