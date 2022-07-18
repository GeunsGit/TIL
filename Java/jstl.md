# JSTL

## JSTL이란 ?
- 자바서버 페이지 표준 태그 라이브러리

### JSTL 사용 방법
- 라이브러리 추가 필요하다.
	* tomcat\taglibs> *.jar
	* 프로젝트 단위 위치: project\WEB-INF\lib> *.jar
	
- EL과 함께 사용한다.
    * jsp 페이지에 지시어 태그 추가
	`<%@ taglib prefix="~~"
        uri="~~" %>`
	
    * `<prefix:tag-name attribute="value" />`

    * `<prefix:tag-name attribute="value" >
        ....
	</prefix:tag-name>`


### 대표적인 JSTL taglib	
- core: c 변수 지원, 흐름제어, URL처리 http://java.sun.com/jsp/jstl/core
- XML: x XML 코어, 흐름제어, XML변환 http://java.sun.com/jsp/jstl/xml
- 국제화:  fmt 지역, 메시지 형식, 숫자 및 날짜 형식 http://java.sun.com/jsp/jstl/fmt
- database:  sql SQL http://java.sun.com/jsp/jstl/sql
- 함수:  Collection, String 처리 http://java.sun.com/jsp/jstl/functions