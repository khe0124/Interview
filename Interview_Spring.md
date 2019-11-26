# Spring_기술면접

## 1. Framework와 Library의 차이
- 특정 형태의 소프트웨어 문제를 해결하기 위해 상호 협력하는 클래스 프레임과 인터페이스 프레임의 집합, 특정한 틀이다.
- 설계가 되어있는 틀이고 라이브러리는 가져다 쓸 수 있는 기능이 모여있는 공구박스.
- 라이브러리는 프로그램 개발시 재사용이 필요한 기능.
- 흐름에 대한 제어권한이 어디있냐? - 프레임워크는 흐름 자체로 갖고 있는(IoC) vs 라이브러리는 사용자가 흐름 제어

## 2. AOP가 무엇인지 어떻게 동작하는지?
- AOP는 관점지향 프로그래밍으로
- AOP방법은 핵심 기능과 공통 기능을 분리 시켜놓고, 공통 기능을 필요로 하는 핵심 기능들에서 사용하는 방식이다.
- 핵심적인 기능과 부가적인 기능을 분리해서 다음과 같이 부른다.
- 횡단 관심(Crosscut Concern) : 여러 객체에서 공통적으로 작성해야 하는 부분. ex)보안, 로깅, 트랜젝션, 등등 
- 핵심 관심(Core Concern) : 비즈니스 로직.
- 핵심관심이 정의된 각 클래스에서 횡단관심코드를 가지고 와 심어 사용하는 방식인데, 이 기법을 위빙Weaving이라고 한다.
- 위와 같이 흩어진 관심사를 Aspect로 모듈화하고 핵심적인 비즈니스 로직에서 분리하여 재사용하겠다는 것이 AOP의 취지다.

## 3. OOP가 무엇인가?
- 모든 데이터를 오브젝트(객체,물체)로 취급하여 프로그래밍 하는 방법이다. 즉  하나의 객체를 가지고 독립적으로 사용하거나 그것을 부품으로써 재사용이 가능하며 부품끼리를 서로 결합하여 새로운 객체를 만들어 사용 할 수 있다.
- 상속에 해당하는 개념이며 이 개념을 이용해 동일한 패턴을 만든것이 디자인 패턴이다.

## 4. Spring MVC 구조의 처리과정
1) DispatcherServlet : 어플리케이션으로 들어오는 모든 Request를 받는 관문이다. Request를 실제로 처리할 Controller에게 전달하고 그 결과값을 받아서 View에게 전달하여 적절한 응답을 생성할 수 있도록 흐름을 제어한다.
2) HandlerMapping : Request URL 각각 어떤 Controller가 실제로 처리할 것인지 찾아주는 역할
3) Controller : Request를 직접 처리한 후 그 결과를 다시 DispatcherServlet에게 돌려준다.
4) ModelAndView : Controller가 처리한 결과와 그 결과를 보여줄 View에 관한 정보를 담고있는 객체이다.
5) ViewResolver : View관련 정보를 갖고 실제 View를 찾아주는 역할을 한다.
6) View : Controller가 처리한 결과값을 보여줄 View를 생성한다.

## 5. 스프링 필터와 인터셉터의 차이점
스프링에서 사용되는 Filter, Interceptor, AOP 세 가지 기능은 모두 무슨 행동을 하기전에 먼저 실행하거나, 실행한 후에 추가적인 행동을 할 때 사용되는 기능들이다.
그렇다면 요청에 흐름에 따라 필터, 인터셉터, AOP의 차이점에 대해 알아보자.

갑론을박이 많지만, 
- 인코딩이나 보안 관련 처리와 같은 web app의 전역적으로 처리해야 하는 로직은 필터로 구현하고 
- 클라이언트에서 들어오는 디테일한 처리(인증, 권한 등)에 대해서는 주로 인터셉터에서 처리하는듯 하다.

### Filter, Interceptor, AOP의 흐름

- Interceptor와 Filter는 Servlet 단위에서 실행된다. <> 반면 AOP는 메소드 앞에 Proxy패턴의 형태로 실행된다.
- 실행순서를 보면 Filter가 가장 밖에 있고 그안에 Interceptor, 그안에 AOP가 있는 형태이다.

따라서 요청이 들어오면 Filter → Interceptor → AOP → Interceptor → Filter 순으로 거치게 된다.

1. 서버를 실행시켜 서블릿이 올라오는 동안에 init이 실행되고, 그 후 doFilter가 실행된다. 
2. 컨트롤러에 들어가기 전 preHandler가 실행된다
3. 컨트롤러에서 나와 postHandler, after Completion, doFilter 순으로 진행이 된다.
4. 서블릿 종료 시 destroy가 실행된다.

Filter, Interceptor, AOP의 개념
1.  Filter(필터)
말그대로 요청과 응답을 거른뒤 정제하는 역할을 한다.

서블릿 필터는 DispatcherServlet 이전에 실행이 되는데 필터가 동작하도록 지정된 자원의 앞단에서 요청내용을 변경하거나,  여러가지 체크를 수행할 수 있다.
또한 자원의 처리가 끝난 후 응답내용에 대해서도 변경하는 처리를 할 수가 있다.
보통 web.xml에 등록하고, 일반적으로 인코딩 변환 처리, XSS방어 등의 요청에 대한 처리로 사용된다.

```xml
EX)
<!-- 한글 처리를 위한 인코딩 필터 -->
<filter>
    <filter-name>encoding</filter-name>
    <filter-class>org.springframework.web.filter.CharacterEncodingFilter</filter-class>
    <init-param>
        <param-name>encoding</param-name>
        <param-value>UTF-8</param-value>
    </init-param>
</filter>
<filter-mapping>
    <filter-name>encoding</filter-name>
    <url-pattern>/*</url-pattern>
</filter-mapping>
```

해당 필터의 이름은 encoding, 값은 UTF-8인 파라미터를 정의하고 있다. 
필터의 URL-PATTERN을 /*로 정의하면 servlet, jsp뿐만 아니라 이미지와 같은 모든 자원의 요청에도 호출 된다.

[ 필터의 실행메서드 ]
ㆍinit() - 필터 인스턴스 초기화
ㆍdoFilter() - 전/후 처리
ㆍdestroy() - 필터 인스턴스 종료


2. Interceptor(인터셉터)

요청에 대한 작업 전/후로 가로챈다고 보면 된다.

필터는 스프링 컨텍스트 외부에 존재하여 스프링과 무관한 자원에 대해 동작한다. 
하지만 인터셉터는 스프링의 DistpatcherServlet이 컨트롤러를 호출하기 전, 후로 끼어들기 때문에 스프링 컨텍스트(Context, 영역) 내부에서 Controller(Handler)에 관한 요청과 응답에 대해 처리한다.

스프링의 모든 빈 객체에 접근할 수 있다.

인터셉터는 여러 개를 사용할 수 있고 로그인 체크, 권한체크, 프로그램 실행시간 계산작업 로그확인 등의 업무처리

인터셉터의 실행메서드
preHandler() - 컨트롤러 메서드가 실행되기 전
postHanler() - 컨트롤러 메서드 실행직 후 view페이지 렌더링 되기 전
afterCompletion() - view페이지가 렌더링 되고 난 후

3. AOP
OOP를 보완하기 위해 나온 개념 

객체 지향의 프로그래밍을 했을 때 중복을 줄일 수 없는 부분을 줄이기 위해 종단면(관점)에서 바라보고 처리한다.

주로 '로깅', '트랜잭션', '에러 처리'등 비즈니스단의 메서드에서 조금 더 세밀하게 조정하고 싶을 때 사용합니다.
Interceptor나 Filter와는 달리 메소드 전후의 지점에 자유롭게 설정이 가능하다.
Interceptor와 Filter는 주소로 대상을 구분해서 걸러내야하는 반면, AOP는 주소, 파라미터, 애노테이션 등 다양한 방법으로 대상을 지정할 수 있다.

AOP의 Advice와 HandlerInterceptor의 가장 큰 차이는 파라미터의 차이다.
Advice의 경우 JoinPoint나 ProceedingJoinPoint 등을 활용해서 호출한다.
반면 HandlerInterceptor는 Filter와 유사하게 HttpServletRequest, HttpServletResponse를 파라미터로 사용한다.

AOP의 포인트컷
```
@Before: 대상 메서드의 수행 전
@After: 대상 메서드의 수행 후
@After-returning: 대상 메서드의 정상적인 수행 후
@After-throwing: 예외발생 후
@Around: 대상 메서드의 수행 전/후
```

## 6. Spring에서 트랜잭션처리?
스프링 프레임워크를 사용하는 주목할 만한 이유중 하나가 광범위한 트랜잭션 지원이다. 
대표적으로 선언적인 트랜잭션 관리 지원을 많이 사용하며, 
어노테이션 @Transactional을 활용하여 트랜잭션 처리를 한다. 단 몇줄의 코드만으로 다이나믹 프록시와 AOP라는 기술을 통해 크게는 인터페이스 단위에서 작게는 메서드까지 세분화하여 트랜잭션을 컨트롤 할 수 있다.

## 7. 비즈니스 로직과 서비스 로직?
### Business Logic
- 정보의 최종 처리, 핵심적인 로직
한 개의 비즈니스 로직은 한개의 클래스에 정의되는 것이 보통이므로 클래스의 규모가 작은 것이 보통이다
데이터베이스 접속이 필요하면 Data Access Layer를 호출한다

### Service Logic
- 정보의 1차적인 처리, 데이터 유효성 검사, 예외처리, 트랜잭션 처리 등 여러 장소에서 공통적으로 요구되는 로직
뒤에 이어지는 Business Logic에 전달하기 위한 데이터를 가공하는 부분
한 개의 클래스에 많은 메소드가 포함되고 각각의 메소드는 서로 직접적인 연관성이 없는 것이 일반적이다
정보처리를 위한 범용 로직
정보를 1차적으로 검사 및 가공하여 뒤에 이어지는 Business Logic를 호출한다
예) BoardService, MemberSerice, CartService


## 8. Configuration 어노테이션
스프링의 @Configuration 어노테이션은 어노테이션기반 환경구성을 돕는다. 이 어노테이션을 구현함으로써 클래스가 하나 이상의 @Bean 메소드를 제공하고 스프링 컨테이가 Bean정의를 생성하고 런타임시 그 Bean들이 요청들을 처리할 것을 선언하게 된다. 아래는 자바 클래서에서 어노테이션을 포함하는 방법을 보여준다.

## 11. Spring 빈관리
간단하게 한줄로 답하자면 스프링 빈이란 자바 객체입니다.
스프링 컨테이너(Spring Container)에 의해서 자바 객체가 만들어 지게 되면 이 객체를 스프링은 스프링 빈이라고 부르는 것입니다.
스프링 빈과 자바 일반 객체와의 차이점은 없습니다. 다만 스프링 컨테이너에서 만들어지는 객체를 스프링 빈이라고 부를 뿐이죠.
