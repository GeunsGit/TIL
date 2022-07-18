- router
    - 조각페이지 <include>

    - 라우터 클릭하면 이동(요청)
      `<router-link to="..."></router-link>`
      `<router-link :to="{ name: 'board', params = {key:data, key:data} }"></router-link>`

    - 해당 라우터 화면 보기
      `<router-view />`

    - router/index.js
```javascript
routes: [
  {
  path: "/",
  name: "home",
  component: HomeView,
  },
],
```