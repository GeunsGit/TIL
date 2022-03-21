# 팩토리 패턴(Factory Pattern)

-------------
## 팩토리 패턴이란?

* 객체지향 디자인 패턴(Design Pattern) 중 하나
* 부모 클래스에 알려지지 않은 구체 클래스를 생성하는 패턴
  * 자식 클래스가 어떤 객체를 생성할지를 결정하도록 하는 패턴이기도 함.
-------------
  
### 설계 규칙
- JDBC 프로그래밍을 하면서 나는 다음과 같이 Factory Pattern을 통해 설계해 보았다.

```java
public class FactoryDao {	
	private static FactoryDao instance = new FactoryDao();
	
	/** 1. JDBC Driver 로딩 : Factory 위임 */
	private FactoryDao() {
		try {
			Class.forName(driver);
		} catch (ClassNotFoundException e) {
			e.printStackTrace();
		}
	}
	
	public static FactoryDao getInstance() {
		return instance;
	}
	
	/** 2. DBMS 서버 연결 : Factory 위임 */
	public Connection getConnection() throws SQLException {
		return DriverManager.getConnection(url, user, password);
	}
}
/*
	생략...
*/
```

```java
public class MemberDao {
	/* Factory 위임
	private String driver = "com.mysql.cj.jdbc.Driver";
	private String url = "jdbc:mysql";
	private String user = "ssafy";
	private String password = "ssafy";
	*/
	
	private FactoryDao factory = FactoryDao.getInstance();
	private static MemberDao instance = new MemberDao();
	
	/** 1. JDBC Driver 로딩 : Factory 위임 */
	private MemberDao() {
		/* Factory 위임
		try {
			Class.forName(driver);
		} catch (ClassNotFoundException e) {
			e.printStackTrace();
		}
		*/
	}
	
	public static MemberDao getInstance() {
		return instance;
	}
}
```
-------------
### 사용 방법 
* 객체 생성부 미 분리
* 객체 생성을 외부 팩토리에서 처리하기
* 서브 클래스에서 객체 생성을 결정하기
-------------
### 사용하는 이유는 ?
- 객체를 생성하는 코드를 분리해 클라이언트 코드와의 결합도를 낮추기 위해 !
    * 객체 추가 및 수정시에도 객체 생성하는 코드만 수정하면 된다.
-------------
### 팩토리 패턴의 장점
- 강력한 유연성을 지닌다.
	- 서브 클래스에 팩토리 메소드를 두기 때문!
	- 생성하는 것을 서브 클래스로 확장해 마음대로 변경할 수 있다.
- 객체 생성을 한 곳에서, 체계적으로 관리할 수 있다.
-------------
### 학습한 내용과 느낀 점
* 간단한 프로젝트를 진행하면서, 새로운 패턴을 학습하게 됐다.
* 생성 책임을 별도로 분리한다는게 어마어마한 장점이라고 생각됐다!
* 여러 패턴을 필요에 따라 잘 활용하는게 중요한 것 같다고 느꼈다.