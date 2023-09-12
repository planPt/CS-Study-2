# Rest API

REST는 3가지로 구성이 되어있다.

1. 자원 : HTTP URL
2. 자원에 대한 행위(Verb) : HTTP Method
3. 자원에 대한 행위의 내용 (Representations) : HTTP Message Pay Load
   - JSON 등을 통해 서버와 클라이언트가 주고받는 표현(응답)을 의미

URI -> ID, URL -> 위치 + ID

URI -> 파일의 식별자

자원 : 소프트웨어가 관리하는 모든 것(데이터베이스 안에 있는 데이터)

REST는 모든 웹 서비스를 만드는 6가지 아키텍처 제약 조건을 정의한다.

1. 균일 인터페이스 (Uniform interface)
2. 클라이언트-서버 (Client-server)

   - 자원 요청 -> 클라이언트, 자원있는 -> 서버

3. 상태 비저장 (Stateless)
   - 첫번째 요청에 의해서 두번째 요청이 영향받지 않는다.
   - 클라이언트의 컨텍스트를 서버에 저장하지 않는다.
   - 구현 단순해짐
   - 세션과 반?대
4. 캐시 가능 (Cacheable)
5. 계층형 시스템 (Layered system)
6. 주문형 코드(선택 사항) (Code on demand(Optional))

[What is REST](https://restfulapi.net/)

CRUD operation

- 생성
- 조회
- 수정
- 삭제

REST의 장단점

- 장점

  - HTTP 표준 프로토콜에 따르는 모든 플랫폼에서 사용이 가능
  - REST API 메시지가 의도하는 바를 명확하게 나타냄
  - 디자인 문제를 최소화한다.
  - 서버와 클라이언트의 역할을 분리한다.

- 단점

  - [HTTP Method 형태](https://rachel0115.tistory.com/entry/HTTP-메서드-정리-GET-POST-PUT-PATCH-DELETE)가 제한적이다.
  - 구형 브라우저에서 호환이 되지 않아 지원해주지 못하는 동작이 많다.(익스폴로어)

RESTful하게 만든 API는 요청을 보내는 주소만으로도 어떤 것을 요청 하는지 파악이 가능하다.  
-> 가독성 증가

## REST API

클라이언트와 서버가 서로 상호작용하기위한 규칙과 규격을 정한 것  
자원을 나타내는 URL과 HTTP 메서드를 사용해서 데이터를 처리하고 관리하는 것  
이를 통해서 클라이언트와 서버간의 효율적인 통신이 가능하다.

**Rest API** : Rest의 원리를 따르는 API

자원의 상태를 전달하는 API

URI는 정보의 자원만 표현해야 하며, 자원의 행위는 HTTP Method에 명시한다

REST API를 왜 쓰는가?

- 서버랑 클라이언트 간에 효율적인 네트워크 통신을 위해서

무상태성  
요청의 모습 자체로 요청의 의도 추론 가능

REST API 설계 기본 규칙

1. URL은 정보의 자원을 표현해야한다.
   - 동사보다는 명사, 소문자 복수형으로
     > GET/Student/1 -> GET/students/1
2. 자원에 대한 행위는 HTTP 메서드로 표현한다.
   - 단 URL에 HTTP 메서드나 행위에 대한 동사 표현이 들어가면 안된다.
     > GET / students / show /1 -> GET /students/1

설계 규칙

1. 슬래시(/)는 계층 관계를 나타내는데 사용한다.
   > https://www.acmicpc.net/problem/1000
2. URL 마지막 문자로 슬래시를 포함하지 않는다.
3. 하이픈(-)은 URL 가독성을 높이는데 사용
4. 밑줄은 URL에 쓰지 않는다 -> 가독성을 해침
5. 소문자가 적합
6. 확장자는 URL에 포함하지 않는다.

관련 질문

1. REST에서 지원하는 HTTP 메서드?
   GET, POST, PUT, DELETE, PATCH 등등

2. PUT과 POST의 차이점?
   POST와 달리 동일한 PUT요청을 여러번 전송해도 결과는 동일하다.

3. RESTful 웹 서비스의 단점?

- 어시스턴트가 무국적자의 개념을 고수하기 때문에 RESTful 웹 서비스의 세션을 유지 관리할 수 없습니다.

-> 어시스턴트가 stateless의 개념을 고수하기 때문에 세션 유지가 안된다.

## 인터페이스

- 서로다른 _2개 이상의_ 요소들이 통신할 수 있게 해주는 것

API - A에서 만들어 둔 웹페이지를 B가 사용

- 상호작용을 위해 정해진 규칙
- 서로 다른 두 시스템이나 요소가 통신이나 상호작용하기 위한 규약을 제공하는 인터페이스

API 예시

API는 식당의 메뉴판  
유저가 요청을 커스텀하지 않고 정해진 대로만, 있는거만 보여준다

서비스를 하기위해 만들어둔 하나의 메뉴판
