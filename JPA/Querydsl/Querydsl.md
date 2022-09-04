# [Querydsl](http://querydsl.com/)

![img_1](https://user-images.githubusercontent.com/92859179/188321459-72a507f5-264c-4635-8808-93c1eae64beb.png)

## 학습하게 된 이유

공통 프로젝트를 하면서 Spring Data JPA를 이용해 CRUD 메서드와 쿼리 메서드로 객체 중심의 개발을 했었다.
JPQL로 정적 쿼리를 다루는 경우라면 애플리케이션 로딩 시점에서 쿼리를 만들기 때문에 
애플리케이션 로딩 시점에서 에러를 발견할 수 있다는 것이 장점이라면 큰 장점이었다.

하지만 쿼리를 실행하는 시점에서 오류를 발견할 수 있고, 요즘은 IDE가 어느정도 보여주긴 하지만 컴파일 시점에서 미리 에러를 잡을 수는 없었다.
테스트하면서 서버를 껐다 켰다 하는 시간도 다 비용이라고 생각됐다..

이러한 문제를 Querydsl 을 사용하면 컴파일 시점에 오류를 잡을 수 있을 뿐만 아니라 여러 장점이 있었다.
그래서 인프런의 김영한 개발자님 강의를 참고하며 학습하게 됐다.

## Querydsl이란?
- Java에서 JPA, MongoDB 및 SQL을 포함한 여러 백엔드에 대해 유형이 안전한 SQL과 유사한 쿼리를 구성할 수 있는 프레임워크
- 쿼리를 인라인 문자열로 작성하거나 XML 파일로 외부화하는 대신 다양한 API를 통해 구성된다.
> https://github.com/querydsl/querydsl

## Querydsl의 장점
- 문자열이 아닌 Java 코드로 작성하기 때문에 **컴파일 시점**에 문법 오류를 확인할 수 있다 !
- JPQL과 유사하기 때문에 학습이 수월하다.
- **동적 쿼리**를 작성하기 쉽다 !!
- 쿼리를 작성할 때 <u>메서드를 추출해 재사용</u>이 가능하다 !

### build.gradle

스프링 부트 2.6 이상 버전부터 Querydsl을 적용하기 위해 build.gradle 설정 파일을 변경할 필요가 있었다.
이번 프로젝트에서도 2.6 이상 버전을 사용할 것이기 때문에 잘 유의해야겠다.

### Spring Boot 2.6 이상, Querydsl 5.0 적용법

```
buildscript {
	ext {
		queryDslVersion = "5.0.0"
	}
}
plugins {
	id 'org.springframework.boot' version '2.7.3'
	id 'io.spring.dependency-management' version '1.0.13.RELEASE'
	// querydsl 추가
	id 'com.ewerk.gradle.plugins.querydsl' version '1.0.10'
	id 'java'
}
group = 'study'
version = '0.0.1-SNAPSHOT'
sourceCompatibility = '11'
configurations {
	compileOnly {
		extendsFrom annotationProcessor
	}
}
repositories {
	mavenCentral()
}
dependencies {
	implementation 'org.springframework.boot:spring-boot-starter-data-jpa'
	implementation 'org.springframework.boot:spring-boot-starter-web'
	// querydsl 추가
	implementation "com.querydsl:querydsl-jpa:${queryDslVersion}"
	annotationProcessor "com.querydsl:querydsl-apt:${queryDslVersion}"
	compileOnly 'org.projectlombok:lombok'
	runtimeOnly 'com.h2database:h2'
	annotationProcessor 'org.projectlombok:lombok'
	// 테스트에서 lombok 사용
	testCompileOnly 'org.projectlombok:lombok'
	testAnnotationProcessor 'org.projectlombok:lombok'
	testImplementation 'org.springframework.boot:spring-boot-starter-test'
}
tasks.named('test') {
	useJUnitPlatform()
}
// querydsl 추가 시작
def querydslDir = "$buildDir/generated/querydsl"
querydsl {
	jpa = true
	querydslSourcesDir = querydslDir
}
sourceSets {
	main.java.srcDir querydslDir
}
compileQuerydsl{
	options.annotationProcessorPath = configurations.querydsl
}
configurations {
	compileOnly {
		extendsFrom annotationProcessor
	}
	querydsl.extendsFrom compileClasspath
}
// querydsl 추가 끝
```

## 느낀 점
- IntelliJ IDE를 이용해 학습했는데, 자바 코드이다 보니 IDE에서 제공하는 코드 자동완성 기능을 활용할 수 있어서 빠른 코드 작성이 가능했다.
- JPA 를 처음 학습했을 때보다 비교적 러닝 커브가 낮은 것 같아서 다음 프로젝트 때 활용할 수 있을 것 같다.
- Where 다중 파라미터를 사용해 동적 쿼리를 작성하면 얻을 수 있는 장점이 많았다.
  - 추출한 메서드를 조립할 수 있다.
  - 재사용이 용이하며 쿼리 자체의 가독성이 높아진다.
    - ```java
      public void dynamicQuery_WhereParam() {
          String usernameParam = "member1";
          Integer ageParam = 10;
           
          List<Member> result = searchMember2(usernameParam, ageParam);
          assertThat(result.size()).isEqualTo(1);
      }
    
      private List<Member> searchMember2(String usernameCond, Integer ageCond) {
          return queryFactory
              .selectFrom(member)
      // where 절에 조립한 메서드 사용 !! == .where(usernameEq(usernameCond), ageEq(ageCond))
              .where(allEq(usernameCond, ageCond))
              .fetch();
      }
    
      private BooleanExpression usernameEq(String usernameCond) {
          return usernameCond != null ? member.username.eq(usernameCond) : null;
      }

      private BooleanExpression ageEq(Integer ageCond) {
          return ageCond != null ? member.age.eq(ageCond) : null;
      }
        
      // 메서드 조립 !!
      private BooleanExpression allEq(String usernameCond, Integer ageCond) {
          return usernameEq(usernameCond).and(ageEq(ageCond));
      }
      ```

#### 레퍼런스
> https://www.inflearn.com/course/Querydsl-%EC%8B%A4%EC%A0%84   
> http://querydsl.com/   
> http://querydsl.com/static/querydsl/4.0.1/reference/ko-KR/html_single/   