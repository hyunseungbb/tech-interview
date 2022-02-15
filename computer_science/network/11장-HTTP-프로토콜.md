### HTTP 프로토콜

- HyperText Transfer Protocol
- www에서 쓰이는 핵심 프로토콜로 문서의 전송을 위해 쓰이며, 거의 모든 웹 애플리케이션에서 사용되는 프로토콜이다.
- 요청, 응답에 기반하여 동작한다는 특징이 있다.



#### HTTP 1.0

- HTML문서를 전송 받은 뒤 연결을 끊고 다시 연결하여 데이터를 전송하는 방식.
- 단순 동작(연결, 요청, 응답, 연결 종료)이 반복되어 통신 부하 문제가 발생한다.

#### HTTP 1.1

- 요청, 응답 후 연결 종료가 아니라 모든 요청 및 응답이 완료된 후 연결을 종료하는 방식
- 부하 문제를 어느정도 개선하였다.



### HTTP 요청 프로토콜

- HTTP Method 설명 중 GET, POST만 사용해야 한다고 하지만 개발자 입장에서 RESTful API 개발시 PUT, DELETE도 사용하는게 원칙임

- 구조
  - Request Line
    - GET /produ/content.asp?code=sch-v210 HTTP/1.1
    - [요청타입] [URI] [HTTP버전]
  - Headers
  - 공백
  - Body
- GET과 POST 메소드의 차이점
  - GET : 서버로부터 데이터를 조회 시 사용
  - POST : 서버에게 데이터를 전송 시 사용

### URL, URI란?

- URI
  - Uniform Resource Identifier
  - scheme
    - ://host:port/path?query


### HTTP 응답 프로토콜

- 구조
  - Status Line
    - ex) HTTP/1.1 200 OK

  - Headers
    - Content-Length
      - 바디의 길이

    - Content-Type
      - 바디의 컨텐츠 종류

    - Cookie
      - 서버로부터 받은 쿠키를 다시 서버에게 보내주는 역할

    - Host
      - 요청된 URL에 나타난 호스트명을 상세하게 표시

    - User-Agent
      - Client Program에 대한 식별 가능 정보 제공

    - Server
      - 사용하고 있는 웹서버의 소프트웨어에 대한 정보를 포함

    - Set-Cookie
      - 쿠키를 생성하고 브라우저에 보낼 때 사용. 해당 쿠키 값을 브라우저가 서버에 다시 보낼 때 사용

  - 공백
  - Body

