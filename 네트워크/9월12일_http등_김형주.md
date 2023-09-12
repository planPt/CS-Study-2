# HTTP 1.0 ~ 3.0

## HTTP

- HyperText Transfer Protocol의 약자로써, 서버와 클라이언트가 인터넷 상에서 데이터를 주고받기 위한 규약이다.
- TCP/IP 5계층에서 Application Layer에 속하는 프로토콜이다.

## HTTP의 특징

- **무상태(Stateless)** 하다. 각각의 요청을 독립적으로 처리하므로, **각각의 요청을 보내기 전에 서버와 연결하는 과정을 필요로 한다.** 요청에 대한 응답이 이루어지면 연결은 유지되지 않는다.
  - 클라이언트의 상태를 저장하지 않는 것이 **stateless** 이다.
    - **첫 번째 요청과 두 번째 요청이 서로 영향을 받지 않는다.**

## HTTP 1.0

- 1.0 버전이 1996년에 상용화되어 사용되기 시작했다.
- 단순한 구조를 가진다. open / operation / close
- TCP Connection당 하나의 URL만 fetch하며, 매번 응답이 끝나면 연결이 끊긴다.

## HTTP 1.0의 문제

- 한 번의 connection에 하나의 (요청, 응답)만 이루어지는 형식 때문에, 매 연결 간 계속 handshake가 일어나야 한다. (time cost의 증가)

## HTTP 1.1

- Persistent Connection을 지원한다. (1.0에서의 문제)
  - 굳이 connection 헤더를 사용하지 않아도 기본적으로 이런 특성을 제공한다.
- 1.0에서는 연결 한 번에 요청/응답이 한 번 이루어지고 TCP 연결이 종료됐지만, 1.1에서는 이것이 개선되었다.
- HTTP Pipelining 개념이 등장하였다.

<img src="network_pipe.png" width="70%">

- 한 요청과 응답이 이루어져야 다음 요청이 갈 수 있던 방식이 아닌, 한 요청이 전송되기 전에 다른 요청 전송이 가능해진 방식이다.

### 문제점

- **HOL(Head of Line) Blocking** : 앞선 요청에 의해 뒤의 요청이 지연되는 것을 의미한다. **(요청이 순차적으로 이루어짐 -> pipelining에서의 문제)**
  - 앞선 데이터(패킷)의 응답이 지연될 때 뒤의 요청이 지연되는 현상이다. 이는 HTTP 1.1에서 발생하는 문제에 해당한다.
- 헤더의 **중복 전송**으로 인해 불필요한 자원으로 인한 네트워크 자원 소비 문제가 발생한다.
- Round Trip Time의 문제가 여전히 남아있다.

## HTTP/2

- HTTP 2.0이라고도 불리는 HTTP/2는 Hypertext Transfer Protocol Version 2의 약자로서, 2015년 IETF에 의해 공식적으로 발표된 HTTP/1.1(기존 표준)의 차기 버전이다.
- 구글이 개발한 비표준 개방형 프로토콜 SPDY를 기반으로 하였다.
  - 웹 페이지 부하 레이턴시를 줄이고 웹 보안을 개선하는 목표 면에서 HTTP와 비슷하다. **(웹 페이지의 로딩 시간을 줄이기 위한 목적으로 설계되었다.)**
  - 압축, 다중화, 우선 순위 설정을 통한 레이턴시 감소를 달성한다.

### Binary 프로토콜

- HTTP 1.1과 다르게 데이터를 binary로 변환해서 전송한다.
  - http 1.1에서는 데이터를 텍스트로 전달했다.

### Multiplexing

- 하나의 커넥션 안에서 다수의 독립적인 stream을 동시에 처리할 수 있다.
- Stream: connection에서 client와 server간 바이트의 양방향 흐름에 해당한다.
- Message: 논리적 요청 또는 응답 메시지에 매핑되는 프레임 sequence (Application layer)
- Frame: HTTP 2에서 통신의 최소 단위이다.

## TCP의 특성

- 흐름제어와 혼잡제어를 제공한다. (데이터의 송수신량 조절)
  - 흐름제어 : client와 server 간의 데이터 처리 속도를 조절하여 buffer overflow를 방지한다.
  - 혼잡제어 : 데이터의 송수신량을 조절한다.

## HTTP 3

### 장점

- Zero RTT (다음 connection간 저장된 정보를 사용한다.)
- 패킷 손실에 대한 빠른 대응
- 네트워크 전환 발생 시의 Connection 유지
