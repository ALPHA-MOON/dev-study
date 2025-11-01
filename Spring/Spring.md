## 스프링에 대하여
### 왜 스프링을 만들었는가
- 2000년대 초반 Java EE(J2EE)환경의 복잡성과 무거움에 대한 반발에서 시작
	- 1990년대 말 ~ 2000년대 초반의 Java 엔터프라이즈 개발은 `EJB(Enterprise Java Bean)`를 중심으로 돌아감
	- 기능은 많았지만 다음과 같은 단점이 있었음
		- 설정이 복잡하고 배포 과정이 까다로움
		- `EJB`를 사용하기 위해서는 별도의 컨테이너(`JBoss`, `WebLogic` 등)이 필수였음
		- 코드가 비대 해지고, 테스트하기 어려웠음
		- 단순한 비지니스 로직에도 많은 보일러 플레이트 코드가 필요했음
	- Rod Johnson(스프링 창시자)은 2002년에 _“Expert One-on-One J2EE Design and Development”_ 라는 책을 출판하면서 EJB의 복잡성을 비판하면서 **경량화된 컨테이너** 개념을 제시
		- 꼭 EJB가 없어도 트랜잭션, 보안, DAO 등을 구현할 수 있다.
		- 객체 지향 설계 원칙(SOLID, POJO 기반)을 지켜야 유지보수가 가능하다.
		- 프레임워크는 개발을 돕는 도구이지, 지배해서는 안 된다.
### 특징
- 철학: 복잡함으로부터 자유
- POJO(Plain Old Java Object)
	- 비즈니스 로직이 특정 컨테이너에 종속되지 않도록 설계
		```java
		//기존의 EJB 코드
		public class MyServiceBean implements SessionBean {
			public void ejbCreate() { ... }
			public void ejbRemove() { ... }
			public void ejbActivate() { ... }
			public void ejbPassivate() { ... }
			public void setSessionContext(SessionContext ctx) { ... }
		
			// 이 안에 실제 비즈니스 메서드
			public void doBusiness(...) { ... }
		}
		```
	- 순수 자바 객체로도 서비스 로직을 작성할 수 있게 함
- IoC(Inversion of Control, 제어의 역전)
	- 객체 생성과 의존성 관리를 내가 하지 않고 프레임워크가 담당 (DI: Dependency Injection)
	- 개발자는 비즈니스 로직에 집중할 수 있음
- AOP(Aspect Oriented Programming, 관점 지향 프로그래밍)
	- 로깅, 트랜잭션, 보안 등 공통 관심사를 핵심 로직과 분리
	- 코드 중복을 줄이고 유지보수를 쉽게 만듦
### 장점과 단점
- 장점
	- POJO 기반의 유연성 (비침투적 설계)
	- IoC / DI를 통한 낮은 결합도
	- AOP를 통한 공통 관심사 분리
	- 방대한 생태계와 통합성
	- 테스트와 품질 보장에 유리
- 단점
	- 학습 곡선이 가파름
	- 런타임 의존성 문제 (보이지 않는 마법)
	- 초기 설정 및 부트스트랩 복잡성
	- 성능 오버헤드
	- 버전 간 변화와 의존성 관리 어려움
- 단점에도 불구하고 spring을 사용하는 이유
	- 표준화된 엔터프라이즈 프레임워크
	- 방대한 생태계와 커뮤니티 지원
	- IoC / AOP 기반의 구조적 완성도
	- Spring Boot를 통한 생산성 향상
	- 클라우드·마이크로서비스 시대에 최적화
## 사용법
