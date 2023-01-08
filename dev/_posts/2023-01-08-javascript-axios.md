---
title:  "[axios] http 서버 통신 axios 사용하기(basic) "
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
  - axios
---

javascript에서 네트워크 통신을 하기 위해 주로 fetch 함수를 많이 사용한다.    
그런데 이보다 더 편하게 네트워크 통신을 편하게 도와 주는 외부 라이브러리가 있다.
바로 axios.

## axios 사용하기

기본적으로 axios는 비동기 처리를 하는 promise 객체를 반환한다.
아래와 같이 axios.html 으로 특정 url에 aixos.get을 사용한 통신 결과를 console로 찍어볼 수 있다.  

```
<html>
  <head>
    <script src="https://cdn.jsdelivr.net/npm/axios/dist/axios.min.js"></script>
    <script>
      axios
        .get("https://jsonplaceholder.typicode.com/todos/1")
        .then(function (result) {
          console.log("통신 결과 : ", result.status);
          console.log("data : ", result.data);
        })
        .catch(function (error) {
          console.log("에러발생 : ", error);
        });
      console.log("바로 실행");
    </script>
  </head>
  <body></body>
</html>
```

![img.png](/assets/images/img.png)

## postman으로 샘플 Mock Server 생성

![img_1.png](/assets/images/img_1.png)

postman을 사용해 샘플 데이터를 가져올 Mock Server를 생성.  
이때 생성되는 INITIAL url 을 가지고 네트워크 통신 테스트를 할 수 있다.   
( https://1b6a571f-bb08-44ad-8ff3-3bd16418d84c.mock.pstmn.io )
  
주의 !! 
포스트맨에서 제공해주는 Mock Server는 요청 횟수가 1분 당 60회로 제한되어 있어서,  
그 이상으로 보내게 되면 429 error 발생하면서 몇 시간 정도 이용 제한이 생긴다.  
  
![img_2.png](/assets/images/img_2.png)
Mock Server 로부터 받은 결과를 html 에서 호출하면 아래와 같이 JSON 결과 데이터를 가져옴.  

![img_3.png](/assets/images/img_3.png)

  