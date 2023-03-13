---
title:  "[React] How to use React Router "
date: 2023-03-12 12:00:00 +0900
last_modified_at: 2023-03-12 12:00:00 +0900
header:
  teaser: /assets/images/unsplash/github-842ofHC6MaI.jpg
  overlay_image: /assets/images/unsplash/github-842ofHC6MaI.jpg
  overlay_filter: 0.5
  caption: "Photo credit: [**Unsplash**](https://unsplash.com/photos/842ofHC6MaI)"

toc: true
toc_sticky: true

tags:
  - React
  - React-Router
  - router-component
---
* React Router 사용하기   
SPA 리액트 프로젝트에서 .html file 갯수는 1개 (MPA 에서는 브라우저측에서 라우팅 처리할 필요 없음)  
한 개의 웹페이지(.html) 내에서 여러 개의 페이지를 보여주기 위해서는 라우팅이 필요하다.  
리액트 자체 에는 라우팅 기능이 내장되어 있지 않아, 우리는 React Router library를 사용해 구현해야 한다.   

* React Router란? 
React JavaScript library를 위한 가볍고 완전한 기능을 갖춘 routing library 이다.  
React Router는 웹, 서버(node.js 기반) 및 React Native 등 React가 실행되는 모든 곳에서 동작한다.  

* React Router (npm v6.9.0 이상) 에서 제공하는 router-component  
BrowerRouter(used a lot)  
HashRouter(used a lot)  
MemoryRouter  
RouterProvider  
Picking a Router  
...

* BrowerRouter vs HashRouter
  참고 링크 : [https://reactrouter.com/en/main/router-components/hash-router](참고 링크 : https://reactrouter.com/en/main/router-components/hash-router)
BrowserRouter는 HTML5의 history API를 사용하여 URL을 처리한다. 
브라우저에서 페이지를 새로 고침하지 않고도 URL을 업데이트할 수 있는 기능을 제공함.
또한 서버 측에서 URL을 처리하도록 구성할 수 있으므로 사용자가 URL을 복사하여 붙여넣어도 작동한다.

반면 HashRouter는 URL의 hash 부분을 사용하여 라우팅을 처리. 
예를 들어, http://example.com/#/about와 같은 URL을 사용한다. 
이 방식은 BrowserRouter와 달리 모든 브라우저에서 지원되므로 이전 버전의 브라우저에서도 작동한다. 
URL이 약간 덜 직관적이라는 단점이 있다. 

어떤 것을 선택할 것인지는 프로젝트의 요구 사항에 따라 고려하면 된다.
예를 들어 SPA 를 구현하고자 한다면, HashRouter가 조금 더 적합할 수 있다.
BrowserRouter는 HTML5의 'history' API를 사용하여 URL을 처리하므로, 서버가 사용자에게 항상 동일한 HTML 파일을 반환하도록 구성되어있어야 한다.
그렇지 않으면 404 Not Found 오류가 발생할 수 있다. 이에 반해, HashRouter는 URL의 'hash'부분을 사용하여 라우팅을 처리하므로,
서버에서 모든 경로를 항상 동일한 파일로 처리할 수 있어 SPA 서버 측에서 라우팅을 구성하기 더 쉽다.
따라서 서버가 정적인 콘텐츠를 제공하고, React 앱이 클라이언트에서 라우팅을 처리해야 하는 경우 HashRouter를 사용하는 것이 더 적합하고,
서버가 동적인 콘텐츠를 생성하는 경우 BrowserRouter를 사용할 수 있다.



* 간단한 예제

BrowserRouter
```
import React from 'react';
import { BrowserRouter, Route, Link } from 'react-router-dom';

function App() {
  return (
    <BrowserRouter>
      <div>
        <nav>
          <ul>
            <li>
              <Link to="/">Home</Link>
            </li>
            <li>
              <Link to="/about">About</Link>
            </li>
            <li>
              <Link to="/contact">Contact</Link>
            </li>
          </ul>
        </nav>

        <Route exact path="/" component={Home} />
        <Route path="/about" component={About} />
        <Route path="/contact" component={Contact} />
      </div>
    </BrowserRouter>
  );
}
```

HashRouter
```
import { HashRouter, Route } from 'react-router-dom';

function App() {
  return (
    <HashRouter>
      <Route exact path="/" component={Home} />
      <Route path="/about" component={About} />
      <Route path="/contact" component={Contact} />
    </HashRouter>
  );
}
```

HashRouter는 URL의 해시 부분을 사용하여 페이지를 관리하며, 이를 통해 페이지를 다시 로드하지 않고도 다른 라우트로 이동할 수 있도록 해준다. 
 예를 들어, /home, /about, /contact와 같은 URL 경로를 사용할 때, HashRouter는 URL의 해시 부분을 사용하여 /home#/, /about#/, /contact#/와 같이 표현.




