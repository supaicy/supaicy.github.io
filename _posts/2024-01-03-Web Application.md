---
title: 웹 어플리케이션 이란?
author: supaicy
categories: [JSP, Servlet]
tags: [jsp,servlet,서버,web,기초지식]
---

Web Application이란?
==================

Client - Server Architecture
----------------------------

![Client server model](https://upload.wikimedia.org/wikipedia/commons/c/c9/Client-server-model.svg)

### Server

* Server는 Client요청한 서비스를 제공

### Client

* Client는 서비스를 사용하는 사용자 혹은 사용자의 단말기

### Server - Client(예)

* 메일 서버

* 파일 서버

  * 파일 서버는 중앙에 위치하면 중앙에 저장된 파일은 여러 사용자가 접근할 수 있습니다. ( ex. 구글드라이브, 두레이 드라이브)


* 웹서버

  * 인터넷을 통해 다양한 웹사이트를 제공

Web Application Architecture
----------------------------

### Web Application Architecture란?

* 애플리케이션 구성 요소, 미들웨어 시스템, 사용자 인터페이스 및 데이터베이스 간의 상호 작용을 표시하는 "골격" 또는 레이아웃을 의미합니다. 이러한 상호 작용을 통해 여러 응용 프로그램이 동시에 함께 작동할 수
  있습니다.

* 데이터가 HTTP를 통해 전달하는 방식을 정의하고 클라이언트와 BackEnd Server(API Server)가 서로 통신할 수 있도록 합니다.

* 모든 사용자의 요청에 대한 유효성 검증

* 권한 기반의 접근(인증)

### 구성요소

* 웹 브라우저

  * HTML 문서

  * 이미지 파일 (jpg, png, gif..)

  * javascript ( 객체 )


* 웹 서버

  * apache

    * [https://httpd.apache.org](https://httpd.apache.org/)

    * nginx

      * [https://www.nginx.com](https://www.nginx.com/)

* 데이터베이스 서버

  * mysql

  * mariadb

  * oracle

  * ms-sql

Client - Server Architecture vs Web Application Architecture
------------------------------------------------------------

|      | Client - Server Application | Web Application |
|:-----|:----------------------------|:----------------|
| 아키텍쳐 | **2 tire**                  | **multi tire**  |
|상호작용 | 사용자의 인터페이스 또는 애플리케이션 | 웹 브라우저 |
|실행 |애플리케이션 사전 설치 |웹 브라우저에서 직접 실행|
|쿠키|none|required|
|보안|상대적으로 사용자가 적기 때문에 위험이 적습니다.|사용자 수가 많을수록 상대적으로 높은 위험
|접근|제한적|anywhare

Reference
---------

* [위키, 클라이언트-서버 모델](https://ko.wikipedia.org/wiki/%ED%81%B4%EB%9D%BC%EC%9D%B4%EC%96%B8%ED%8A%B8_%EC%84%9C%EB%B2%84_%EB%AA%A8%EB%8D%B8)
