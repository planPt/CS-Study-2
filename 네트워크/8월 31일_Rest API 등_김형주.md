# 8월 28일 : REST API / 동기 비동기

## HTTP
- HyperText Transfer Protocol의 약자로써, 서버와 클라이언트가 인터넷 상에서 데이터를 주고받기 위한 규약이다.

## REST
- REST(Representational State Transfer) : 월드 와이드 웹과 같은 분산 하이퍼미디어 시스템을 위한 소프트웨어 아키텍처의 한 형식
   - 엄격한 의미로 네트워크 아키텍처 원리의 모음이다.
   - **자원을 이름으로 구분**하여 **해당 자원의 상태**를 주고 받는 것
   - 통신을 위한 규칙을 설립했다고 생각하면 편하다.
      - 자원 : **데이터베이스에 포함된 어떤 것에 대한 정보 모든 것이 자원이 된다.**
      - 상태 : 정보를 들고 있는 것
      1. HTTP URI(Uniform Resource Identifier)를 통해 자원을 명시
      2. HTTP Method(POST, GET, PUT, DELETE, PATCH 등)를 통해
      3. 해당 자원(URI)에 대한 CRUD Operation을 적용하는 것

### API란?
- API : 서로 다른 두 시스템이나 component가 통신하고 상호작용하기 위한 규약이나 인터페이스를 제공하는 것
   - 예시 : API를 식당의 메뉴판이라고 생각해보자!
      - 요청을 custom하고 정해진 규약에 따라 주문을 하는것!
         - 김치찌개를 주문하는데 그냥 김치찌개라 하지않고 메뉴판에 돼지고기김치찌개라 적혀있으면 그걸 주문한다!
      - 웹툰 앱도 API 규약을 잘 보여주는 예시라고 할 수 있다. 네이버 웹툰에서만 볼 수 있는 웹툰이 여기에 모여있다!

### ★ <질문> REST API를 왜 사용할까?
- 가장 대중화된 HTTP 프로토콜을 사용하는 API?
- HTTP 프로토콜을 기반으로 클라이언트와 서버 간의 네트워크 통신을 주 목적으로 한다.
   - 서로 상호작용하기 위한 규칙과 규격을 정한 것.
   - 이를 통해 효율적인 통신이 가능하다.
- 인터페이스 : 두 개 이상의 component 가 서로 통신할 수 있게 하는 매개체

### 통합 자원 식별자 URI
- 인터넷에 있는 자원을 나타내는 유일한 주소를 의미한다.
- URI의 하위 개념으로는 **URL과 URN**이 있다.
   - **URL** : Uniform Resource Locator의 약자이며, 통칭 **web address** 이다.
      - 네트워크 상에서 자원이 어디에 위치하는지를 알려주기 위한 규약이다.
      - <*scheme>://<*host>:<*port>/<*path>?<*searchpart>
      - https://search.naver.com/search.naver?where=nexearch&sm=top_hty&fbm=0&ie=utf8&query=%EC%9D%B8%ED%95%98%EB%8C%80%ED%95%99%EA%B5%90
      - 위의 주소 예시를 참고하면서 비교하면 쉬울 듯?
         - **scheme**은 브라우저가 사용할 규약(프로토콜)의 내용이다. HTTP URL의 경우 이 자리에 **HTTP**가 들어간다.
         - **host**는 요청이 도달할 서버를 나타낸다. 일반적으로 도메인 네임을 사용하나, IP address를 직접 사용할 수도 있다.
            - 예를 들어 www.naver.com, www.google.com 이나 기타 IP주소가 들어간다.
         - **port**는 서버에서 프로그램이 사용하는 소켓을 구분한다.
            - http는 80, https는 443으로 설정되어 있다.
         - **path**는 서버에서 자원의 경로에 해당한다.
         - **searchpart** 또는 **query**는 서버에 전달할 파라미터에 해당한다. **key=value** 쌍으로 표시하고 이 쌍이 여러 개일 경우 &로 구분한다.
      - URL에서는 #<*fragment> 개념을 포함하지 않고 ?<*query> 까지만 포함된다.

## HTTP URI (2)
- 따라서, URI의 표현 방법은 아래와 같다.
   -  scheme:[//[user[:password]@]host[:port]][/path][?query][#fragment]
      - **fragment**는 html 요소의 id를 가르켜 해당 지점으로 스크롤을 이동한다.

## URN(Uniform Resource Name)
- 리소스를 나타내는 유일하고 지속적인 식별자(Identifier)이다.
   - 리소스에 부여된 고유의 식별자이므로, 리소스의 위치가 바뀌어도 유지된다.
   - <*URN> ::= "urn:" <*NID> ":" <*NSS>

## CRUD Operation
- **CRUD**는 대부분의 컴퓨터 소프트웨어가 가지는 기본적인 데이터 처리 기능인 Create(생성), Read(읽기), Update(갱신), Delete(삭제)를 묶어서 일컫는 말이다.
   - Create : 데이터 생성 (POST)
   - Read : 데이터 조회 (GET)
   - Update : 데이터 수정(PUT, PATCH)
   - Delete : 데이터 삭제(DELETE)

## REST API의 상태 코드
- HTTP 요청에 대한 응답으로 반환되는 **숫자 코드**이다.
   - 예를 들어, 404의 경우에는 해당하는 데이터를 찾을 수 없을 때 표기되는 반환 코드이다.

## REST API의 특징
- REST API에서의 resource는 웹 서비스에서 제공하는 데이터이다.
   - 이는 URI로 식별되며, **각 URI는 고유하다.**
- REST는 **무상태(Stateless)** 하다. 각각의 요청을 독립적으로 처리하므로, **각각의 요청을 보내기 전에 서버와 연결하는 과정을 필요로 한다.** 요청에 대한 응답이 이루어지면 연결은 유지되지 않는다.
   - 클라이언트의 상태를 저장하지 않는 것이 **stateless** 이다.
      - **첫 번째 요청과 두 번째 요청이 서로 영향을 받지 않는다.**
   - 상태 저장이 없으므로, 매 요청 간 더 많은 양의 데이터를 보내야 한다.
   - 이 때 상태 유지 간 필요한 정보는 쿠키나 세션에 저장한다.
- REST에서는 **계층화된 시스템(Layered System)을 만들 수 있다.**
   - 클라이언트는 REST API Server만 호출한다.
   - API Server에서는 순수 비즈니스 로직만 수행하고 그 앞에 보안이나 암호화 과정 등을 추가하여 구조상의 유연성을 줄 수 있다.
      - 로드밸런싱, 공유 캐시 등을 통해 확장성과 보안성 향상이 가능하다.
- URI로 지정한 Resource에 대한 조작을 통일된 인터페이스로 수행한다.
   - 즉 **특정 언어나 기술에 종속되지 않는다.**

## Load Balancing

- Pull migration
  - Idle한 processor가 non-idle한 process의 프로세스를 가져온다.
- Push migration
  - 주기적으로 특정 task가 프로세서의 load를 check한다.
- 자주 load-balacing 한다는 것은 affinity를 깨드릴 수 있으므로, 적당한 수준을 요한다.

※ 참고1 : https://hahahoho5915.tistory.com/54

※ 참고2 : https://e2e2e2.tistory.com/14

※ 참고3 : https://khj93.tistory.com/entry/%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-REST-API%EB%9E%80-REST-RESTful%EC%9D%B4%EB%9E%80

## 동기 / 비동기 처리 방식
- **동기** : 작업이 순차적으로 진행된다.
   - 작업 간의 의존성이 높을 때 사용하는 방식이다.
   - 한 작업이 완료(응답을 받기 전)되기 전에 **다른 작업은 block 된다.**
   - 따라서 요청과 응답의 순서가 정해져 있다(보장된다).
   - 따라서 대량의 작업이 존재할 경우 **starvation**이 발생할 수 있다.
   - 인터럽트의 장점을 사용할 수 없는 처리 방식이기도 하다.
- **비동기** : 어떤 작업이 종료되지 않아도 다른 작업을 수행할 수 있다.
   - multithreading이 비동기에 해당한다.
   - I/O request나 네트워크 호출 같은 긴 response time이 필요할 때 적합하다.

## Multithreading Models

### 1. User-Level Threads (ULTS)

- Thread 관리가 **user 공간의 thread library에서 진행**된다.
- 빠르다는 장점이 있다.
  - Thread간 switch가 kernel에서 일어나는 것이 아니다. **즉, mode switch overhead가 없다.**
- 단, kernel이 모르기 때문에 multithreading의 장점을 다 사용할 수 없다.
- 또한 thread 하나가 block되면 모든 process가 block될 것이다.

### 2. Kernel-Level Threadsd (KLTS)

- Multiprocessor에서 multithreading이 가능하다.
  - 즉, multithreading의 장점을 전부 가져갈 수 있다.
- 단, 위와 달리 **mode switch의 비용**이 발생한다.