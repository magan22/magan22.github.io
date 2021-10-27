---
title: "Django project [2] 데이터베이스"
comments: true
categories:
- dev
tags:
- dev
- python
- Django
- project
- database
last_modified_at: 2021-10-21T23:10:00+09:00
toc: true
---


# 데이터 베이스 설치
**mysite/settings.py** 파일은 Django 설정을 모듈 변수로 표현한 보통의 Python 오듈입니다.

데이터베이스 설정은 이 **settings.py** 폴더에서 하는데 기본적으로는 파이썬에서 제공하는 SQLite로 설정이 돼있습니다.

```python
# mysite/settings.py

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': BASE_DIR / 'db.sqlite3',
    }
}
```

데이터베이스를 한번 경험해 보고 싶다면, SQLite가 가장 간단한 방법이지만 실제 프로젝트를 시작할 때는 번거로움을 덜기 위해 mysql과 같은 확장성 있는 데이터베이스를 설치하는 편이 좋습니다.

다른 데이터베이스를 사용해보고 싶다면, 적절한 데이터베이스 바인딩을 설치하고 데이터베이스 연결 설정과 맞겠끔 위 **settings.py** 파일의 **ENGINE** 항목을 변경해주면 됩니다.

데이터베이스 테이블을 만들기 위해 아래 명령어를 입력합니다.

```sh
$ python manage.py migrate
```

마이그레이션 명령은 **mysite/settings.py** 파일의 INSTALLED_APPS 설정을 살펴보고 파일의 데이터베이스 설정과, 앱과 함께 제공되는 데이터베이스 마이그레이션에 따라 데이터베이스 테이블을 생성합니다.

본 내용은 **[장고 프로젝트 문서](https://docs.djangoproject.com)**를 기반으로 작성됐습니다.