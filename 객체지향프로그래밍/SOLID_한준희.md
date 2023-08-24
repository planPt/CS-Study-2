# 객체지향 설계 원칙 SOLID

객체지향 프로그래밍을 설계할 때 지켜야 하는 5가지 원칙이 있다.

## S: 단일 책임 원칙 (SRP; Single Responsibility Principle)

**모든 클래스는 반드시 단 하나의 책임만을 가져야 한다.**  
 -> 메서드 등으로 다른 객체를 변경할 때 하나만 변경되어야 함

객체가 담당하는 동작(책임)이 많아질 수록 해당 객체의 변경에 따른 영향도의 양과 범위가 커진다.  
-> 특정 객체의 책임 의존성 과증을 최대한 지양하기 위한 원칙

## O: 개방 폐쇄 원칙 (OCP; Open-Closed Principle)

**확장에는 열려있고 수정에는 닫혀있다.**  
 -> 기존 코드를 건드리지 않고 신규 기능을 넣을 수 있어야 한다.  
 -> 기능이 변하거나 확장되는 것은 가능하지만 그 과정에서 기존의 코드가 수정되지 않아야 한다.  
 -> 객체 간의 의존성을 최소화하여 코드 변경에 따른 영향력을 낮출 수 있다.

[![](https://velog.velcdn.com/images/harinnnnn/post/10489f56-5d4a-4ba8-a134-8da46e88283c/image.png)](https://velog.io/@harinnnnn/OOP-객체지향-5대-원칙SOLID-개방-폐쇄-원칙-OCP)

## L: 리스코프 치환 원칙 (LSP; Liskov Substitution Principle)

**"프로그램의 객체는 프로그램의 정확성을 깨뜨리지 않으면서 하위 타입의 인스턴스로 바꿀 수 있어야 한다."**  
 부모 객체를 호출하는 동작에서  
 자식 객체가 부모 객체를 완전히 대체할 수 있어야 한다.  
 -> 올바른 상속을 위해 자식 객체의 확장이 부모 객체의 방향을 온전히 따르도록 권고하는 원칙

> 직사각형⊃정사각형

이 아닌

> 사각형⊃정사각형

## I: 인터페이스 분리 원칙 (ISP; Interface Segregation Principle)

객체는 자신이 호출하지 않는 메소드에 의존하지 않아야 한다.  
 -> 부모 객체가 큰 경우에 자식이 필요 없는 메소드까지 상속받으면 안된다.

-> 개방-폐쇄 원칙을 준수하고 인터페이스 분리원칙을 준수 할 경우 자연스럽게 준수가 된다고 한다.

![](https://user-images.githubusercontent.com/50317129/128585790-a761f795-b4da-4a52-865d-d2dd4b858f20.png)

[SOLID-인터페이스 분리 원칙](https://blog.itcode.dev/posts/2021/08/16/interface-segregation-principle)

## D: 의존 역전 원칙 (DIP; Dependency Inversion Principle)

"구체화에 의존하지말고 추상화에 의존해야한다."

[![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcJfGAM%2FbtrB6t0bt86%2FX159MJJzXmoAdc0g1S6fO0%2Fimg.png)](https://blog.hexabrain.net/395)

의존성 주입은 이 원칙을 따르는 방법 중 하나이다.
