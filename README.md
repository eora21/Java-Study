# JAVA

> C#이랑 비슷하지만 약간 다름, 언어 하나쯤 더 공부하는것도 나쁘지 않지
>
> C#도 온전히 내 걸로 만들지 못 했으니, JAVA 처음부터 차근차근 보면서 공부해보자!



## package

- package란?
  - 여러 클래스들의 이름을 디렉터리로 계층 구조화해 체계적으로 관리하는 것
  - 유형 충돌을 피하기 위해 사용함
  - 만약 package를 명시하지 않은 클래스와 인터페이스는 모두 `이름없는 패키지`에 포함되게 된다. 따라서 패키지를 명시하지 않은 모든 클래스와 인터페이스는 같은 패키지에 포함되는 것과 같다.
  - 소속.프로젝트.용도 순으로 네이밍해 주는 걸 추천



- C#의 namespace와 무슨 차이가 있는가?
  - C# namespace
    - 클래스를 구성하고 관리하는 영역을 구상한다.
    - using을 이용하여 네임스페이스에 간단히 접근할 수 있다.
    - 별칭을 부여할 수 있다.
- JAVA package는 유사한 유형의 클래스 및 인터페이스를 그룹화하여 코드 유지 관리 용이성을 향상시키며 이름 충돌을 방지하고 액세스 보호를 제공한다.
- 즉, **namespace는 클래스의 논리적 구분**인 반면 **package는 관련 클래스 및 인터페이스의 조직화된 집합**이다.



## JAVA의 특징

- C++, C# 같은 경우 컴파일 시 OS 종속적으로 프로그램이 구성된다.
- JAVA는 컴파일러가 해당 코드를 바이트코드로 변경시킨 후 JVM에서 해석하여 구성한다 => OS에 비종속적이다!
  - JVM에 따라 bool이 1비트가 쓰여질 수도 있고, 아닐 수도 있다. 신기..
- 객체지향 언어이므로 멤버 변수, 메서드를 가진다.
- .java 파일의 파일명은 해당 파일의 public 클래스 이름과 같아야 하며, 하나의 파일은 하나의 public 클래스만 가질 수 있다.
  - 가독성이 좋아진다
    - 자바는 C#처럼 sln, namespace로 구조를 유지하는 형태와는 다르다. 해당하는 클래스가 어디에 있는지, 정확히 파일로 구분하여 관리한다면 프로젝트의 구조를 유지, 보수하는 데 도움이 된다.
  - 컴파일러의 효율성과 성능이 향상된다. 컴파일 중 .java와 .class파일을 보다 효율적으로 조회가 가능하며, 이는 클래스 로딩의 향상으로 이어진다.
    - .java - > 자바 컴파일러 -> .class -> 자바 인터프리터 -> 기계어
- 자바는 클래스 단일 상속(is a)만 지원한다.
  - 대신 interface와 포함 관계(has a)로 극복한다.
    - 2개 이상의 클래스에서 특성을 가져올 때 하나는 상속(extends), 나머지는 멤버 변수로 처리
  - 어떤 클래스를 상속받을지는 문법적인 문제가 아니며, 프로젝트의 관점 문제이다.
- Annotation
  - 소스코드에 메타 데이터를 삽입하는 형태
  - 코드에 대한 정보 추가 -> 소스 코드의 구조 변경, 환경 설정 정보 추가 등의 작업 진행
  - @Deprecated, @Override, @SuppressWarnings 등
  - IDE가 해당 Annotation에 대해 언급해 줌



## Type

>  변수에 저장되는 데이터의 정류

- Primative Type(기본형)

  - 미리 정해진 크기의 Memory Size로 표현
  - 변수 자체에 값 저장

  

- Reference Type(참조형)

  - 미리 정해질 수 없는 데이터의 표현
  - 변수에는 실제 값을 참조할 수 있는 주소만 저장
  - 미리 만들 수 없는 데이터를 별도의 공간(heap)에 표현하고 그 공간의 주소를 저장



## 접근 제한자

> package에서 오는 C#과의 차이점이 꽤 크다. 주의할 것!

![image-20211227203730391](README.assets/image-20211227203730391.png)



- 클래스는 public과 package로만 이루어지며, package가 default이다.
- package의 범위는 말 그대로 package까지다! 일관성 있어 좋은걸..?
- public은 언제나 열려있다.



## Interface

> 사용만 많이 했지, 제대로 알지 못했던 것 같다. 이번 기회에 개념 확실히 잡을 것!



### 인터페이스란?

서로 다른 두 시스템, 장치, 소프트웨어 따위를 서로 이어 주는 부분, 또는 그런 접속 장치

프로그램과 사용자 사이의 접점



- 유저의 입장
  - 누르면 저장 되겠지? => 실행(호출)하면 동작(메서드)를 통해 결과(리턴)이 오겠지?
  - 어떻게 동작되지?는 궁금하지 않음
  - 호환되기만 한다면 동작되겠지~
  - 선언부만 필요
- 개발자의 입장
  - 누군가가 인터페이스를 동작시킨다면 **어떻게** 행동할 지 고민
- 사용과 구현의 관심으로 나뉘어진다



#### 인터페이스 작성

- 최고 수준의 추상화 단계: 모든 메서드가 abstract 형태
  - JDK8에서 default method와 static method가 추가
    - body를 가진다!
    - 접근 제한자는 public으로 한정, 코드문장을 생략 가능
    - abstract라면 상속받은 클래스에서 무조건 구현해야 하나, default를 사용하면 반드시 구현할 필요가 사라지므로 이미 프로젝트 구조가 크게 작성된 경우 재정의를 일일히 하지 않아도 되기 때문에 편리함
    - 그러나 충돌이 일어날 수 있음, 다행히도 default는 클래스의 메소드, 인터페이스의 메소드와 이름이 겹칠 시 우선순위가 낮음
    - static 메서드는 이미 메모리에 올라가 있기 때문에 바로 호출해서 사용 가능
- 형태
  - 클래스와 유사하게 interface 선언
  - 멤버 구성
    - 모든 멤버변수는 public static final이며 코드문장을 생략 가능(default가 public static final)
    - 모든 메서드는 public abstract이며 코드문장을 생략 가능(default가 public abstract)



#### 인터페이스 상속

- 클래스와 마찬가지로 인터페이스도 extends를 이용해 상속이 가능
- 클래스와 다른 점은 **다중상속**이 가능
  - 어차피 body가 없으니 헷갈릴 메서드 구현 자체가 없다!



#### 인터페이스 구현과 객체 참조

- 클래스에서 implements 키워드를 사용하여 interface 구현
  - 모든 abstract 메서드를 overide해야 한다.
  - 구현하지 않을 경우 abstract 클래스로 표시해야 한다.
- 여러 개의 interface를 implements 가능하다!



#### 인터페이스의 필요성

- 구현의 강제로 표준화 처리
- 인터페이스를 통한 간접적인 클래스 사용으로 손쉬운 모듈 교체 지원
- 서로 상속의 관계가 없는 클래스들에게 인터페이스를 통한 관계 부여로 다형성 확장
- 모듈 간 독립적 프로그래밍 가능 => 개발 기간 단축



## 기타 문법 및 사용법

- 인코딩 확인
  - workspace를 UTF-8로 변경하여 환경 구축



- 간단한 형변환
  - float f = 10f / 3F
  - 숫자의 형을 float으로 바꾸려면 f 또는 F로 할 수 있다. double 등도 마찬가지



- 실수를 이용한 계산 값을 정확히 나타내고 싶을 때
  - BigDecimal을 사용



- 라벨
  - outer: for (int i = 0; i < 100; i++)
    - 반복문 자체를 outer라는 라벨로 선언
  - break outer;
    - outer 자체를 중지
  - continue outer;
    - outer 자체를 반복
  - 다중 반복문에서 flag를 쓰지 않아도 된다!



- 사용자에게 Input을 받으려면
  - Scanner sc = new Scanner(System.in);
  - sc.close();
    - using처럼 자원 반납까지 간편하게 하고 싶다면 try와 함께 사용



- String에서 char를 가져올 때
  - 배열처럼 idx로 접근할 수 없음!
  - charAt(idx)로 가져올 것



- 다차원 배열 선언
  - 대괄호의 자리는 크게 상관이 없다
    - `int[][] arr`
    - `int [] arr []`
    - `int arr [][]`
  - 가독성이 좋게끔 선언할 것
  - new 뒤에 해당 공간을 지정해주거나, 혹은 중괄호로 value를 지정해줄 수 있다.



- 배열에 도움이 될 유틸은 java.util.Arrays에 있다.
  - 다차원 배열을 toString할 경우, .deepToString을 사용해야 한다.



- 여러 인자 한번에 넘기기

  - ```java
    public static void func(int... params) {
    ```



- 이미 알고있는 패키지 임포트
  - 코드 먼저 치고 ctrl + shift + o



- super
  - C#의 base, 부모에 접근



- get, set
  - C#처럼 간결하게는 불가하지만, IDE에서 간단하게 제공해준다!
  - 직접 작성하려면 메소드로 작성!



- isinstanceof
  - C#의 is, 해당하는 객체가 본연의 객체를 지닌 녀석인지 확인



- abstract
  - 추상 클래스
  - 구현의 강제를 통해 프로그램의 안정성 향상
  - C#에서도 있었지만, 잘 활용은 하지 않았었다.. 이번에 제대로 사용해볼 것!



- generic type wild card
  - <? extends T>
    - T 또는 T를 상속받은 타입들만 사용 가능
  - <? super T>
    - T 또는 T의 조상 타입만 사용 가능



- exception handling
  - getMessage
    - 발생된 예외에 대한 구체적인 메세지를 반환
  - getCause
    - 예외의 원인이 되는 Throwable 객체 또는 null 반환
  - printStackTrace
    - 예외가 발생된 메서드가 호출되기까지의 메서드 호출 스택 출력, 디버깅의 수단으로 주로 사용



- try-with-resources
  - try 소괄호에 객체를 선언함으로서 try문이 끝났을 때 자동 close 호출
  - C#의 using과 작동 자체는 같다.
  - 단, 해당 객체들은 AutoCloseable interface가 구현되어있어야만 한다.



- list remove
  - remove 인자가 int라면 해당 index 삭제로 이루어진다
  - 값으로 삭제하려면 remove(Integer.valueOf(1)) 등으로 구현할 것



- 동일한 데이터의 기준
  - equals()가 true를 리턴, hashCode() 값이 같을 것
  - set에 어떠한 class를 new해서 넣어 판단할 경우, 해당 클래스의 equals()와 hashCode() 재정의 필요
    - IDE에서 지원해주는 경우가 있음. 그러나 코드를 잘 이해하고 확인해야 함



- 정렬

  - Comparable을 상속받아야 정렬 가능하다. 상속받으며 정렬 기준을 잡아주어야 한다.

  - 클래스에서 기준을 잡거나, anonymous inner class, 또는 람다로 가능하다.
  
  - ```java
    public class ClassName implements Comparable<ClassName>{
        String some; // 사전에 비교 가능한 기준이 있다면 재사용하기
        ...
        @Override
        public int compareTo(ClassName o){
            //양수: 자리 바꿈, 음수: 자리 유지, 0: 동일 위치
            return this.some.compareTo(o.some);
        }
    }
    ```
  
  - ```java
    Collections.sort(names, new Comparator<String>(){
    	@Override
        public int compare(string o1, string o2){
            return Integer.compare(o1.length(), o2.length());
        }
    });
    ```
  
  - ```java
    Collections.sort(names, (o1, o2)->{
        return Integer.compare(o1.length(), o2.length());
    });
    ```
  
    



