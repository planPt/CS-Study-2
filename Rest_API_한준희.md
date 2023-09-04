# Rest API

REST는 3가지로 구성이 되어있다.

1. 자원 : HTTP URL
2. 자원에 대한 행위(Verb) : HTTP Method
3. 자원에 대한 행위의 내용 (Representations) : HTTP Message Pay Load

REST는 모든 웹 서비스를 만드는 6가지 아키텍처 제약 조건을 정의한다.

1. 균일 인터페이스 (Uniform interface)
2. 클라이언트-서버 (Client-server)
3. 상태 비저장 (Stateless)
4. 캐시 가능 (Cacheable)
5. 계층형 시스템 (Layered system)
6. 주문형 코드(선택 사항) (Code on demand(Optional))

[What is REST](https://restfulapi.net/)

RESTful하게 만든 API는 요청을 보내는 주소만으로도 어떤 것을 요청 하는지 파악이 가능하다.  
-> 가독성

Rest API : Rest의 원리를 따르는 API

관련 질문

1. REST에서 지원하는 HTTP 메서드?
   GET, POST, PUT, DELETE 등등

2. PUT과 POST의 차이점?
   POST와 달리 동일한 PUT요청을 여러번 전송해도 결과는 동일하다.

3. RESTful 웹 서비스의 단점?
