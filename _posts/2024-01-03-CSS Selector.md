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
    #hello{
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


