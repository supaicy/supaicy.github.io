---
title: context-param의 url 정보를 다른 Servlet에서 조회하기
author: supaicy
categories: [JSP, Servlet]
tags: [JSP,Servlet,Java,Server,Http,Web]
---

## context-param의 url 정보를 다른 Servlet에서 조회하기

```xml
<context-param>
    <param-name>url</param-name>
    <param-value>https://nhnacademy.com/</param-value>
</context-param>
```

```java
    Stirng url = getServletContext().getInitParameter("url");
```
