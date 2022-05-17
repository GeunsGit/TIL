## Vue.js
	- 이벤트처리 directive
		- v-on:이벤트명, @이벤트명
		- 클릭이벤트 : v-on:click="", @click=""
		- 변경이벤트 : @change=""
		- 전송이벤트 : @submit

	- component 통신
		- 기본적으로 상위 컴포넌트와 하위 컴포넌트의 단방향 통신
		- EventBus : 형제 컴포넌트 통신 (Vue에서는 권장하지 않는 방식 ! vuex를 사용하자 !)
			- bus.$emit('', data) : 이벤트 발생
			- bus.$on('', data) : 이벤트 수신
		- vuex : (데이터)상태 관리, 세션 관리 라이브러리, 중앙 자료 저장소

	- axios
		- 비동기통신 목적, ajax
		- http method: crud(post, get, put, delete) => REST
		- 성공하면(then), 오류가 발생하면(catch), 반드시 수행 로직(finally)
		- axios.get('url').then().then().then().catch().finally();

	- REST : 네트워크 웹에 있는 자원을 정의(post, get, put, delete)하고 , url(주소) 지정하는 기술

	- router
		- 조각페이지 <include>
		- 라우터 클릭하면 이동(요청)
			<router-link to="..."></router-link>
			<router-link :to="{ name: 'board', params = {key:data, key:data} }"></router-link>
		- 해당 라우터 화면 보기
			<router-view />
		- router/index.js
			routes: [
				{
					path: "/",
					name: "home",
					component: HomeView,
				},
			]

### Vue CLI
		- CLI : Command Line Interface
		- Vue 프로젝트 관리 패키지
		- NPM(Node Package Manager)
			=> 의존관계 패키지 설정
			=> package.json
		- ES6 기반
			=> 프로젝트 생성 시 선택 : babel (ES6 미지원시 ES5로 자동 변환)
		- prettier/lint(eslint) : 프로젝트 생성 시 선택
			=> 소스코드 표준 형식 체킹, 오류 체킹
			=> JavaScript