# 인터페이스 (Interface)

-------------
## 인터페이스란?

* Class Node Type (클래스 종류) 중 하나
* 동일한 목적 하에 동일한 기능을 수행하게끔 강제하는 것

-------------
### 설계 방법

- 부모인터페이스 > 구현 자식클래스
	- 통상적으로 작명은 다음과 같이 한다.
- 부모인터페이스
	- public interface IF인터페이스이름 {}
	- public interface I인터페이스이름  {}
	- public interface 인터페이스이름   {}

- 자식구현클래스
	- public class 클래스이름Impl implements 부모인터페이스이름 {}
	- public class 클래스이름 implements IF부모인터페이스이름 {}

-------------
### 특징

- 직접 객체 생성 불가
- 상수와 추상메서드로만 존재하는 클래스 형태
- 상속(구현) : 필수
- 상속(구현) : implements 부모인터페이스이름1, 부모인터페이스이름X
- 인터페이스도 extends를 이용해 상속이 가능
- 클래스와 다른 점은 인터페이스는 다중 상속이 가능
- 다중 구현
- 자식클래스가 반드시 재정의(overriding)해서 자식객체로 객체 생성 사용
- 최고 수준의 추상화 단계 : 모든 메서드가 abstract 형태
	- 형태
		* 클래스와 유사하게 interface 선언
		* 멤버 구성
			* 모든 멤버변수는 public static final 이며 생략 가능
			* 모든 메서드는 public abstract 이며 생략 가능

-------------
### 필요성	
	
- 인터페이스의 필요성
	- 구현의 강제로 표준화 처리
		* abstract 메서드 사용
	- 인터페이스를 통한 간접적인 클래스 사용으로 손쉬운 모듈 교체 지원
	- 서로 상속의 관계가 없는 클래스들에게 인터페이스를 통한 관계 부여로 다형성 확장
	- 모듈 간 독립적 프로그래밍 가능 -> 개발 기간 단축

-------------
### default method vs static method

- default method
	- 인터페이스에 선언 된 구현부가 있는 일반 메서드
		* 메서드 선언부에 default modifier 추가 후 메서드 구현부 작성
		- 접근 제한자는 public으로 한정됨(생략 가능)
	- 필요성
		* 기존에 interface 기반으로 동작하는 라이브러리의 interface에 추가해야 하는 기능이 발생
		* 기존 방식으로라면 모든 구현체들이 추가되는 메서드를 override 해야 함
		* default 메서는 abstract가 아니므로 반드시 구현 해야 할 필요는 없어짐
	- 충돌
		* jdk1.7 이하의 java에서는 interface method에 구현부가 없으므로 충돌이 없었음
		* 1.8부터 default method가 생기면서 동일한 이름을 갖는 구현부가 있는 메서드가 충돌
		* method 우선 순위
			* super class의 method 우선 : super class가 구체적인 메서드를 갖는 경우 default method는 무시됨
			* interface간의 충돌 : 하나의 interface에서 default method를 제공하고 다른 interface에서도 같은 이름의 메서드(default 유무와 무관)가 있을 때 sub class는 반드시 override 해서 충돌 해결!!
								
- static method
	- interface에 선언된 static method
		* 일반 static 메서드와 마찬가지로 별도의 객체가 필요 없음
		* 구현체 클래스 없이 바로 인터페이스 이름으로 메서드에 접근해서 사용 가능
-------------
### default method가 생기게 된 배경?

- 오픈소스 : interface 제공
		- 변경사항발생
		- 추상메서드 추가
		
- 오픈소스를 가져와서 interface 구현클래스 사용
	1. 기존 오류 발생
	2. 변경
	3. 하위버전호환성을 보장하지 않음: 문제 발생!
	4. default method는 서브클래스에서 재정의 가능


-------------
### 사용 방법

- default method는 객체생성 참조변수명.default메서드명();
- static method는 객체생성없이 인터페이스이름.static메서드명();

-------------
### 학습한 내용과 느낀 점

- 기존에는 interface를 단순히 표준화하기 위한 도구라고만 생각했다. 하지만 더 공부해보니 강제 구현, 다형성 여러 부분을 적용시킬 수 있는 클래스 노드 타입이었다.
- 또한 인터페이스를 공부하면서 함수형 프로그래밍에 대해 알게 됐다. 자바에서 함수형 인터페이스(FunctionalInterface)를 사용해 람다 표현식도 사용할 수 있는 것을 알게 됐다.
- default method가 Java8 부터 생겼다고 하는데, 그 전부터는 변경사항이 발생했을 때 얼마나 많은 작업이 필요했을지 상상이 안된다. 물론 아직 Java8 이전의 버전을 사용하는 곳도 많겠지만 default method는 참 편리하겠다는 생각이 들었다.