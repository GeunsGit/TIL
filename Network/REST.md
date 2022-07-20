## REST

### REST 구성 요소
1. 자원(Resource) : HTTP URI

2. 자원에 대한 행위(Verb) : HTTP Method

3. 자원에 대한 행위의 내용 (Representations) : HTTP Message Pay Load


### REST 특징
1. Server-Client(서버-클라이언트 구조)

2. Stateless(무상태)

3. Cacheable(캐시 처리 가능)

4. Layered System(계층화)

5. Uniform Interface(인터페이스 일관성)


### RESTful 이란?
RESTFUL이란 REST의 원리를 따르는 시스템을 의미합니다. 하지만 REST를 사용했다 하여 모두가 RESTful 한 것은 아닙니다.  REST API의 설계 규칙을 올바르게 지킨 시스템을 RESTful하다 말할 수 있으며

모든 CRUD 기능을 POST로 처리 하는 API 혹은 URI 규칙을 올바르게 지키지 않은 API는 REST API의 설계 규칙을 올바르게 지키지 못한 시스템은 REST API를 사용하였지만 RESTful 하지 못한 시스템이라고 할 수 있습니다.


#### References
- www.incodom.kr/REST

### **Question** REST의 개념에 대해 설명해주세요.
- **답변 예시**

REST란 Representational State Transfer의 약자로 자원을 이름으로 구분하여 해당 자원의 상태를 주고 받는 것으로,

HTTP URI를 통해 자원을 명시하고 HTTP Method를 통해 해당 자원에 대한 상태를 주고 받는 방식을 말합니다.