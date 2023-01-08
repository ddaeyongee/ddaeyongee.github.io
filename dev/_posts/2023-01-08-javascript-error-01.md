---
title:  "[javascript] Uncaught TypeError: Cannot set properties of null (setting 'innerHTML') 오류 "
date: 2023-01-08 18:15:00 +0900
last_modified_at: 2023-01-08 18:15:00 +0900
header:
  teaser: /assets/images/unsplash/github-842ofHC6MaI.jpg
  overlay_image: /assets/images/unsplash/github-842ofHC6MaI.jpg
  overlay_filter: 0.5
  caption: "Photo credit: [**Unsplash**](https://unsplash.com/photos/842ofHC6MaI)"

toc: true
toc_sticky: true

tags:
  - javascript
  - html
---

Uncaught TypeError: Cannot set properties of null (setting 'innerHTML')


위와 같이 script 태그를 활용한 innerHTML를 사용하여 필드 호출시 아래와 같은 null 오류가 발생할 수 있다.

```
index.html?_ijt=k8ile6j503u771v0cq4cc5emet&_ij_reload=RELOAD_ON_SAVE:26 
  Uncaught TypeError: Cannot set properties of null (setting 'innerHTML')
  at index.html?_ijt=k8ile6j503u771v0cq4cc5emet&_ij_reload=RELOAD_ON_SAVE:26:57
```

브라우저가 html 리소스를 로딩할 때 위에서부터 순서대로 읽는다.
동적 데이터 처리를 위한 script 태그에서 선언한 필드가 호출하는 지점보다 위에 있는 경우 발생
```
  <script>
    document.querySelector("#product-list").innerHTML = "<p>안녕</p>";
  </script>
```

document 활용 html 호출 기능 사용시  
script 태그와 body 태그 위치를 적절하게 조정해서 극복ㄱㄱ   


