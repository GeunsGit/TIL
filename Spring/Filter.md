# Filter

## `includeFilters` 와 `excludeFilters`
- includeFilters : 컴포넌트 스캔 대상을 추가로 지정하는 어노테이션
- excludeFilters : 컴포넌트 스캔에서 제외할 대상을 지정하는 어노테이션

## Filter 적용 방법
1. 스프링 빈에 등록되도록 하기 
   - @ComponentScan(includeFilters = ~)
```java
    @Configuration
    @ComponentScan(
            includeFilters = @Filter(type = FilterType.ANNOTATION, classes = includeComponent.class)
    )
    public class ComponentFilterAppConfig {

    }
```


2. 스프링 빈에 등록되지 않도록 하기
    - @ComponentScan(excludeFilters = ~)
```java
    @Configuration
    @ComponentScan(
            excludeFilters = @Filter(type = FilterType.ANNOTATION, classes = excludeComponent.class)
    )
    public class ComponentFilterAppConfig {

    }
```


3. 위의 두 Filter을 동시에 적용할 수도 있다.
```java
    @Configuration
    @ComponentScan(
            includeFilters = @Filter(type = FilterType.ANNOTATION, classes = includeComponent.class),
            excludeFilters = @Filter(type = FilterType.ANNOTATION, classes = excludeComponent.class)
    )
    public class ComponentFilterAppConfig {

    }
```


## FilterType 옵션
- FilterType은 5가지 옵션이 있다.
    - ANNOTATION : 기본값, 애노테이션을 인식해 동작한다.

            ex) org.example.AnnotationName
    - ASSIGNABLE_TYPE : 지정한 타입과 자식 타입을 인식해서 동작한다.

            ex) org.example.ClassName
    - ASPECTJ : AspectJ 패턴을 사용한다.

            ex) org.example..*Service+
    - REGEX : 정규 표현식

            ex) org\.example\.Default.*
    - CUSTOM : `TypeFilter`이라는 인터페이스를 구현해서 처리한다.

            ex) org.example.MyTypeFilter


### PS
사실상 `@Component` 어노테이션이면 충분하기 때문에, `includeFilters`를 사용할 일은 거의 없다.
`excludeFilters`는 여러가지 이유로 간혹 사용할 때가 있지만 많지는 않다.