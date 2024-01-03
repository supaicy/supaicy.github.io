---
title: Hyperlink
author: supaicy
categories: [Web, HTML]
tags: [web,html,hyperlink,css,head,body]
---

### Hyperlink

- 같은 문서 내의 요소의 위치로 이동
- 링크할 요소에 id 속성을 삽입하고 TAG로 연결
- 특정 페이지의 특정 위치로 이동

**예제 코드**<br>
  이상하게 나오면 알아서 조정 해보셈
```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      div{
          border-width: 1px;
          width: 200px;
          height: 200px;
          font-size: 20pt;
          vertical-align: baseline;
          line-height: 200px;
          text-align: center;
      }

      div#top_area{
          background-color: burlywood;
          margin-bottom: 2000px;
      }

      div#bottom_area{
          background-color: royalblue;
          color: white;
      }
    </style>
  </head>
  <body>
    <div id="top_area" >
      top area
      <a href="#bottom_area">bottom 이동</a>
    </div>
    <div id="bottom_area">
      bottom area <a href="#top_area">top 이동</a>
    </div>
  </body>
</html>
```

**각종 링크**
```html
<p><img src="이미지 파일 경로" alt="대체용 텍스트" /></p>
<p><img src="https://i.pinimg.com/474x/cb/da/73/cbda73c4e8117c1e7154986ec2198569.jpg" alt="랜디 로즈" /></p>

<!-- 이미지 크기 조정 -->
<p><img src="경로" alt="이미지가 없을시 대체 텍스트" height="원하는 사이즈" width="원하는 사이즈"></p>

```

**Web에서 자주 사용됨** 
- GIF
- JPG/JPEG
- PNG

