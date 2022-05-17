## Vue.js
	- Vue.js 특징
		1. MVVM(ModelView-View-Model) 디자인 패턴
			- Model-View-ViewModel로 뷰가 특정 모델에 종속되지 않도록 모델을 분리한 패턴
			- 뷰와 모델의 독립성이 증가하고, 테스트와 유지보수에 용이해지며, 재사용성이 높아짐
		2. SFC(Single File Component, SPA)
			- 하나의 파일에 여러개의 Component로 분리 설계
			- 구성 요소
				* <template></template> : 화면 구조
				* <script> : 기능, 컴포넌트
					import 모듈명 from '외부모듈파일';
					export default {
						// 컴포넌트 관련 기술
					}
				  </script>
				  * <style></style> : css
					- scoped : 현재 컴포넌트에만 css 적용


	- Vue 인스턴스
		- 라이프사이클 : 생성, 부착, 변경, 소멸
		- beforeCreate() created() beforeMount() mounted() beforeUpdate() updated() beforeDestroy() destroyed()

		- vue 속성
			new Vue({
				el: '#app',
				data: {
					message: '',
					count: 0,
					member; {},
					members: [],
				},
				// ES5
				data: function() {
					return {
						...
					}
				},
				data() {
					return {
						...
					}
				},
				methods: {
					doA() : {
					}
				},
				filters: {
					priceUnit(value) {
						return `${value} 만원`; // 지역필터선언 => {{ data-name | price | priceUnit }}
					}
				},
				template: {
				},
				components: {
				},
				router: {
				},
			});
			

	- vue directive
		- v-model
			* 양방향 바인딩 : input, textarea 사용자 입력데이터와 vue data를 바인딩, 변경되면 자동으로 반영
			* 단방향 바인딩 : component 자식컴포넌트가 이벤트를 발생시키면 부모컴포넌트가 자식 컴포넌트에게 데이터 전달
		- v-model.lazy : 데이터 입력을 다 하고, 포커스 이동 시에 데이터 바인딩 처리하는 디렉티브
		- v-bind : 속성명, 속성값 바인딩하는 디렉티브
		- 조건 : v-if, v-else, v-else-if
			* v-if : 조건이 거짓(false)면 DOM을 생성하지 않음
			* v-show : DOM은 생성하지만 보여주지 않음(display: none;)
		- 반복 : boards: []
			v-for="(article, index) in articles" :key="index"
			pk 컬럼이 있다면 ? v-for="article in articles" :key="article.articleno"
		- message : '<h3>제목입니다</h3>',
			=> 화면표현 html 태그로 파싱처리
			=> v-html : 태그 파싱처리 => JS innerHTML
			   v-text, {{ }} => 문자열로 처리 태그, 문자열 보간법
