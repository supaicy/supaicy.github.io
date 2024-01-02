---
title: Charset Sets & Encodings [HTML]
author: supaicy
categories: [Web, HTML]
tags: [web,html,front,ascii,uft,utf-8]
pin: true


---

### ASCII

- 7bit 인코딩
- 128개 문자열
- 영문: 52
- 숫자: 10
- 특수문자: 32
- 제어문자: 33
- 000 0000 ~ 111 1111
- 한글은 표현 불가능

### UTF-8(유니코드)

- 전세계의 모든 문자열을 하나의 코드표로 통합
- 문자를 저장하기 위해 1~4byte 까지 동적으로 사용
- 조합형 : 한글의 제적 원리에 기반하여 초성, 중성, 종성에 각각 코드를 할당하는 방식
- 완성형 : '가', '나', '다'와 같이 완성형 문자열에 할당하는 방식, 한글 표준안
- Emoji : 일본에서 시작함 ㅋ

---

> (유의사항)
>
> charset = euc-kr, 파일은 UTF-8 인코딩이면..
>
> 뷁쉣둣 같이 이상하게 나옴(님들도 아는 그거 맞음)