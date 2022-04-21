## Java Platfrom
	객체지향, 플랫폼 독립적(OS, DB, WAS)
	1. Java SE(JDK : IDE(Ecplise / InteliJ{상용화버전}), JRE : JVM + API{*.jar})
	2. java EE

### library vs f/w vs pattern vs architecture
- library : 개발을 하다 보니 반복적인 코드가 나오는 경우 - 미리 작성해서 재사용 *.class -> *.jar
			내가 만들어서 사용할 경우 클래스명, 자원위치, 확장자 등이 자유로움
- Framework : 패턴을 포함하는 누군가가 제공해준 기본 틀. 이용방법(규칙)이 정의됨 *.class -> *.jar형태의 라이브러리로 제공
- Pattern : 개발을 하다 보니 어떠한 문제점이 발생했을 때, 그 문제점에 대한 해결책
- Architecture

## Web Application
	- Model 2 Architecture
	- MVC Pattern
		- model : Java Class(Java Bean)
		- view : html, jsp
		- controller : servlet

## Spring 규칙
	-  기본 뼈대(필요 *.class -> *.jar)
		> library : *.jar(굉장히 많음) jar파일간의 의존관계 존재
		> 의존 관계 library 자동 framework
			- maven : xml 형식 -> pom.xml(Spring 프레임워크의 라이브러리 의존관계에 대한 자동 설정)
				환경설정
					1. xml(위치:classpath기반) : /tag 규칙, 속성, 계층 tag
						tag : body, empty body
					2. Annotation ex) @Controller @Service @Repository
					3. property 파일 (자원파일) *.properties
			- gradle : a, b, ... 규칙

## Spring 기본 어노테이션
	@Component
	framework에서 관리하는 객체(di 대상객체)
	선언위치 : 클래스 선언
	
	@Service
	서비스 기반 클래스
	선언위치 : 클래스 선언

	@Repository
	DAO 기반 클래스
	선언위치 : 클래스 선언
	
	@Autowired
	필요한 객체를 자동으로 주입 선언
	선언위치 : 멤버변수, 생성자, 메서드(setter(), 일반메서드() 가능)
	xml 환경설정 
		- <context:component-scan base-package="com.ssafy"/>
		- 해당 패키지에 있는 클래스들 중에서 @Component, @Service, @Repository 찾기 룩업
		- 여러개있을경우 Qualifiy
		
	@Controller
	Controller 클래스

### IoC

### DI (Dependancy Injection)
	의존성 주입
	
### DL

### POJO (Plain Old Java Object)
	오래된 방식의 간단한 자바 오브젝트