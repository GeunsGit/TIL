# Exception

-------------
### 에러와 예외
	- 어떤 원인에 의해 오동작 하거나 비정상적으로 종료되는 경우
	- 심각도에 따른 분류
		* Error
			- 메모리 부족, stack overflow와 같이 일단 발생하며 복구할 수 없는 상황
			- 프로그램의 비 정상적 종료를 막을 수 없음 -> 디버깅 필요
		* Exception
			- 읽으려는 파일이 없거나 네트워크 연결이 안 되는 등 수습될 수 있는 비교적 상태가 약한 것들
			- 프로그램 코드에 의해 수습될 수 있는 상황
	- exception handling(예외 처리)란
		* 예외 발생 시 프로그램의 비 정상 종료를 막고 정상적인 실행 상태를 유지하는 것
			- 예외의 감지 및 예외 발생 시 동작할 코드 작성 필요

-------------
### 예외 클래스의 계층
	- checked exception
		* RuntimeException 아닌 계열의 예외
		* IOException, SQLException
		* javac 컴파일시점에서 예외처리를 체킹함 : 예외처리를 강제 : 하지 않으면 컴파일 오류 발생
		* 예외에 대한 대처 코드가 없으면 컴파일이 진행되지 않음
		
		
	- unchecked exception (RuntimeException의 하위 클래스)
		* 예외에 대한 대처 코드가 없더라도 컴파일은 진행됨
		* javac 컴파일시점에서 예외처리 여부 체킹하지 않음

-------------
### try ~ catch 구문
	
	try {
	예외가 발생할 수 있는 코드
	} catch (XXException e) { // 던진 예외를 받음
	예외가 발생했을 때 처리할 코드
	}

-------------
### Exception 객체의 정보 활용
	- Throwable의 주요 메서드
		* public String getMessage() : 발생된 예외에 대한 구체적인 메시지 반환
		* public Throwable getCause() : 예외의 원인이 되는 Throwable 객체 또는 null을 반환
		* public void printStackTrace() : 예외가 발생된 메서드가 호출되기까지의 메서드 호출 스택을 출력한다. 디버깅의 수단으로 주로 사용된다.
		
-------------
### try-catch 문에서의 흐름
	- try 블록에서 예외가 발생하면
		* JVM이 해당 Exception 클래스의 객체 생성 후 던짐(throw)
		- throw new XXException()
		* 던져진 exception을 처리할 수 있는 catch 블록에서 받은 후 처리
		- 적당한 catch 블록을 만나지 못하면 예외처리는 실패
		* 정상적으로 처리되면 try-catch 블록을 벗어나 다음 문장 진행
	- try 블록에서 어떠한 예외도 발생하지 않은 경우
		* catch 문을 거치지 않고 try-catch 블록의 다음 흐름 문장을 진행	
		
--------------
### 다중 exception handling
	- try 블록에서 여러 종류의 예외가 발생할 경우
		* 하나의 try 블록에 여러 개의 catch 블록 추가 가능
		- 예외 종류별로 catch 블록 구성
	- 다중 catch 문장 작성 순서 유의 사항
		* JVM이 던진 예외는 catch문장을 찾을 때는 다형성이 적용됨
		* 상위 타입의 예외가 먼저 선언되는 경우 뒤에 등장하는 catch 블록은 동작할 기회가 없음
		* 상속 관계가 없는 경우는 무관
		* 상속 관계에서는 작은 범위(자식)에서 큰 범위(조상)순으로 정의
		
--------------
### 다중 예외 처리를 이용한 Checked Exception 처리
	- 발생하는 예외들을 하나로 처리하기
		try {
		// 다중 예외 발생 코드
		} catch (Exception e) {
			System.out.printf("예외 발생: %s%n", e.getMessage());
		}
		* 예외 상황 별 처리가 쉽지 않음
		* 가급적 예외 상황 별로 처리하는 것을 권장
	- 심각하지 않은 예외를 굳이 세분화 해서 처리하는 것도 낭비

--------------
### try ~ catch ~ finally 구문을 이용한 예외 처리

	- finally는 예외 발생 여부와 상관 없이 언제나 실행
		* 중간에 return을 만나는 경우도 finally 블록을 먼저 수행 후 리턴 실행
	- 주요 목적 : try 블록에서 사용한 리소스 반납
	- 생성한 시스템 자원을 반납하지 않으면 장래 resource leak 발생 가능 -> close 처리
	- finally에서 close를 통한 자원 반납

--------------	
### try-with-resources

	- JDK 1.7 이상에서 리소스의 자동 close 처리
	try(리소스_타입1 res1 = 초기화: 리소스_타입2 res2 = 초기화; ...) {
	// 예외 발생 코드
	} catch(Exception e) {
	// exception handling 코드
	}
	
	- try 선언문에 선언된 객체들에 대해 자동 close 호출(finally 역할)
		* 단 해당 객체들이 AutoCloseable interface를 구현할 것
		 - 각종 I/O stream, socket, connection ...
		* 해당 객체는 try 블록에서 다시 할당될 수 없음

--------------
### throws 키워드를 통한 처리 위임

	- method에서 처리해야 할 하나 이상의 예외를 호출한 곳으로 전달(처리 위임)
		* 예외가 없어지는 것이 아니라 단순히 전달됨
		* 예외를 전달받은 메서드는 다시 예외 처리의 책임 발생
		* 처리하려는 예외의 조상 타입으로 throws 처리 가능
	
--------------	
### checked exception과 throws

	- checked exception은 반드시 try~catch 또는 throws 필요
	- 필요한 곳에서 try~catch 처리
	
--------------	
### 메서드 재정의와 throws

	- 메서드 재정의 시 조상클래스가 메서드가 던지는 예외보다 부모예외를 던질 수 없다.
		* 부모가 치지 않은 사고를 자식이 칠 수 없다.
	
--------------	
### 사용자 정의 예외

	- API에 정의된 exception이외에 필요에 따라 사용자 정의 예외 클래스 작성
	- 대부분 Exception 또는 RuntimeException 클래스를 상속받아 작성
		* checked exception 활용 : 명시적 예외 처리 또는 throws 필요
		 - 코드는 복잡해지지만 처리 누락 등 오류 발생 가능성은 줄어듦
		* runtime exception 활용 : 묵시적 예외 처리 가능
		 - 코드가 간결해지지만 예외 처리 누락 가능성 발생
	- 사용자 정의 예외를 만들어 처리하는 장점
		* 객체의 활용 - 필요한 추가 정보, 기능 활용 가능
		* 코드의 재사용 - 동일한 상황에서 예외 객체 재사용 가능
		* throws 메커니즘의 이용 - 중간 호출 단계에서 return 불필요
		
--------------
### 학습한 내용과 느낀점
- 예외처리를 공부하면서도 다형성의 중요함이나 위대함을 느꼈다. 예외간에도 계층 관계가 있다는 점이 신기했다.
- Checked Exception과 Unchecked exception에 대해 알게 됐다. checked exception 같은 경우는 컴파일 시점에서 예외 처리를 체킹하기 때문에 정상적으로 예외처리가 되어 있지 않으면 컴파일조차 되지 않는 점을 알았다.
- 단순히 예외는 throws로 던지거나 try ~ catch문을 통해 에러가 발생했을 때 대처하는 거로만 인지하고 있었는데, 다양한 예외와 예외 처리 방법을 알면 에러가 발생했을 때 명확한 원인을 파악하기 쉽고, 자원 낭비를 막을 수 있는 것을 알게 되었다.