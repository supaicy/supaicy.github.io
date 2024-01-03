---
title: CSS Selector
author: supaicy
categories: [ CSS, Selector ]
tags: [ CSS,Selector,HTML,속성,id ]
---

## Selector?

- CSS를 적용할 요소를 지칭

## Tag Selector

```html

<style>
  p {
    color: red;
  }
</style>

<p>Hello World!</p>
<p id="hello">Hello World!</p>
<p class="hello">Hello World!</p>
<input type="button" value="Hello World!">
```

위 코드에 대한 결과는 아래와 같다.

<style>
p {
  color: red;
  }
</style>

  <p>Hello World!</p>
  <p id="hello">Hello World!</p>
  <p class="hello">Hello World!</p>
  <input type="button" value="Hello World!">

---

## Id Selector

- Id 값 앞에 #을 붙여서 선택
- 우선순위 때문에 쓰지 않는 것이 좋음

```html

<style>
  #hello {
    color: blue;
  }
</style>

<p>안녕하세요.</p>
<p id="hello">안녕하세요.</p>
<p class="hello">안녕하세요.</p>
<input type="button" value="안녕하세요">
```

위 코드에 대한 결과는 다음과 같다.
<style>
    #hello{
        color: blue;
    }
</style>

<p>안녕하세요.</p>
<p id="hello">안녕하세요.</p>
<p class="hello">안녕하세요.</p>
<input type="button" value="안녕하세요">

---

## Class Selector

- Class 앞에 '.'을 붙여서 선택
- 가장 많이 씀

```html

<style>
  .hello {
    color: green;
  }
</style>
<p>안녕하세요.</p>
<p id="hello">안녕하세요.</p>
<p class="hello">안녕하세요.</p>
<input type="button" value="안녕하세요">
```

<style>
  .hello{
    color: green;
  }
</style>
<p>안녕하세요.</p>
<p id="hello">안녕하세요.</p>
<p class="hello">안녕하세요.</p>
<input type="button" value="안녕하세요">

## CSS 속성 Selector

- []안에 속성명="값"
- []안에 속성명 형태로도 사용 가능

```html

<style>
  [type="button"] {
    color: green;
  }
</style>

<p>안녕하세요.</p>
<p id="hello">안녕하세요.</p>
<p class="hello">안녕하세요.</p>
<input type="button" value="안녕하세요">
```

<style>
    [type="button"]{
        color: green;
    }
</style>

<p>안녕하세요.</p>
<p id="hello">안녕하세요.</p>
<p class="hello">안녕하세요.</p>
<input type="button" value="안녕하세요">

---

## 부모 자식 관계 Selector

- HTML 문서는 부모 자식 관계가 있음
- header 와 h1,h2는 부모-자식 관계
- h1 h2는 형제 관계

```html

<header>
  <h1>첫째</h1>
  <h2>둘째</h2>
</header>
```

## 후손 Selector

- 부모와 후손을 선택시 공백 사용
- 여러 개의 Selector를 적용할 때 콤마로 구분

```html

<style>
  header h1 {
    color: red;
  }

  header h1, header h2 {
    color: red;
  }
</style>
```

## 자식 Selector

```html

<style>
  header > h1 {
    color: red;
  }

  header > h1, header > h2 {
    color: red;
  }
</style>
```

## 바로 뒤 형제 Selector

```html

<style>
  h1 + p {
    color: red;
  }
</style>
```

## 뒤에 오는 모든 형제 Selector

- 뒤에 오는 모든 형제 선택시 ~(물결) 사용

```html

<style>
  h ~ p {
    color: red;
  }
</style>
```

## 전체 Selector

- 모든 Element 선택시 * 사용
- 성능에 좋지 않음, 남발하지 마셈

```html

<style>
  header * {
    color: red;
  }

  or
  header p {
    color: red;
  }

  or
  * {
    color: red;
  }

</style>
```

## 유사 Class Selector

- Element 가 특별한 상태일 때
- 마우스가 올라가 있거나, 선택되어 있거나..
- (구체적) 마우스가 올라가면 색이 변경됨

```html

<style>
  header > p:hover {
    color: red;
  }
</style>
```

| 유사 클래스 셀렉터               | 설명                |
|:-------------------------|:------------------|
| hover                    | 마우스 오버            |
| active                   | 선택된 상태            |
| focus                    | 포커스가 있을 때         |
| checked                  | 체크 상태일 때          |
| disabled                 | 사용 불가능일 때         |
| first-child, :last-child | 해당 요소 중 첫 번째, 마지막 |
| nth-child(n)             | 해당 요소 중 n 번째      |
| nth-of-type(n)           | 해당 요소 중 n 번째 엘리먼트 |
| not(셀렉터)                 | 해당 요소가 아닌 것들      |

## 유사 Element Selector
- Element 내용의 앞과 뒤에 내용을 삽입
- 가상요소이므로 블록 지정이 안됨
- 존재하는 Element가 없는 가상의 요소를 선택
- 유사 클래스는 상태를 선택하고, 유사 Element는 선택적인 부분을 선택
- 주로 문자열을 지정하는 content 속성과 함께 사용
- 콜론 두개와 함께 사용

```html

<style>
  div::before {
    content: "마블's";
    color: red;
    margin-right: 10px;
  }

  div::after {
    content: "시리즈";
    color: blue;
    margin-left: 10px;
  }
</style>

<div>캡틴 아메리카</div>
```

<style>
    div::before{
        content: "마블's";
        color:red;
        margin-right:10px;
    }
    div::after{
        content:"시리즈";
        color:blue;
        margin-left:10px;
    }
</style>

<div>캡틴 아메리카</div>

## CSS 우선 순위
- 하나의 Element에 여러 가지 Selector로 선택 가능
- 각 Selector 로 지정한 스타일 중 우선순위에 따라 적용
- 클래스 셀렉터 > 태그 셀렉터
- 셀렉터 우선순위 동등: 나중에 선언된 스타일 적용

```html
<style>
                main h1{
                color:yellow;
            }
            .title{
                color:red;
            }
            .title{
                color:blue;
            }
            .title{
                color:green;
            }
</style>

<main>
    <h1 class="title">오드리 헵번</h1>
</main>

```
<style>
            main h1{
                color:yellow;
            }
            .title{
                color:red;
            }
            .title{
                color:blue;
            }
            .title{
                color:green;
            }
</style>

<main>
    <h1 class="title">오드리 헵번</h1>
</main>

## ID Selector를 적용한다면?

<style> 
    #title{
        color:aqua;
    }
    main h1{
        color: yellow;
    }
    .title{
        color: red;
    }
    .title{
        color: blue;
    }
    .title{
        color: green;
    }
</style>







