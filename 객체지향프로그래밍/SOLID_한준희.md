# 객체지향 설계 원칙 SOLID

객체지향 프로그래밍을 설계할 때 지켜야 하는 5가지 원칙이 있다.

- S: 단일 책임 원칙 (SRP; Single Responsibility Principle)  
  모든 클래스는 반드시 단 하나의 책임만을 가져야 한다.  
  -> 메서드 등으로 다른 객체를 변경할 때 하나만 변경되어야 함

- O: 개방 폐쇄 원칙 (OCP; Open-Closed Principle)  
  확장에는 열려있고 수정에는 닫혀있다.  
  -> 기존 코드를 건드리지 않고 신규 기능을 넣을 수 있어야 한다.

- L: 리스코프 치환 원칙 (LSP; Liskov Substitution Principle)  
  부모 객체를 호출하는 동작에서  
  자식 객체가 부모 객체를 완전히 대체할 수 있어야 한다.

- I: 인터페이스 분리 원칙 (ISP; Interface Segregation Principle)  
   객체는 자신이 호출하지 않는 메소드에 의존하지 않아야 한다.  
   -> 부모 객체가 큰 경우에 자식이 필요 없는 메소드까지 상속받으면 안된다.

  [SOLID-인터페이스 분리 원칙](https://blog.itcode.dev/posts/2021/08/16/interface-segregation-principle)

- D: 의존 역전 원칙 (DIP; Dependency Inversion Principle)
  "구체화에 의존하지말고 추상화에 의존해야한다."
  ![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcJfGAM%2FbtrB6t0bt86%2FX159MJJzXmoAdc0g1S6fO0%2Fimg.png)
