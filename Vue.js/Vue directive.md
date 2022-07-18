## Vue.js

- **이벤트처리 directive**

    - `v-on:이벤트명`, `@이벤트명`

    - 클릭이벤트 : `v-on:click=""`, `@click=""`

    - 변경이벤트 : `@change=""`

    - 전송이벤트 : `@submit`

    - v-model
      * 양방향 바인딩 : input, textarea 사용자 입력데이터와 vue data를 바인딩, 변경되면 자동으로 반영

      * 단방향 바인딩 : component 자식컴포넌트가 이벤트를 발생시키면 부모컴포넌트가 자식 컴포넌트에게 데이터 전달

      - v-model.lazy : 데이터 입력을 다 하고, 포커스 이동 시에 데이터 바인딩 처리하는 디렉티브

      - v-bind : 속성명, 속성값 바인딩하는 디렉티브

    - 조건 : v-if, v-else, v-else-if
      * v-if : 조건이 거짓(false)면 DOM을 생성하지 않음
      * v-show : DOM은 생성하지만 보여주지 않음(display: none;)

    - 반복 : boards: []
    - `v-for="(article, index) in articles" :key="index"`

    - pk 컬럼이 있다면 ? `v-for="article in articles" :key="article.articleno"`

    - message : `'<h3>제목입니다</h3>'`,
      - 화면표현 html 태그로 파싱처리
      - v-html : 태그 파싱처리 => JS innerHTML
      - v-text, {{ }} => 문자열로 처리 태그, 문자열 보간법