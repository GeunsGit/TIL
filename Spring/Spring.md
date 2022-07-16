## Java Platfrom
	객체지향, 플랫폼 독립적(OS, DB, WAS)
	1. Java SE(JDK : IDE(Ecplise / InteliJ{상용화버전}), JRE : JVM + API{*.jar})
	2. java EE

### Library vs Framework vs Pattern vs Architecture
- **Library (라이브러리)**
  - 개발을 하다 보니 반복적인 코드가 나오는 경우 - 미리 작성해서 재사용 *.class -> *.jar
  - 내가 만들어서 사용할 경우 클래스명, 자원위치, 확장자 등이 자유로움


- **Framework (프레임워크)**
  - 패턴을 포함하는 누군가가 제공해준 기본 틀. 이용방법(규칙)이 정의됨 *.class -> *.jar형태의 라이브러리로 제공


- **Pattern (패턴)**
  - 개발을 하다 보니 어떠한 문제점이 발생했을 때, 그 문제점에 대한 해결책


- **Architecture (아키텍처)**
  - 기획한 내용을 프로그램화했을 경우 필요한 주요 특징을 기술적으로 설계하고 명시하는 것


## Web Application
- Model 2 Architecture
	- MVC Pattern
		- Model : Java Class(Java Bean)
		- View : html, jsp
		- Controller : servlet

## Spring 규칙
- 기본 뼈대 (필요 *.class -> *.jar)
  - library : *.jar(굉장히 많음) jar파일간의 의존관계가 존재한다.
      - 의존 관계 library 자동 framework
          - maven : xml 형식 -> pom.xml (Spring 프레임워크의 라이브러리 의존관계에 대한 자동 설정)
            
                환경설정 (크게 3가지로 분류된다.)
                    1. xml (위치 : classpath기반) - /tag 규칙, 속성, 계층 tag
                        tag : body, empty body
                    2. Annotation - ex) @Controller @Service @Repository
                    3. property 파일 (자원파일) - *.properties
          - gradle : a, b, ... 규칙

## Spring 기본 어노테이션
- @Component
  - framework에서 관리하는 객체(di 대상객체)
  - 선언위치 : 클래스 선언
	

- @Service
  - 서비스 기반 클래스
  - 선언위치 : 클래스 선언


- @Repository
  - DAO 기반 클래스
  - 선언위치 : 클래스 선언
	

- @Autowired
  - 필요한 객체를 자동으로 주입 선언
  - 선언위치 : 멤버변수, 생성자, 메서드(setter(), 일반메서드() 가능)
  - xml 환경설정 
      - <context:component-scan base-package="com.abcde"/>
      - base-package 기반 해당 패키지에 있는 클래스들 중에서 @Component, @Service, @Repository 룩업 !
      - 여러개 있을 경우 Qualifiy (@Qualifier 어노테이션을 통해 ID를 명시한다.)
		

- @Controller
  - Controller 클래스

### IoC
- 제어의 역전 : 메소드나 객체의 호출작업을 개발자가 결정하는 것이 아니라, 외부에서 결정되는 것을 의미한다.


### DI (Dependancy Injection)
- 의존성 주입, 의존관계 설정 : 객체를 직접 생성하는 게 아니라 외부에서 생성한 후 주입시켜주는 방식이다.
  - 모듈 간의 결합도가 낮아지고 유연성이 높아지는 장점을 갖는다.
	

### POJO (Plain Old Java Object)
  - 오래된 방식의 간단한 자바 오브젝트