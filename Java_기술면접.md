# Java_기술면접

## 1. 자바의 특징에 대해 말해보시오.

- OOP(객체 지향 언어) : 부품에 해당하는 객체들을 먼저 만들고, 이것들을 하나씩 조립해 전체 프로그램을 완성하는 개발 기법
- "가비지 컬렉션"에 의한 메모리 자동 관리
- "멀티 쓰레드"를 지원한다.
- JVM 위에서 동작하기 때문에 특정 OS에 종속적이지 않고 이식성이 좋으며, 보안성이 좋다.
- 다양한 Open 라이브러리들이 존재한다.

## 2. 자바를 만든 사람에 대해 아시나요? 
- "제임스 고슬링"

## 3. 변수란?
- "하나의 값을 저장할 수 있는 메모리 공간"

## 4. 객체와 클래스의 차이점에 대해 설명해 보시오.
- 클래스(Class) : 현실 세계의 객체의 속성과 동작을 추려내 필드와 메서드로 정의한 것으로 "아직 메모리가 할당되지 않은 상태"
- 객체(Object) : 이 Class라는 설계도를 기반으로 실제 메모리가 잡힌 것을 의미하며 이런 객체를 조합해 전체 프로그램을 완성해나가는 방식을 OOP(객체지향 프로그래밍)이라고 한다.

## 5. 객체 지향 PG이란? 또 그 특징은?
- 현실세계의 객체를 필드와 메서드로 정의한 Class를 기반으로 실제 메모리가 잡혀 만들어진 부품과 같은 객체들을 조합해 전체 프로그램을 완성해 나가는 개발 기법이다.
- 캡슐화, 은닉화 : 외부 객체에서 구현방식은 알 수 없도록 숨기고 별도로 접근할 수 있는 getter/setter 메서드를 통해 접근하도록 하는 방식
- 상속 : 부모 Class를 자식이 접근할 수 있도록 물려 받는 방식
- 다형성 : 부모 클래스 타입으로 해당 부모를 상속받는 여러 자식 class를 대입할 수 있는 성질등을 들 수 있다.

## 6. 다형성이란?
- 서로 다른 클래스로부터 만들어진 객체지만 같은 부모의 Class 타입으로 이들을 관리할 수 있는(=대입될 수 있는) 성질

## 7. 자바의 메모리 영역(간단하게 설명)
- 메서드 영역 : static 변수, 전역변수, 코드에서 사용되는 Class 정보 등이 올라간다. 코드에서 사용되는 class들을 로더로 읽어 클래스별로 런타임 필드데이터, 메서드 데이터 등을 분류해 저장한다.
- 스택(Stack) : 지역변수, 함수(메서드) 등이 할당되는 LIFO(Last In First Out) 방식의 메모리
- 힙(Heap) : new 연산자를 통한 동작할당된 객체들이 저장되며, 가비지 컬렉션에 의해 메모리가 관리되어 진다.

## 8. 추상메서드? 추상 클래스?
- 추상메서드 : 메서드의 정의부만 있고 구현부는 있지 않은 메서드
- 추상 클래스 : 추상메서드를 적어도 하나 이상 가지고 있는 클래스로 자식클래스에서 오버라이딩(재정의)가 필요한 추상메서드를 가지고 있기 때문에 객체화 할 수 없다.

## 9. 인터페이스(Interface)란? 또 왜 사용하나?
- 인터페이스는 모든 메서드가 구현부가 없는 추상메서드로 이루어진 클래스로, abstract 키워드를 붙이지 않아도 자동으로 모든 메서드는 추상메서드로 정의가 된다. 또한 변수도 자동으로 final static 키워드가 붙게 된다.

## 10. 왜 인터페이스를 사용하는가? 
- 팀작업시 개발코드 부분과 객체가 서로 통신하는 접점 역할을 지원하게 되는데, 이는 개발코드에선 객체의 내부 구조를 모르더라도 인터페이스의 메서드 명만 알고 있으면 되기 때문이다. 이를 통해 얻을 수 있는 장점은 해당 메서드를 통해 나오는 결과물을 알고 있기 때문에 다른 팀의 작업을 기다리고 있지 않아도 되며, 또한 해당 객체가 수정될 경우 개발 코드 부분은 수정을 하지 않아도 된다. 또한, 부가적으로 객체를 파일에 쓰기 위해 Serializable 인터페이스를 구현하거나, Collections.sort()를 하기 위해서 Comparable 인터페이스를 상속하는 것, Cloneable 을 구현하는 것처럼 특정 작업을 하겠다라는 "Mark"역할을 해주기도 한다.

## 11. 프로세스(Process) 와 쓰레드(Thread)의 차이점에 대해 아는가?
- 프로세스 : OS가 메모리 등의 자원을 할당해준 실행중인 프로그램을 가리킨다. 이때, 각각의 프로세스는 서로 메모리 공간을 독자적으로 갖기 때문에 서로 메모리 공간을 공유하지 못한다. 따라서 공유하기 위해서는 IPC(InterProcess Communication)과 같은 방식이 필요하다.
- 쓰레드 : 쓰레드는 프로세스 내에서 프로세스의 자원을 가지고 실제로 일하는 "일꾼"과 같으며 각 쓰레드는 독자적인 Stack 메모리를 갖고 그 외의 자원(메모리)는 프로세스 내에서 공유하게 된다.

## 12. 컬렉션프레임워크(CollectionFramework)에 대해 아는만큼 말해 보시오.
- Collection 인터페이스 
- List 인터페이스 : 배열과 유사하되, 추가할때마다 자동으로 Boundary를 늘려주는 구조로, 중복된 데이터를 허용하며, 순서가 존재한다.
ex) - ArrayList : 배열로 구현됐으며, 인접해 있기 때문에 데이터 조회에 매우 빠르다 하지만, 빈번한 삽입, 삭제시 새로 배열을 만들고 데이터를 옮겨야 하기 때문에 LinkedList에 비하여 속도가 느리다.
- LinkedList : 링크 구조로 되어 있기 때문에 조회는 ArrayList에 비해 느리지만, 삽입 삭제시 링크를 끊고 새로 추가되는 데이터에 링크만 연결하면 되기 때문에 삽입, 삭제에 유리하다.
- Vector : 구현 방식은 ArrayList와 유사하지만 Vector를 개선한 것이 ArrayList이다. 또한 Vector의 경우에는 ArrayList와 달리 Synchronized(동기화)가 걸려 있어 여러 쓰레드에서 동시에 접근할 수 없다.
- Set 인터페이스 : 집합처럼 중복된 데이터를 허용하지 않으며, 순서가 없다. 또한, 객체 내부의 중복된 데이터를 배제하고 싶은 경우 Object 클래스의 equals 메서드와 hashCode 메서드의 재정의가 반드시 필요하다.
ex) - HashSet
    - TreeSet : 순서가 있는 HashSet으로 이진 트리 구조로 만들어 졌다. 순서에 맞게 정렬되어 저장되기 위해서 Comparable을 구현해야한다.
- Map 인터페이스 : key와 value 쌍으로 데이터를 저장하며, key는 중복될 수 없고, value는 중복 저장이 가능하다.
ex) - HashMap
    - TreeMap
    - Properties : key value 쌍으로 저장되지만 value의 타입이 String만 가능하다.
    - Hashtable : HashMap과 구조는 같으며, 단지 Synchronized(동기화) 되어져 있다는 점이 다른점이다.
  
## 13. 오버로딩과 오버라이딩의 차이?
- 오버로딩 : 메서드 명은 동일하지만, 매개 변수 타입과 개수를 다르게 해 선언하는 방식
- 오버라이딩 : 상속한 자식에서 부모의 메서드를 재정의하는 방식

## 14. Servlet vs JSP
- Servlet : 자바 언어로 웹 개발을 위해 만들어진 것으로, Container가 이해할 수 있게 구성된 순수 자바코드로만 이루어진 것
- JSP : html 기반에 JAVA 코드를 블록화하여 삽입한 것으로 Servlet을 좀 더 쉽게 접근할 수 있도록 만들어 진 것

## 15. Wrapper Class의 사용이유를 아나요?
기본 data 타입은 객체가 아니어서 Object로 받는 다형성을 지원할 수가 없다. 하지만, 메서드에서 실재로 기본데이터 타입을 다형성으로 넘겨주어야 하는 경우가 빈번히 발생하는데 이때, 기본 데이터 타입을 객체로 변환시켜 전달하기 위해 사용되며 최근에는 AUTO Boxing, AUTO UnBoxing이 지원된다.

## 16. private, protected, public, default 제어자에 대해 설명해 보시오
- private : 같은 class 내부에서"만" 접근이 가능하다.
- public : 어디서든 자유롭게 접근이 가능하다.
- protected : 같은 class 내부 + 상속받은 자식에서는 부모 class에 접근이 가능하다.
- default : 아무 것도 선언하지 않은 경우로 같은 패키지 내부에서만 접근이 가능하다.

## 17. 자바의 제네릭이란??
클래스 내부에서 사용할 데이터 타입을 인스턴스(객체) 생성시에 결정짓는 방식

## 18. OOP 객체지향프로그래밍이란?
데이터를 객체로 취급하여 프로그램에 반영한 것.
순차적 프로그램 동작과 다르게 객체와 객체의 상호작용을 통해 프로그램이 동작하는 것이다.
객체 지향 프로그래밍은 객체, 클래스, 메시지를 이용하여 개발하는 방식으로, 각 구성 
요소에 대한 내용은 다음과 같다. 
(1) 객체(Object): 개체, 속성, 메소드로 구성된 클래스의 인스턴스를 의미한다. 
(2) 클래스(Class): 객체의 타입을 정의하고 객체를 생성하는 틀을 의미한다. 
(3) 메시지(Message): 객체 간의 통신을 의미한다.
OOP의 특징은
- 코드 재사용성이 높다.
- 코드 변경용이
- 직관적 코드분석 가능
- 개발속도 향상
- 상속을 통한 장점 극대화
 
## 19. 객체(Object)가 무엇인가?
객체는 OOP에서 데이터(변수)와 그 데이터와 연관된 동작, 기능, 함수(메소드).
즉, 절차, 방법, 기능을 모두 포함한 개념.
객체는 속성과 기능, 두 종류의 구성요소로 이루어진, 속성과 기능의 집합이다.
객체가 가지고 있는 속성과 기능을 그 객체의 멤버라고 한다.
프로그래밍에서의 객체는 클래스에 정의된 내용대로 메모리에 생성된 것이다.
클래스는 객체를 정의해놓은 것, 객체의 설계도, 틀이고 객체는 그것을 토대로 만든 사물,개념이다.
 
## 20. 클래스는 무엇인가?
클래스란 객체를 정의한 것으로 클래스에는 객체의 모든 속성과 기능이 정의되어있다.
클래스로부터 객체를 생성하면, 클래스에 정의된 속성과 기능을 가진 객체가 생성된다.
완벽한 하나의 프로그램을 하나의 블록으로 묶은 것이다.
클래스의 목적은 프로그램을 모듈화시키는 것이다. 
클래스를 만드는 것은 곧 프로그램을 만드는 것이다.
클래스의 특징은
-캡슐화+정보은닉
  캡슐화는 관련있는 데이터와 함수를 하나로 묶는 것이다.
  정보은닉은 데이터보호를 위해 클래스 외부에서 클래스 멤버변수에 직접적 접근이 불가하게 한 것이다.
-상속:클래스의 멤버변수나 멤버메소드를 상속하거다 상속받는다
-다형성: 클래스의 다양한 모양이나 성질, 부모클래스로부터 상속받은 자손클래스의 다양한 형태로 제어가능 및 이벤트처리
필드 = 멤버변수
클래스의 기본형식은
class 클래스명 {
멤버필드 //데이터선언,저장
생성자 //멤버필드 초기화
메소드//데이터입력,연산,출력
}
 
## 21. 자바의 데이터 타입 중 기본형(원시형) 은 무엇인가?
기본형은 실제 값을 저장하는 공간이다.
자바가 제공하는 기본형은 int, long, short, float, double, boolean, byte, char형 등이 있다.
 
## 22. 자바의 데이터 타입 중 참조형은 무엇인가?
참조형 변수에 객체를 대입하면 객체가 변수에 저장되는 것이 아니라 메모리상에 객체가 있는 위치를 가리키는 주소만 변수에 저장된다.
자바에서 기본형 8가지를 제외하고 모두 참조형이다.
실제 값은 heap영역에 저장되고 stack에는 메모리 주소만 저장된다.
자바에서 제공되는 클래스와 사용자가 만든 클래스 모두 자료형으로 사용될 수 있고,
클래스를 자료형으로 사용하여 저장공간을 만들었을 경우, 생성된 것을 객체라고 한다. 이때 사용된 클래스를 객체의 타입(형)이라고 한다.
참조형 변수는 클래스에 정의된 생성자를 사용하여 만들어진다. 참조형 변수의 default값은 null이다.
참조형변수는 객체를 참조하는데 사용된다.
 
## 23. 자바의 메모리영역에 대해 이야기 하라
JVM이 실행되면 OS가 JVM에 필요한 메모리를 할당해준다.
JVM은 OS로부터 받은 메모리를 나누어 관리한다. 이것을 Runtime Data Area라고 한다.
 
### Method 영역 (Class Area)
바이트코드와 전역변수, static 변수 클래스파일의 바이트코드가 로드되는 곳이다.
메소드 영역에 저장되는 바이트코드는 프로그램의 흐름을 구성하는 바이트 코드이다.
이 바이트코드는 자바 컴파일러에 의해 컴파일된 것들. 
클래스로딩 -> 어떤 메소드가 호출되려면 먼저 그 메소드를 갖고 있는 클래스 파일이 메모리에 로딩되어 있어야 한다. 그래서 클래스를 실행할 때 *.class파일을 찾아서 메모리에 로딩하는 것.
 
### Static 메모리 영역 
하나의 자바파일은 필드,생성자,메소드로 구성된다. 
그 중 필드 부분에서 선언된 변수(전역)와 정적 멤버변수(static이 붙은 자료형) Static 영역에 데이터를 저장한다. 
Static 영역의 데이터는 프로그램의 시작부터 종료까지 메모리에 남아있게 된다.
 
### Stack 영역
매개변수, 지역변수 //사용이 끝나면 바로 소멸된다. 컴파일 시 메모리를 할당한다.
메소드 내에서 정의하는 기본 자료형(int, double, byte, long, boolean 등) 에 해당되는 
지역변수 (매개변수 및 블럭문 내 변수 포함)의 데이터의 값이 저장되는 공간이 Stack영역이다. 
해당 메소드가 호출될 때 메모리에 할당되고 종료되면 메모리가 해제된다.
 
### Heap 영역
new로 생성된 객체 //호출이 끝나도 사라지지 않으며 프로그램 실행 시 동적으로 할당한다.
인스턴스를 생성하는 방법은 "클래스 변수 = new 클래스();" 
참조형(Reference Type)의 데이터 타입을 갖는 객체(인스턴스), 배열 등은 Heap 영역에 데이터가 저장된다.  
이때 변수(객체, 객체변수, 참조변수)는 Stack 영역의 공간에서 실제 데이터가 저장된 
Heap 영역의 참조값(reference value, 해시코드 / 메모리에 저장된 주소를 연결해주는 값)을 new 연산자를 통해 리턴 받는다.  
다시 말하면 실제 데이터를 갖고 있는 Heap 영역의 참조 값을 Stack 영역의 객체가 갖고 있다. 이렇게 리턴 받은 참조 값을 갖고 있는 객체를 통해서만 해당 인스턴스를 핸들 할 수 있다.
 
## 24. 인스턴스가 무엇인가?
인스턴스는 클래스를 통해 표현하는 객체를 실체화한 상태이다.
- 객체를 프로그램에 실체화 하면 그것을 인스턴스라고 한다.
- 실체화된 인스턴스는 메모리에 할당된다.
- 객체는 클래스의 인스턴스다.
- 객체 간의 링크는 클래스간의 연관 관계의 인스턴스다.
- 실행 프로세스는 프로그램의 인스턴스다.
자바에서는 클래스변수, 인스턴스변수, 지역변수 3 종류가 있다.
그 중 클래스변수와 인스턴스변수를 합쳐 멤버변수라고 한다.
인스턴스변수는 클래스 내부에 위치하며 객체를 생성해야 사용할 수 있다.
인스턴스변수의 값을 사용하기 위해서는 인스턴스화 해야한다.
new연산자를 통해 객체생성(new를 사용해 메모리 할당)하는 것이 인스턴스화.
 
## 25. 생성자가 무엇인가?
생성자는 인스턴스 생성할 때 딱 한번 호출되는 메소드이다.
생성자메소드는 인스턴스변수 초기화를 목적으로 정의된다.
클래스를 갖고 객체를 생성하면 해당 객체는 즉시 메모리에 생성된다.
하지만 이렇게 생성된 객체는 모든 인스턴스변수가 아직 초기화되니 않은 상태이다.
클래스 이름과 같은 이름의 메소드여야하며 반환형이 선언되어있지 않으며, 반환하지 않는 메소드여야한다.
인스턴스 생성문과 생성자를 호출하는 호출문이 겹쳐있다.
Number num = new Number();
### 생성자의 특징
- 생성자는 클래스의 이름과 항상 동일해야한다.
- 생성자는 반환값이 없지만, 반환 타입을 void형으로 선언하지 않는다.
- 객체를 초기화하는 방법이 여러개 존재할 경우는 하나의 클래스가 여러개의 생성자를 가질 수도 있다.
- 생성자도 하나의 메소드이므로, 메소드 오버로딩이 가능하다. 자바에서 new연산자로 객체 생성시 자동으로 생성자가 호출된다.
 
## 26. 자바의 메소드가 무엇인가?
메소드는 함수, 기능이다.
자바에서 클래스는 멤버로 속성을 표현하는 필드와 기능을 표현하는 메소드를 가진다.
메소드는 어떤 특정 작업을 수행하기 위한 명령문의 집합이다.
클래스에서 메소드를 사용하는 이유는 중복되는 코드와 반복적 프로그래밍을 피팔 수 있고
모듈화를 통해 코드의 가독성을 좋게 할 수 있다.
1. 접근 제어자 : 해당 메소드에 접근할 수 있는 범위를 명시.
2. 반환 타입(return type) : 메소드가 모든 작업을 마치고 반환하는 데이터의 타입을 명시. 
3. 메소드 이름 : 메소드를 호출하기 위한 이름을 명시. 
4. 매개변수 목록(parameters) : 메소드 호출 시에 전달되는 인수의 값을 저장할 변수들을 명시. 
5. 구현부 : 메소드의 고유 기능을 수행하는 명령문의 집합.  
 
## 27. 메소드오버로딩과 메소드오버라이딩
### 메소드 오버로딩
-클래스 내에서 같은 이름의 메소드를 여러 개 정의하는 것.
-매개변수의 갯수나 타입이 달라야한다.
-반환형과 접근 제어자는 영향을 주지 않는다.
 
### 메소드오버라이딩
-상속에서 나온 개념
-부모클래스의 메소드를 자손클래스에서 재정의하는 것이다.
-오버라이딩 된 메소드는 부모클래스의 메소드보다 우선되어 자손 객체에서 호출 시 오버라이딩된 메소드가 호출됨
-원래 메소드와 동일한 리턴타입, 메소드 이름, 매개변수 리스트를 가져야함.
-상속함으로 통해서 부모클래스의 메소드를 다른 방식으로 사용하기 위해 재정의하는 것.
 
## 28. 상속이 무엇인가?
기존 클래스의 기능을 유지하며 추가적인 기능을 추가하여 클래스를 만들고 싶을 때 사용하는 방법이다.
새로운 클래스 생성 시 extends 상위 클래스를 통해 상위클래스의 모든 기능, 속성을 제공받고
자신의 클래스에는 부가적인 기능, 속성을 추가 할 수 있다. 상속은 코드를 간결화하며, 재사용성을 높인다.
변수와 메소드를 그대로 사용하므로 코드중복을 줄인다.
 
## 29. 접근제한자에 대해 이야기 하라.
public: 모든 접근을 허용함. 
protected: 상속받은 클래스 또는 같은 패키지에서만 접근 가능 
default: 기본 제한자, 자신 클래스 내부와 같은 패키지 내에서만 접근 가능 
private: 외부에서 접근 불가능, 같은 클래스 내에서만 가능
 
## 30. Static이 무엇인가?
클래스가 로딩될 때, 메모리 공간을 할당하는데 처음 설정된 메모리 공간이 변하지 않는 것을 뜻함.
객체를 아무리 만들어도 해당 변수는 하나만 존재한다.
static은 단 하나밖에 생기지 않기 때문에 모든 곳에서 이 하나뿐인 메모리 공간을 같이 쓴다.
특정한 값을 공유해야할 때 static을 쓴다.
 
## 31. String과 StringBuilder와 StringBuffer의 특징과 차이가 무엇인가?
String은 불변객체이다. 문자를 수정하려면 지우고 다시 생성해야한다. 문자열 연산이 많으면 성능이 떨어지는데
StringBuffer는 가변할 수 있다. 한번 생성하고 필요할 때 크기를 변경하여 문자를 변경시킬 수 있다. 
append()처럼.
StringBuilder는 동기화 지원하지 않는다. 멀티 쓰레드 환경에 적합하지 않다. 그러나 싱글쓰레드에서는 StringBuffer보다 낫다.
 
## 32. Final이 무엇인가?
생성자, 상속 중요
변수, 함수, 클래스 확장 못하게 한 것.
변수: 변수의 상수화. 주로 static과 같이 사용한다.
클래스: 누군가의 부모클래스가 될 수 없다. 자식을 둘 수 없음. 상속받기 상속하기 둘 다 불가. //종단클래스
메소드: 더 이상 오버라이드(override, 재정의) 할 수 없다.
 
## 33. Wrapper클래스가 무엇인가?
기본자료형으로 표현된 데이터를 참조자료형으로 만들어야 할 경우 래퍼클래스를 사용한다.
기본 자료형을 참조형화 해놓은 클래스를 말한다.
주로 java.lang패키지게 선언되어있다.
이렇게 8개의 기본타입에 해당하는 데이터를 객체로 포장해주는 클래스로 그것을 박싱이라고 한다.
래퍼클래스는 각각 타입에 해당하는 데이터를 인자로 전달받아, 해당 값을 가지는 객체로 만들어 준다.
보통 특정 메소드에서 참조 자료형을 인자로 받거나, 기본 자료형이 아닌 객체 자료형으로 저장해야할 경우, 
객체간 비교가 필요할 경우에 사용한다.
 

## 34. 다형성이 무엇인가?
하나의 클래스나 함수가 다양한 방식으로 동작 가능 한 것을 말함. 
다형성의 효과는 하나의 타입으로 다양한 실행결과를 얻을 수 있어 객체를 부품화해 유지보수 용이하게 한다.
 자식이 부모에 들어갈 수 있음. 같은 자료형에 여러가지 객체를 대입하여 다양한 결과를 얻어내는 성질.
 
## 35. 추상클래스가 무엇인가?
추상클래스는 추상메서드를 하나 이상 가진 클래스로 자신의 생성자로 객체생성이 불가한 클래스다.
->new 연산자를 사용할 수 없다는 뜻이다. 인스턴스를 생성할 수 없다.
- 일반메소드와 추상메소드로 이루어져있다.
- 클래스에 추상메소드가 하나라도 존재하면 추상클래스이다.
- 일반메소드가 추상메소드를 호출할 수 없다.
- 다른 클래스를 작성하는데 도움을 줄 목적으로 작성된다.
이러한 추상클래스는 OOP에서 중요한 특징인 다형성을 가지는 메소드의 집합을 정의할 수 있도록 해준다.
하위클래스를 참조하여 상위클래스 객체를 생성한다.
하위클래스를 제어하기 위해 사용된다.
 
- 추상: 덜 구체화된 좀 더 포괄적이고 개념적인 것
- 객체: 상태와 기능을 가진 것
- 클래스: 객체를 만들기 위한 설계, 틀
- 초기화: 클래스를 이용하여 객체생성
 
 
## 36. 추상메소드가 무엇인가?
추상메소드는 선언부만 있고 구현부 (body)가 없는 메소드를 말한다. 
꼭 필요하지만 자손마다 다르게 구현될 것으로 예상되는 경우에 사용한다.
추상메소드는 선언만되고 구현이 되지 않은 불완전한 메소드이므로 객체로 생성되어서는 안된다.
추상메소드를 사용하기 위해서는 반드시 해당 메소드를 재정의해야만 한다.
추상클래스를 상속받는 자손클래스에서 추상메소드의 구현부를 완성해야 한다.

 
## 37. 인터페이스가 무엇인가?
인터페이스는 일종의 추상클래스로 오직 추상메서드와 상수만을 멤버로 갖는 클래스다.
Implements 키워드를 사용한다.
상속 관계가 없는 클래스간 서로 공통되는 로직을 구현하여 쓸 수 있도록 한다.
하나만 상속할 수 있는 Extends와 다르게 Interface는 다중상속이 가능하다.


## 38. 컬렉션 프레임웍이란?
다수의 데이터를 쉽게 처리할 수 있는 표준화된 방법을 제공하는 클래스
핵심 인터페이스로는
### List
- 순서가 있는 데이터의 집합, 데이터의 중복을 허용한다.
- 구현클래스: ArrayList, LinkedList, Stack, Vector 등
### Set
- 순서를 유지하지 않는 데이터의 집합, 데이터의 중복을 허용하지 않는다.
- 구현클래스: HashSet, TreeSet 등
### Map
- 키Key와 값Value의 쌍(Pair)으로 이루어진 데이터의 집합이다. 순서는 유지되지 않으며, 키는 중복을 허용하지 않고, 값은 중복을 허용한다.
- 구현클래스: HashMap, TreeMap, Properties 등
 
## 39. 동기화(Synchronization)
멀티쓰레드 프로그래밍에서는 하나의 객체를 여러 쓰레드가 동시에 접근할 수 있기 때문에 데이터의 일관성을 위해서는 동기화가 필요하다.
 
## 40. ArrayList와 LinkedList
- 순차적으로 추가/삭제하는 경우에는 ArrayList가 LinkedList보다 빠르다.
- 중간 데이터를 추가/삭제하는 경우에는 LinkedList가 ArrayList보다 빠르다.
 
## 41. LinkedList와 배열의 차이점은?
- `(배열)` 인덱스를 가짐, 원하는 데이터를 한번에 접근하여 접근 속도가 빠름. 크기 변경 불가.
데이터를 삽입, 삭제 후 그 위치의 다음위치부터 모든 데이터의 위치를 변경해야하는 단점.
- `(연결리스트)` 인덱스 대신 현재 위치의 이전/ 다음 위치를 기억. 크기가 가변적.
한번에 접근 불가, 연결되어 있는 링크를 따라가야 접근 가능하여 배열에 비해 속도가 떨어짐.
데이터 삽입/삭제는 논리적 주소만 바꿔주기 때문에 용이함.
- 데이터 양이 많지만 삽입/삭제 없으며, 데이터 접근이 빈번할 때 (배열 추천)
- 데이터 양이 적고, 삽입/삭제가 빈번할 때 (링크드리스트 추천)
 
## 42. ArrayList<>란?
배열의 확장판이다. 배열의 크기를 임의적으로 변화시킬 수 있으며 list안에 들어가 데이터 타입을 설정할 수 있다.
(add, remove, isEmpty, size, get, indexOf 등의 메소드가 있다.)
 
## 43. 제네릭이란?
클래스에서 사용할 타입을 클래스 외부에서 설정하는 것. 
만들어져 있는 클래스를 내가 원하는 형태로 사용할 수 있다. 
< > 안에 들어갈 수 있는 것은 참조자료형(클래스, 인터페이스, 배열) 뿐. 
기본자료형을 사용하기 위해선 wrapper 클래스를 이용해야 한다.
 
## 44. 컬렉션 클래스에서 제네릭을 사용하는 이유는?
컬렉션 클래스에서 제네릭을 사용하면 컴파일러는 특정 타입만 포함 될 수 있도록 컬렉션을 제한한다.  
컬렉션 클래스에 저장하는 인스턴스 타입을 제한하여 런타임에 발생할 수 있는 잠재적인 모든 예외를 컴파일타임에 잡아낼 수 있도록 도와준다.
 
## 45. Hash란?
내부적으로 배열을 사용(HashTable)하여 데이터를 저장, 검색 속도가 빠름.
데이터 삽입/삭제시 기존 데이터를 밀어내거나 채우지 않고, 데이터와 연관된 고유한 숫자를 생성해
이를 인덱스로 사용.
 
## 46. Call by Reference, Call by Value 
Call by Reference - 매개 변수의 원래 주소에 값을 저장하는 방식. 클래스 객체를 인수로 전달한 경우 
Call by Value - 인수로 기본 데이터형을 사용. 주어진 값을 복사하여 처리하는 방식. 메서드 내의 처리 결과는 메서드 밖의 변수에 영향을 미치지 않는다.
 
## 47. Thread가 무엇인가? 
시스템 내부에서 실행되는 코드의 최소 실행단위를 의미한다. 자바에서는 사용자 프로그램을 통해 쓰레드를 생성하고, 멈추고, 재실행시키는 등의 제어가 가능하다. 쓰레드를 제어한느 작업도 역시 자바가 제공하는 클래스와 인터페이스를 이용한다.
어떤 방식으로 CPU를 할당해서 각 프로세스를 실행할 것인가 하는 것은 OS의 정책에 따라 달라진다. 쓰레드는 바로 이러한 프로세스내의 또 다른 실행단위이다. 자바의 쓰레드는 시분할 방식이 기본이며, 우선순위를 지정해서 실행 순서를 조절할 수 있다.
 
- 프로세스: 운영체제로부터 자원을 할당받는 작업의 단위, OS로부터 메모리, 주소공간 등을 할당받음.
- 쓰레드: 프로세스가 할당받은 자원을 이용하는 실행의 단위이다,  쓰레드는 할당받은 자원들을 내부쓰레드끼리 공유.
 
## 48. 가비지 콜렉터(Garbage Collector)가 무엇인가? 
가비지는 정리되지 않은 메모리, 유효하지않은 메모리 주소를 말한다. 이런 것을 프로그래밍 언어로 Dangling Object라고 하고 자바에서는 쓰레기, 즉 Garbage라고 한다.
가비지 콜렉터는 메모리가 부족할 때 이런 쓰레기(Garbage)를 정리해주는 프로그램을 말한다.
사용하지도 않으면서 공간을 차지하고 있는 메모리를 해제시키는 프로그램이다.
메모리를 부여받은 JVM이 메모리가 부족해서 OS에 추가요청할 때 가비지 콜렉터가 실행된다.
