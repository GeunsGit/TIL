## Vue.js

### Vue.js의 특징

1. MVVM(ModelView-View-Model) 디자인 패턴
    - Model-View-ViewModel로 뷰가 특정 모델에 종속되지 않도록 모델을 분리한 패턴
    - 뷰와 모델의 독립성이 증가하고, 테스트와 유지보수에 용이해지며, 재사용성이 높아짐



2. SFC(Single File Component, SPA)
    - 하나의 파일에 여러개의 Component로 분리 설계
    - 구성 요소
        * <template></template> : 화면 구조
        * `<script> : 기능, 컴포넌트
            import 모듈명 from '외부모듈파일';
            export default {
                // 컴포넌트 관련 기술
            }
          </script>`
          * `<style></style>` : css
            - scoped : 현재 컴포넌트에만 css 적용