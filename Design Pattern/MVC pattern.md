# MVC패턴(Model-View-Controller Pattern)

## MVC 패턴이란?

* 디자인 패턴(Design Pattern) 중 하나
* MVC란 Model View Controller의 약자로 어플리케이션의 역할을 세가지로 구분한 개발 방법론이다.

## Model, View, Controller

- Model
	* 서비스 로직(업무 로직) 클래스
	* DAO: DB Access 클래스
	* DTO: Data Transfer Object Class
	


- View:
	* 화면(view) : GUI, CLI
	* html(static contents), css, javascript(jquery, bootstra), ajax
	* JSP(Java Server Page: static + dynamic contents)
	


- Controller:
	* 요청 ~ 응답 제어 하는 클래스
	* 요청 데이터 가져오기
	* 요청 데이터 valid 검증 
		* view 검증: form 속성 required(필수), javascript(browser 지원여부 달라짐)
	* Model 요청의뢰(valid - 검증데이터)
	* Model 요청 결과 데이터 받기
	* 요청결과를 응답하기 위한 설정: 성공, 실패
	* 응답페이지 이동하기	
	

### 장점
- 직관적이고 단순하다.
- 기능별 코드 분리를 통해 코드의 가독성이 증가한다.


### 단점
- View와 Model간의 의존성이 높다.
- View와 Model간의 의존성이 높아질수록 유지보수가 어려워진다.
- 대규모 어플리케이션에서는 Controller에 다수의 Model과 View가 복잡하게 연결되어, 새 기능을 추가할 때마다 문제가 발생할 수 있다.


### 파생 패턴
- MVP Pattern
- MVVM Pattern


### 학습한 내용과 느낀 점
* 요즘 공부하면서 사용하는 패턴인데, 아직까지는 MVC 패턴의 한계를 느끼지는 못했지만, 여러 패턴을 숙지하고 장점을 살릴 수 있는 개발을 해야겠다.