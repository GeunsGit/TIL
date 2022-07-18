# Spring


## Spring MVC Project 폴더 구조
- pom.xml
    - 의존관계 라이브러리 설정


- src/main/java
    - 자바 클래스


- src/main/resources
    - 자원 설정 파일
    - 로깅 관련 설정 : log4j.xml


- src/test/java
- src/test/resources
    - 테스트 관련 자바 클래스 및 자원 파일


- src/main/webapp/resources
    - static 파일 : html, css, js, image 등


- src/main/webapp/WEB-INF
    - web.xml


- src.main/webapp/WEB-INF/spring/
    - root-context.xml
    - 일반 자바 관련 빈 설정
    - DB 관련 빈 설정


- src/main/webapp/WEB-INF/spring/appServlet/
    - servlet-context.xml
    - web 관련 설정
    - resources 설정: static file(html, css 등)의 위치
    - jsp 관련 위치 등 설정
    - 컴포넌트 설정 <context:component-scan base-package="com.~~~.~~~" />