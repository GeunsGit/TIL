## Spring Web MVC 프로젝트 관련 환경 설정
1. pom.xml : 의존관계 라이브러리
2. web.xml : DispatcherServlet 설정
3. servlet-context.xml
4. root-context.xml

## Spring MVC 프로젝트 개발 순서
1. pom.xml
2. web.xml
	- url-pattern
	- filter : 한글 인코딩
	- error 등

3. servlet-context.xml
    - 웹 관련 설정

4. root-context.xml
	- 웹 이외 설정
	- Model(DB) 관련 설정


## Web MVC 클래스 의존관계
1. 요청view

2. @Controller
    - 의존관계 서비스
    @Autowired
    Service service;

3. @Service
    - 의존관계 서비스
    @Autowired
    Dao dao;

4. @Repository

## @Controller 주요 어노테이션
- 요청 매핑 어노테이션 : 메서드 선언 앞에 위치
	- @RequestMapping("요청")

	- @RequestMapping(value={"/", "/index"})

	- @RequestMapping(value="요청", method=RequestMethod.GET)
	- @RequestMapping(value="요청", method=RequestMethod.POST)

	- @GetMapping("요청")
	- @PostMapping("요청")

- 요청 매핑 어노테이션 : 클래스 선언 앞에 위치
	- `ex) "/user/login", "/user/logout", "/user/input", "/user/list"`
	
```java
@Controller
@RequestMapping("/user")
public class UserController {
	@RequestMapping("/login")
	public String doA(){}

	@RequestMapping("/logout")
	public String doB(){}

	@RequestMapping("/list")
	public String doC(){}
}
```

- 요청 데이터 가져오기
    1. `public String doA(HttpServletRequest request) {
        String data1 = request.getParameter("data1");
	}`

    2. `public String doA(String data1, String data2) {
	}`

    3. `public String doA(Member dto) { // 반드시 JavaBean 규칙을 준수해야 함
	}`

    4. `public String doA(@RequestParam Map dtoMap) {
	}`

    5. `public String doA(@RequestParam("id") String userid) {
	}` // id를 가져와서 userid로 저장

    6. `public String doA(@ModelAttribute Member dto) {
	}`

    7. `public String doA(Member dto, Model model) {
        model.addAttribute("dto", dto);	// 요청 객체를 응답위한 설정
        model.addAttribute("result", result);	// 응답 설정
	}`