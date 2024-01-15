---
title: Java Logging, 자바 로그
author: supaicy
categories: [Java, Log]
tags: [Java, Log,Logging,자바,로그]
---

## Java Logging
---
### Log Level
- 6 fatal : error 보다 더 심각한 오류를 출력 
- 5 error : 오류 출력 
- 4 warn : 경고 정보를 출력 
- 3 info : 일반적인 정보 출력 
- 2 debug : 디버깅 목적으로 사용 
- 1 trace : debug 보다 더 상세한 정보를 나타낼 경우에 사용.

#### 일반적으로 개발시에 debug 사용
#### 서버에 배포되었을 때는 ERROR of WARN 사용
- 다만 서버에서 디버길 용도로 info, debug 등등 상황에 맞게 일시적으로 설정해서 사용할 수 있음.
- 운영서버에서 디버깅 할 수 있는 유일한 수단
