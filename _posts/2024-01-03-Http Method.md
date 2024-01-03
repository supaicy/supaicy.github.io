---
title: HTTP Method 종류
author: supaicy
categories: [ Web, HTML ]
tags: [ HTTP,Web,Http method,get,post,request,response ]
---

### HTTP Method 종류

| method  | 설명                                                  |
|:--------|:----------------------------------------------------|
| GET     | 특정 리소스의 표시를 요청, GET은 데이터를 받기만 함                     |
| HEAD    | GET과 같은 응답을 함, 그러나 본문을 포함하지 않음                      |
| POST    | 특정 리소스에 엔티티를 제출할 때 쓰임, 서버의 변화나 부작용을 일으킴(서버 여드름 발생자) |
| PUT     | 목적 리소스의 모든 현재 표시를 요청 payload로 바꿈                    |
| DELETE  | 특정 리소스 삭제                                           |
| OPTIONS | 목적 리소스의 통신을 설정                                      |
| PATCH   | 리소스의 부분만을 수정                                        |
| CONNECT | 목적 리소스로 식별되는 서버로의 터널을 연결함                           |
| TRACE   | 목적 리소스의 경로에서 메시지 Loop-Back 테스트 함                    |

**GET test**
- https://httpbin.org/get?no=1&id=marco&age=30

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
</head>
<body>
<form method="get" action="https://httpbin.org/get">
  <p><input type="number" name="no" placeholder="no"></p>
  <p><input type="text" name="id" placeholder="id"></p>
  <p><input type="number" name="age" placeholder="age"></p>
  <p>
    <button type="submit">submit</button>
  </p>
</form>
</body>
</html>
```

**POST test**
- https://httpbin.org/get?no=1&id=marco&age=30

GET <-> POST 의 차이를 잘 알아두셈 <br>
url에 정보가 노출되냐 아니냐 잘 보셈
