---
title: "Django - path()"
comments: true
categories:
- dev
tags:
- dev
- python
- Django
- project
last_modified_at: 2021-10-21T20:30:00+09:00
toc: true
---

URLconf에서 사용하는 함수인 path()에는 2개의 필수 인수인 route와 view가 있고, 2개의 선택 가능한 인수로 kwargs와 name이 있습니다. 이 인수들이 무엇인지 살펴보는 것은 의미가 있습니다.

# paht()

## path() 인수: route
**route**는  "/"와 같이 URL 패턴을 가진 문자열입니다. 요청이 처리될 때 Django는 urls.py의 urlpatterns 리스트에서 첫 번째 패턴부터 시작하여, 일치하는 패턴을 찾을 때까지 요청된 URL을 각 패턴과 순서대로  비교합니다.

패턴들은 GET이나 POST 의 매개변수들, 혹은 도메인 이름은 검색하지 않습니다. 예를 들어 **https://example.com/myapp/page=3**이 요청된 경우, URLconf는 최상위 도메인과 쿼리스트링을 제외한 제외한 myapp/부분만 바라보게 됩니다.

## path() 인수: view
Django에서 일치하는 패턴을 찾으면, HttpRequest 객체를 첫번째 인수로 하고, 경로로부터 <챕처된> 값을 키워드 인수로하여 특정한 view 함수를 호출합니다.

## path() 인수: kwargs
**kwargs**로 전달된 임의의 키워드 인수들은 목표한 view에 딕셔너리 형식으로 전달됩니다.

## path() 인수: name
URL에 이름을 지으면, 템플릿을 포함한 Django 어디에서나 명확하게 참조할 수 있습니다. name 인수는 단 하나의 파일만 수정해도 project 내의 모든 URL 패턴을 바꿀 수 있도록 도와줍니다.

본 내용은 **[장고 프로젝트 문서](https://docs.djangoproject.com)** 를 기반으로 작성됐습니다.