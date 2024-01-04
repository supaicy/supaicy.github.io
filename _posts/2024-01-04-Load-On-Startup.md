---
title: Servlet의 문제점
author: supaicy
categories: [JSP, Servlet]
tags: [JSP,Servlet,Java,Web]
---

## Load-On-Startup

### Servlet 의 문제점
- Servlet 은 브라우저 최초 요청시 init() 메서드(초기화) 과정을 통해서 메모리에 로드되어 기능수행을 함
  - 최초요청에 대해서 실행시간이 길어질 수 있는 단점이 있음.
  - 지연 초기화(Lazy initialization)
### load-on-startup 특징
- 0 보다 크면 톰캣 컨테이너가 미리 서블릿을 초기화 함
- 숫자의 순서에 의해 초기화 됨

> Client 가 필요한 Servlet Instance 를 메모리에 로드되면 실행이 길어지니까 
> 우선순위를 정하는 load-on-startup 으로 미리 인스턴스를 톰캣이 만들어서 가지고 있다!!! 를 알아라. 맞노?
---
### Servlet Class 계층 알기
---
### Generic Servlet ?
- HTTP 이오의 프로토콜을 위한 범용 Servlet
  - HTTP 프로토콜 -> HttpServlet 확장
  - HTTP 이외의 프로토콜 -> GenericServlet 확장
- 추상 클래스 로 기본 구현 제공
  - Servlet Interface 에서 service() 메서드를 제외한 나머지 메서드들에 대한 기본 구현

---

## HttpServlet.service() METHOD
- 내부적으로 METHOD 에 의해서 doXXXX METHOD 를 호출 함
```java
protected void service(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
    String method = req.getMethod();
    long lastModified;
  
  
  
    if (method.equals("GET")) {
        lastModified = this.getLastModified(req);
        if (lastModified == -1L) {
            this.doGet(req, resp);
        } else {
            long ifModifiedSince = req.getDateHeader("If-Modified-Since");
            if (ifModifiedSince < lastModified) {
                this.maybeSetLastModified(resp, lastModified);
                this.doGet(req, resp);
            } else {
                resp.setStatus(304);
            }
        }
    } else if (method.equals("HEAD")) {
        lastModified = this.getLastModified(req);
        this.maybeSetLastModified(resp, lastModified);
        this.doHead(req, resp);
    } else if (method.equals("POST")) {
        this.doPost(req, resp);
    } else if (method.equals("PUT")) {
        this.doPut(req, resp);
    } else if (method.equals("DELETE")) {
        this.doDelete(req, resp);
    } else if (method.equals("OPTIONS")) {
        this.doOptions(req, resp);
    } else if (method.equals("TRACE")) {
        this.doTrace(req, resp);
    } else {
        String errMsg = lStrings.getString("http.method_not_implemented");
        Object[] errArgs = new Object[]{method};
        errMsg = MessageFormat.format(errMsg, errArgs);
        resp.sendError(501, errMsg);
    }

}
```

## HttpServlet.doXXX() method
- doGet,doPost,doPut,doDelete 등 메서드에서 해당 HTTP 메서드를 지원하지 않을 때 클라이언트에게 에러 응답을 보냄
```java
protected void doGet(HttpServletRequest req, HttpServletResponse resp) /* ... */ {
    // ...
    resp.sendError(getMethodNotSupportedCode(protocol), msg);
}

protected void doPost(HttpServletRequest req, HttpServletResponse resp) /* ... */ {
    // ...
    resp.sendError(getMethodNotSupportedCode(protocol), msg);
}

protected void doPut(HttpServletRequest req, HttpServletResponse resp) /* ... */ {
    // ...
    resp.sendError(getMethodNotSupportedCode(protocol), msg);
}

protected void doDelete(HttpServletRequest req, HttpServletResponse resp) /* ... */ {
    // ...
    resp.sendError(getMethodNotSupportedCode(protocol), msg);
}
```

