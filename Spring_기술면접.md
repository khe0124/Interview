# Spring_기술면접

## 1. Framework
- 특정 형태의 소프트웨어 문제를 해결하기 위해 상호 협력하는 클래스 프레임과 인터페이스 프레임의 집합.
- 특정한 틀을 만들어 놓고 거기에 살을 붙여 놓음으로써 프로그램을 만들어 작업시간을 줄여주는 것이다.
- 프레임워크는 특정 개념들의 추상화를 제공하는 여러 클래스나 컴포넌트로 구성된다.
- 프레임워크는 이렇게 추상적인 개념들이 문제를 해결하기 위해 같이 작업하는 방법을 정의한다.
- 프레임워크는 좀 더 높은 수준에서 패턴을 조작한다.
* 프레임워크가 중요한 이유는 객체지향 개발을 하게 되면서 개발자의 취향에 따라 다양한 프로그램이 나오게 되었다. 프로그램 개발에 투입되는 개발자도 점점 늘어남에 따라 전체 시스템의 통합성, 일관성이 부족하게 되었기 때문이다. 그래서 개발자의 자유를 제한하기 위해 프레임워크를 도입했다.

## 2. 프레임워크가 가져야할 특징
a. 개발자들이 따라야할 가이드라인을 가진다.
b. 개발할 수 있는 범위가 정해져 있다.
c. 개발자를 위한 다양한 도구들이 지원된다.

## 3. 프레임워크의 장/단점
장점  –  개발 시간을 줄일 수 있고 오류로부터 자유로울 수 있다.
단점  –  프레임워크에 너무 의존하면 개발 능력이 떨어져서 프레임워크 없이 개발하는 것이 불가능해진다.


## 4. Spring Framework(스프링 프레임워크)
- 자바(JAVA) 플랫폼을 위한 오픈소스(Open Source) 애플리케이션 프레임워크(Framework)
- 자바 엔터프라이즈 개발을 편하게 해주는 오픈소스 경량급 애플리케이션 프레임워크
- 자바개발을 위한 프레임워크로 종속 객체를 생성해주고, 조립해주는 도구
- 자바로 된 프레임워크로 자바SE로 된 자바 객체(POJO)를 자바EE에 의존적이지 않게 연결해주는 역할


## 5. 스프링 특징 간단히
- 크기와 부하의 측면에서 경량
- 제어 역행(IoC)이라는 기술을 통해 애플리케이션의 느슨한 결합을 도모
- 관점 지향 프로그래밍(AOP)을 위한 풍부한 자원
- 애플리케이션 객체의 생명주기와 설정을 포함하고 관리한다는 점에서 일종의 컨테이너(Container)라고 할 수 있음.
- 간단한 컴포넌트로 복잡한 애플리케이션을 구성하고 설정할 수 있음.


## 6. 스프링 특징 자세히
- a. 경량 컨테이너로서 자바 객체를 직접 관리 => 각각의 객체 생성, 소멸과 같은 라이프 사이클을 관리하며 스프링으로부터 필요한 객체를 얻어올 수 있다.
- b. 스프링은 POJO(Plain Old Java Object) 방식의 프레임워크. => 일반적인 J2EE 프레임워크에 비해 구현을 위해 특정한 인터페이스를 구현하거나 상속을 받을 필요가 없어 기존에 존재하는 라이브러리 등을 지원하기에 용이하고 객체가 가볍다.
- c. 스프링은 제어의 역행(IoC : Inversion of Control)을 지원 => 컨트롤의 제어권이 사용자가 아니라 프레임워크에 있어서 필요에 따라 스프링에서 사용자의 코드를 호출한다.
- d. 스프링은 의존성 주입(DI : Dependency Injection)을 지원 => 각각의 계층이나 서비스들 간에 의존성이 존재할 경우 프레임워크가 서로 연결시켜준다.
- e. 스프링은 관점 지향 프로그래밍(AOP : Aspect-Oriented Programming)을 지원 => 따라서 트랜잭션이나 로깅, 보안과 같이 여러 모듈에서 공통적으로 사용하는 기능의 경우 해당 기능을 분리하여 관리할 수 있다.
- f. 스프링은 영속성과 관련된 다양한 서비스를 지원 => MyBatis나 Hibernate등 이미 완성도가 높은 데이터베이스 처리 라이브러리와 연결할 수 있는 인터페이스를 제공한다.
- g. 스프링은 확장성이 높음 => 스프링 프레임워크에 통합하기 위해 간단하게 기존 라이브러리를 감싸는 정도로 스프링에서 사용이 가능하기 때문에 수많은 라이브러리가 이미 스프링에서 지원되고 있고 스프링에서 사용되는 라이브러리를 별도로 분리하기도 용이하다.


## 7. Spring MVC 구조의 처리과정
1) DispatcherServlet : 어플리케이션으로 들어오는 모든 Request를 받는 관문이다. Request를 실제로 처리할 Controller에게 전달하고 그 결과값을 받아서 View에게 전달하여 적절한 응답을 생성할 수 있도록 흐름을 제어한다.
2) HandlerMapping : Request URL 각각 어떤 Controller가 실제로 처리할 것인지 찾아주는 역할
3) Controller : Request를 직접 처리한 후 그 결과를 다시 DispatcherServlet에게 돌려준다.
4) ModelAndView : Controller가 처리한 결과와 그 결과를 보여줄 View에 관한 정보를 담고있는 객체이다.
5) ViewResolver : View관련 정보를 갖고 실제 View를 찾아주는 역할을 한다.
6) View : Controller가 처리한 결과값을 보여줄 View를 생성한다.

## 8. AOP
- Aspect Oriented Programming 관점 지향 프로그래밍의 약자
- 기존의 OOP에서 기능별로 class를 분리했음에도 불구하고, 여전히 로그, 트랜잭션, 자원해제, 성능테스트, 등 처럼 공통적으로 반복되는 중복코드 ( 횡단 관심사 ) 가 나오는 단점을 해결하고자 나온 방식 
- 개발코드에서는 비지니스 로직에 집중하고 실행시 비지니스 로직 앞, 뒤 등 원하는 지점에 해당 공통 관심사를 수행할 수 있게 함으로써 중복 코드를 줄일 수 있는 방법


## 9. DI


## 10. service layer


## 11. Spring 빈관리
간단하게 한줄로 답하자면 스프링 빈이란 자바 객체입니다.
스프링 컨테이너(Spring Container)에 의해서 자바 객체가 만들어 지게 되면 이 객체를 스프링은 스프링 빈이라고 부르는 것입니다.
스프링 빈과 자바 일반 객체와의 차이점은 없습니다. 다만 스프링 컨테이너에서 만들어지는 객체를 스프링 빈이라고 부를 뿐이죠.


## 12. 마이크로서비스란? 
## 13. 도커란? 
## 14. 회사에서 개발한 마이크로서비스 아키텍처에 대하여 
## 17. Spring 서비스 추상화란? 
## 18. 서비스 장애 대응? 
## 19. API 게이트웨이? 
## 20. 객체지향이란? 
## 21. SOLID 법칙 
## 22. 캡슐화에 대하여? 

## 23. 스프링의 configuration option 은?
XML, Annotations, Java, Groovy, DSL

## 24. SOLID 의 S 의 기능?
Single Responsibility Principle

## 25. SpringFramework 5에서는 XML Configuration이 아직 지원된다.

## 26. Dependency Injection은 생성자 방식을 지향하는이유는?
클래스가 초기화 되었을 때 의존성을 주입하기 위해서이다.

## 27. ComponentScan이 어떤 Annotation을 스캔하는지?
Spring's Stereotype annotation 을 scan한다. @Controller, @Service, @Component, @Repository

## 28. Java class를 Spring configuration으로 쓰려면 어떤 annotation을 쓰는지?
@Configuration

## 29. Java configuration class 안에 어떻게 spring component를 정의하는지?
@Bean 

## 30. 2개의 bean (같은 타입)이 있는데 어떻게 한쪽의 preference를 갖게 하는지?
@Primary annoation이 primary bean을 설정한다.

## 31. Spring Bean의 lifecycle에 접근하는 2가지 annotation은?
@PostConstruct, @PreDestory

## 32. @RestController가 Spring StereoType인가?
기술적으로, @Controller와 @ResponseBody 를 합치기 위한 편리한 annoation이다.

## 33. SpringBoot Maven project가 왜 Spring Boot Parent POM을 상속받는지?
Compatible하게 하기 위해서

## 34. Spring Sterotype이 어떤 annoation을 상속하는지?
@Component

## 35. Ant로 Spring Boot을 빌드할 수 있는지?
가능, Ivy 사용해야함

## 36. Spring Boot Starter 가 무엇인가?
Spring Boot Starter는 POM으로써 dependency들의 공통 집합이다. (기본 설정같은 것) 대부분 자바 프로젝트에 가능하다.

## 37. @Repository의 특별한 점?
DAO관련 특정 예외를 잡을 수 있다 = 스프링이 specific persistence exception을 잡는다. (persistence는 영속성을 의미한다.) 
그리고 Spring exception으로 다시 던져준다.

## 38. @SpringBootApplication은 3가지의 다른 annotation들을 가지고 있다. 무엇인가?
@Configuration, @EnableAutoConfiguration, @ComponentScan

## 39. auto-configuration을 springboot에서 어떻게 실행하는지?
Start Spring Boot에서 커맨드라인에 --debug를 한다.

## 40. 특정 auto-configuration 클래스를 disable할 수 있는가?
@EnableAutoConfiguration안에 exclude 인자를 넣어준다.

## 41. Spring scope의 default는 무엇인가?
Singleton Scope 이다.

## 42. custom bean scope를 생성할 수 있는가?
가능하다. (extensible하니까)

## 43. Prototpye에는 bean이 어떻게 생성되는가?
매 요청 마다 새로운 bean instance를 생성한다.

