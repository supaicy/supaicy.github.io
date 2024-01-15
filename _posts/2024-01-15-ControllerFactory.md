---
title: ControllerFactory
author: supaicy
categories: [Servlet, Jsp]
tags: [Jsp, Servlet, Java, DB, Server]
---

# ControllerFactory
### for what? -> HTTP 요청에 따라 적절한 컨트롤러 객체를 찾아 매핑

### 주요 개념
1. Java Reflection API
   - Reflection API를 사용하면 실행시간(runtime)에 클래스의 정보를 조사하고, 인스턴스를 생성하거나 메서드를 호출 할 수 있다.
   - Class.forName(String className) 메서드로 클래스 객체를 얻고, newInstance()로 인스턴스를 생성
2. Controller Mapping
   - 각 컨트롤러 클래스에는 특정 HTTP 요청을 처리하는 데 사용되는 @RequestMapping 어노테이션이 있음
   - @RequestMapping 의 value 속성은 해당 컨트롤러가 처리할 경로를 나타냄
   - ex: @RequestMapping(method = RequestMapping.Method.GET, value = {"index.do", "/main.do"})
3. ConcurrentHashMap
   - ConcurrentHashMap은 스레드 안전한 HashMap의 변형으로, 복수의 쓰레드 환경에서 효율적으로 작동
   - put(String key, Object value) 메서드를 사용하여 컨트롤러의 인스턴스를 저장
4. ServletContext
   - ServletContext는 웹 어플리케이션의 정보를 담고있는 객체로, 전체 어플리케이션에서 공유되는 정보를 저장할 때 사용
   - setAttribute(String name, Object obj) 메서드를 사용해서 ControllerFactory 인스턴스를 저장할 수 있음

```java
// ControllerFactory 초기화(initialize 메서드)
for (Class<?> controllerClass : c) {
    if (BaseController.class.isAssignableFrom(controllerClass)) {
        BaseController controller = (BaseController) controllerClass.getDeclaredConstructor().newInstance();
        RequestMapping mapping = controllerClass.getAnnotation(RequestMapping.class);
        String[] paths = mapping.value();
        for (String path : paths) {
            String key = mapping.method() + "-" + path;
            beanMap.put(key, controller);
        }
    }
}

// ServletContext에 ControllerFactory 추가
ctx.setAttribute(CONTEXT_CONTROLLER_FACTORY_NAME, this);

// Controller 객체 반환(getBean, getController 메서드)
private Object getBean(String key){
  return beanMap.get(key);
}
public Object getController(HttpServletRequest request){
  String key = getKey(request.getMethod(), request.getServletPath());
  return getBean(key);
}

// Key 생성(getKey 메서드)
private String getKey(String method, String path){
  return method.toUpperCase() + "-" + path;
}
```


이 예시에서 `initialize` 메서드는 주어진 컨트롤러 클래스들의 인스턴스를 생성하고, 각 인스턴스를 해당 HTTP 메서드와 경로에 매핑합니다. 
Reflection API를 사용하여 `BaseController`를 구현한 클래스의 인스턴스를 생성하고, `
@RequestMapping` 애노테이션을 통해 얻은 정보를 기반으로 `beanMap`에 저장합니다.

`getController` 메서드는 `HttpServletRequest`를 통해 받은 HTTP 메서드와 경로 정보를 사용하여 적절한 컨트롤러 객체를 반환합니다. 
이 과정에서 `getKey` 메서드를 사용하여 `beanMap`에서 사용할 키를 생성합니다.

`ServletContext`에 `ControllerFactory` 객체를 저장하는 것은 애플리케이션의 다른 부분에서 `ControllerFactory`에 접근할 수 있게 하기 위함입니다.

이러한 구현은 Java 웹 애플리케이션에서 요청을 처리하는 컨트롤러를 동적으로 관리하는 데 유용합니다. 
Reflection과 애노테이션 처리를 통해 유연하고 확장 가능한 방식으로 컨트롤러를 관리할 수 있습니다.

