# Page Routing

> **폴더 구조를 통한 라우팅**

NextJS 13이 나오기 이전부터 쓰이던 라우팅 방식이다.  
 pages폴더의 구조를 통해 라우트를 제공하는 방식이라고 보면 된다.

## 정적 라우팅

페이지에서 `/`, `/profile`등의 라우팅를 의미한다.  
 파일을 생성하고 이름을 바꾸는 것으로 라우트를 생성할 수 있다.
또한 폴더를 생성하는 것으로 중첩 라우트를 생성할 수도 있다.

```js
pages
└ _app.jsx
└ _document.jsx
└ index.jsx // "/" 경로에서 보여짐
└ profile.jsx // "/profiles" 경로에서 보여짐
└ posts
  └ index.jsx // "/posts" 경로에서 보여짐
  └ write.jsx // "/posts/write" 경로에서 보여짐
```

## 동적 라우팅

파일의 이름을 `[name].js`등으로 설정하여 동적 라우팅을 사용할 수도 있다.

```js
pages
└ _app.jsx
└ _document.jsx
└ index.jsx // "/" 경로에서 보여짐
└ profile.jsx // "/profiles" 경로에서 보여짐
└ posts
  └ index.jsx // "/posts" 경로에서 보여짐
  └ write.jsx // "/posts/write" 경로에서 보여짐
  └ detail
    └ [id].jsx // "/posts/detail/1", "/posts/detail/2" 등의 경로에서 보여짐
```
