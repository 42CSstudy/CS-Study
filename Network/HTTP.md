# **HTTP**

## HTTP 정의

## HTTP

### HyperText

HTTP는 HyperText Transfer Protocol의 약자이다.

HTML은 HyperText Markup Language의 약자로, HyperText(웹 페이지에서 다른 페이지로 이동할 수 있도록 하는 것)기능을 가진 문서를 만드는 언어이다.

### Transfer

전송하다의 의미를 가진 Transfer은 우리가 가진 정보를 다른 컴퓨터와 공유해야 할 때 필요한 동작이다.

전송을 **보내는 주체와 받는 주체가 있다**는 것이 특징이다.

### Protocol

프로토콜은 협약이라는 의미를 가지는데 물리적으로 떨어져 있는 컴퓨터들끼리 어떤 규칙으로 HTML파일(HyperText)을 주고 받을것인지에 대한 약속을 프로토콜이라고 한다.

요약하면 HTTP란, 컴퓨터들끼리 HTML파일을 주고받을 수 있도록 하는 소통방식 또는 약속이다.

특징

### Request / Response

사람이 말을 하면 대답을 하듯이 컴퓨터가 요청을 하면 응답을 해야한다.

사람과 컴퓨터의 차이는 사람은 요청과 응답이 다양한 형태로 나타나지만

컴퓨터는 오직 text의 형태로 요청과 응답이 이루어진다(http 요청과 응답은 모두 text)

클라이언트-서버 구조 : 클라이언트는 서버에 요청을 보내고 대기. 서버는 요청 결과를 만들어서 응답을 준다.

### Stateless = State + less

HTTP의 가장 중요한 특징이 Stateless(상태없음)다.

Stateful은 서버가 클라이언트의 이전 상태를 보존한다는 의미이다.

반대로 Stateless는 서버가 클라이언트의 이전 상태를 보존하지 않는다는 의미이다.

각각의 HTTP 통신(요청/응답)은 독립적이기 때문에 과거의 통신(요청/응답)에 대한 내용을 전혀 알지 못 한다. 그러므로 매 통신마다 필요한 모든 정보를 담아서 요청을 보내야 한다.

## HTTP status code

잘 설계된 REST API는 URI만 잘 설계된 것이 아니고 리소스에 대한 응답을 잘 내어주는 것까지 포함되어야 한다. 정확한 응답의 상태코드만으로도 많은 정보를 전달할 수가 있기 때문에 응답의 상태코드 값을 명확히 돌려주는 것은 생각보다 중요한 일이 될 수도 있다.

| 상태코드 | 내용 |
| --- | --- |
| 200 | 클라이언트의 요청을 정상적으로 수행함 |
| 201 | 클라이언트가 어떠한 리소스 생성을 요청, 해당 리소스가 성공적으로 생성됨(POST를 통한 리소스 생성 작업 시) |
| 400 | 클라이언트의 요청이 부적절 할 경우 사용하는 응답 코드 |
| 401 | 클라이언트가 인증되지 않은 상태에서 보호된 리소스를 요청했을 때 사용하는 응답 코드 (로그인 하지 않은 유저가 로그인 했을 때, 요청 가능한 리소스를 요청했을 때) |
| 403 | 유저 인증상태와 관계 없이 응답하고 싶지 않은 리소스를 클라이언트가 요청했을 때 사용하는 응답 코드 (403 보다는 400이나 404를 사용할 것을 권고. 403 자체가 리소스가 존재한다는 뜻이기 때문에) |
| 405 | 클라이언트가 요청한 리소스에서는 사용 불가능한 Method를 이용했을 경우 사용하는 응답 코드 |
| 301 | 클라이언트가 요청한 리소스에 대한 URI가 변경 되었을 때 사용하는 응답 코드 (응답 시 Location header에 변경된 URI를 적어 줘야 한다.) |
| 500 | 서버에 문제가 있을 경우 사용하는 응답 코드 |

## HTTP method (HTTP REST)

`[GET]`

메서드 `GET`는 지정된 리소스의 표현을 요청합니다. 를 사용하는 요청은 `GET`데이터 검색만 해야 합니다.

`[HEAD]`

이 메서드는 요청과 동일하지만 응답 본문이 없는 `HEAD`응답을 요청합니다 .`GET`

`[POST]`

이 `POST`메서드는 엔터티를 지정된 리소스에 제출하며, 종종 서버의 상태 변경이나 부작용을 유발합니다.

`[PUT]`

이 `PUT`메서드는 대상 리소스의 모든 현재 표현을 요청 페이로드로 바꿉니다.

`[DELETE]`

이 `DELETE`메서드는 지정된 리소스를 삭제합니다.

`[CONNECT]`

이 `CONNECT`방법은 대상 리소스로 식별된 서버에 대한 터널을 설정합니다.

`[OPTIONS]`

이 `OPTIONS`방법은 대상 리소스에 대한 통신 옵션을 설명합니다.

`[TRACE]`

이 `TRACE`메서드는 대상 리소스에 대한 경로를 따라 메시지 루프백 테스트를 수행합니다.

`[PATCH]`

이 `PATCH`방법은 리소스에 부분 수정을 적용합니다.

https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods

## REST

REST(Representational State Transfer)의 약자로 자원을 이름으로 구분하여 해당 자원의 상태를 주고받는 모든 것을 의미한다.

좀 더 정확히 말하면

**1. HTTP URI(Uniform Resource Identifier)를 통해 자원(Resource)을 명시하고, 2. HTTP Method(POST, GET, PUT, DELETE, PATCH 등)를 통해3. 해당 자원(URI)에 대한 CRUD Operation을 적용하는 것을 의미한다.**이 세 개의 특징이 HTTP RESTFUL에서 제일 중요하다.

**CRUD Operation** : CRUD는 대부분의 컴퓨터 소프트웨어가 가지는 기본적인 데이터 처리 기능인 Create(생성), Read(읽기), Update(갱신), Delete(삭제)를 묶어서 일컫는 말로 REST에서의 CRUD Operation 동작 예시는 다음과 같다.

Create : 데이터 생성(POST)

Read : 데이터 조회(GET)

Update : 데이터 수정(PUT, PATCH)

Delete : 데이터 삭제(DELETE)

## REST 구성

자원(RESOURCE) - HTTP URI

행위(Verb) - HTTP METHOD

표현(Representations) - HTTP Message Pay Load

## REST 특징

- Server-Client(서버-클라이언트 구조)
    
    REST 서버는 API 제공, 클라이언트는 사용자 인증이나 컨텍스트(세션, 로그인 정보)등을 직접 관리하는 구조로 각각의 역할이 확실히 구분되기 때문에 클라이언트와 서버에서 개발해야 할 내용이 명확해지고 서로간 의존성이 줄어들게 된다.
    
- Stateless(무상태)
    
    REST는 무상태성 성격을 갖는다. 즉 작업을 위한 상태정보를 따로 저장하고 관리하지 않는다. 세션 정보나 쿠키정보를 별도로 저장하고 관리하지 않기 때문에 API 서버는 들어오는 요청만을 단순히 처리하면 되기 때문에 서비스의 자유도가 높아지고 서버에서 불필요한 정보를 관리하지 않음으로서 구현이 단순해진다.
    
- Cacheable(캐시 처리 가능)
    
    REST의 가장 큰 특징 중 하나는 HTTP라는 기존 웹표준을 그대로 사용하기 때문에 웹에서 사용하는 기존 인프라를 그대로 활용이 가능하다. 따라서 HTTP가 가진 캐싱 기능이 적용 가능합니다. HTTP 프로토콜 표준에서 사용하는 Last-Modified태그나 E-Tag를 이용하면 캐싱 구현이 가능하다.
    
- Layered System(계층화)
    
    REST 서버는 다중 계층으로 구성될 수 있으며 보안, 로드 밸런싱, 암호화 계층을 추가해 구조상의 유연성을 둘 수 있다. 또한 PROXY, 게이트웨이 같은 네트워크 기반의 중간매체를 사용할 수 있게 한다.
    
- Uniform Interface(인터페이스 일관성)
    
    Uniform Interface는 URI로 지정한 리소스에 대한 조작을 통일되고 한정적인 인터페이스로 수행하는 아키텍처 스타일을 말한다.
    

## REST API

RESPT API란 REST의 원리를 따르는 API를 의미한다.

로이 필딩은 HTTP의 주요 저자 중 한 사람으로 그 당시 웹(HTTP) 설계의 우수성에 비해 제대로 사용되어지지 못하는 모습에 안타까워하며 웹의 장점을 최대한 활용할 수 있는 아키텍처로서 REST를 발표했다.

REST API를 설계할 때 따라야 할 몇몇 규칙이 있다.

1. URI는 동사보다는 명사를, 대문자보다는 소문자를 사용하여야 한다.

- http://tlsdnxkr.com/Eat (x)
- http://tlsdnxkr.com/car (o)
1. 마지막에 슬래시 (/)를 포함하지 않는다.
- http://tlsdnxkr.com/car/ (x)
- http://tlsdnxkr.com/car (o)
1. 언더바 대신 하이폰을 사용한다.
- http://tlsdnxkr.com/red_car (x)
- http://tlsdnxkr.com/red-car (o)
1. 파일확장자는 URI에 포함하지 않는다.
- http://tlsdnxkr.com/car.jpg (x)
- http://tlsdnxkr.com/car (o)
1. 행위를 포함하지 않는다.
- http://tlsdnxkr.com/delete-post1 (x)
- http://tlsdnxkr.com/post1 (o)

## RESTFUL

RESTFUL이란 REST의 원리를 따르는 시스템을 의미한다. 하지만 REST를 사용했다 하여 모든 시스템이 RESTFUL 한 것은 아니다. REST API의 설계 규칙을 올바르게 지킨 시스템을 RESTFUL하다 말할 수 있다.

(1) 모든 CRUD 기능을 POST로 처리 하는 API

(2) URI 규칙을 올바르게 지키지 않은 API

(3) REST API의 설계 규칙을 올바르게 지키지 못한 시스템

이러한 경우는 REST API를 사용하였지만 RESTful 하지 못한 시스템이라고 할 수 있다.

## HTTP 1.1 2.0 3.0

## 1.0 VS 1.1

### 커넥션 유지(Persistent Connection)

HTTP 프토콜은 클라이언트 - 서버 간의 데이터를 주고 받는 응용 계층의 프로토콜이다. HTTP를 이용한 데이터 전달은 TCP세션 기반에서 이루어 진다.

HTTP 1.0과 1.1의 차이는 TCP세션을 지속적으로 유지할 수 있냐 없냐에 따라 나뉜다.

TCP 연결을 재사용할 수 있는 기능인 keep-alive가 등장하면서 TCP 연결을 하나의 요청이 아닌 여러 요청에 대해서도 사용을 할 수 있게 되었다.

![image (19)](https://github.com/42CSstudy/CS-Study/assets/69511382/3f1b862b-06f4-4ad3-a81d-abe32466315b)


위의 그림에 나와있듯이 HTTP 1.0은 요청마다 TCP세션을 맺어야 하지만 HTTP 1.1은 한개의 TCP세션에서 여러 요청을 처리할 수 있다.

HTTP 1.0 : 1 Get / 1 Connection

HTTP 1.1 : N Get / 1 Connection

### 파이프라이닝(Pipelining)

파이프라이닝이 있으면 요청에 대한 응답이 없더라도 다른 요청을 할 수 있다.

파이프라이닝이 없는 경우, 요청에 대한 응답이 안오면 응답이 올 때까지 다른 요청을 보낼 수 없다.

요청1 -> 응답1 -> 요청2 -> 응답2 -> 요청3 -> 응답3 -> ~

이런 식으로 요청에 대한 응답이 와야만 다른 요청을 할 수 있는데 파이프라이닝이 있는 경우 요청에 대한 응답이 안와도 다른 요청을 할 수 있다.

요청1 -> 요청2 -> 요청3 -> 응답1 -> 응답2 -> 응답3 -> ~

이는 응답 속도를 높여 페이지 뷰의 속도를 높이기 위함이다.

![image (20)](https://github.com/42CSstudy/CS-Study/assets/69511382/8c3852c2-ea85-4d68-85b7-7e0fbcff95b7)


### 호스트 헤더(Host Header)

HTTP 1.0에서는 하나의 IP에 여러 개의 도메인을 운영할 수 없었다.

도메인 마다 IP를 구분해야해서 도메인이 늘어날 때마다 서버의 개수도 늘어나는 구조다.

HTTP 1.1에서는 Host 헤더의 추가로 가상 호스팅이 가능해졌다.

가상 호스팅은 하나의 서버에 여러 개의 도메인 이름을 호스팅 하는 방식이다. 이를 통해 하나의 서버에서 다 수의 웹 사이트를 제공해준다. 쉽게 말해 하나의 물리 서버를 여러 개의 가상 서버로 나누어 사용하면서, 각각의 가상 서버를 독립적으로 운영할 수 있게 해주는 것 이다.

![image (21)](https://github.com/42CSstudy/CS-Study/assets/69511382/0f3aa499-704e-429d-b73b-cf630abd4c6a)


### 호스팅이란?

서버 컴퓨터의 전체 또는 일정 공간을 이용할 수 있도록 임대해 주는 서비스

### 강력한 인증 절차(Improved Authentication Procedure)

HTTP 1.1 에서 다음 2개의 헤더가 추가된다.

proxy-authentication

proxy-authorization

실제 서버에서 클라이언트인증을 요구하는 www-authentication 헤더는 HTTP 1.0 에서부터 지원되어 왔으나, 클라이언트와 서버 사이에 프록시가 위치하는 경우 프록시가 사용자의 인증을 요구할 수 있는 방법이 없었다.

## 1.1 VS 2.0

### Multiplexed Streams

HTTP 1.0은 기본적으로 Connection 당 하나의 요청을 처리한다.

따라서 동시전송은 불가능하고 하나의 요청에 대한 응답이 온 후 다음 요청을 처리하므로 수 많은 리소스들이 있는 상황에서 이러한 특징은 Network Latency를 발생시킨다.

HTTP 1.1에서는 이러한 문제점을 해결하기 위해 Pipelining을 도입했는데 이는 TCP 안에 두 개 이상의 HTTP 요청을 담아 Network Latency을 줄이는 방식이다. 그러나 이 방식은 구현이 힘들고 HOL Blocking을 발생시킨다. 후속 요청들은 이전 요청이 처리될 때까지 기다려야 했기 때문에 HOL Blocking은 HTTP 1.1의 단점 중 하나였다.

이를 해결하기 위해 HTTP 2.0에서는 Multiplexed Streams를 도입하였는데 하나의 Connection으로 동시에 여러 개의 메세지를 주고 받을 수 있게 하였다. 또한 응답은 요청 순서에 상관없이 Stream으로 받기 때문에 HOL Blocking이 발생하지 않는다.

![image (22)](https://github.com/42CSstudy/CS-Study/assets/69511382/bfc5e743-c69d-4c0f-be52-932108584220)


그림상에서 Pipelining과 Multiplexed Streams 둘 다 요청에 대한 응답이 오기 전에 또다른 요청을 보내므로 별 차이가 없어 보인다.

그러나 HTTP 1.1은 완벽한 Multiplex가 아니라 요청을 한꺼번에 해도 결국엔 응답은 순차적으로 받는 HOL Blocking 문제가 발생된다.

(두 번째 요청에 대한 응답이 첫 번째 요청에 대한 응답보다 빨리 완료되어도 첫 번째 요청에 대한 응답이 먼저 실행되어야 두 번째 응답에 대한 요청이 실행된다 -> HOL Blocking)

![image (23)](https://github.com/42CSstudy/CS-Study/assets/69511382/db89f315-8e10-46a2-a143-19e00d23516f)


- 그러나 TCP 전송 계층에서는 방트로 데이터를 처리하기 때문에 TCP HOL 문제까지는 해결하지 못하였다. 이는 HTTP 3.0에서 QUIC기반으로 바뀌면서 HOL문제를 해결 했다.

### Header Compression

클라이언트와 서버 간에 수 많은 HTTP 요청이 발생할 것이고 header의 정보는 대부분 동일하다. 하지만 HTTP 1.1에서는 이러한 헤더를 중복해서 계속 보낼 뿐 아니라 cookie 정보 역시 매 요청마다 헤더에 포함되어 전송된다. 즉 불필요한 데이터를 주고 받는데 시간과 자원이 소비되는 문제점이 있었다.

HTTP 2.0의 경우, Header Table과 Huffman Encoding을 사용하는 HPACK 압축방식으로 이를 개선하였다.

클라이언트와 서버는 각각 Header Table을 관리하고 이전 요청과 동일한 필드는 table의 index만 보내고, 변경되는 값은 Huffman Encoding 후 보냄으로서 Header의 크기를 경령화 하였다.

![image](https://github.com/42CSstudy/CS-Study/assets/69511382/da77642c-e09d-43e8-8e87-d91024fba008)


### Stream Prioritization

응답에 대한 우선순위를 정해 우선순위가 높을수록 응답을 빨리 하게 되었다.

예를 들어 하나의 HTML 문서에 CSS 파일과 여러 IMG 파일이 있다고 가정해보자.

만일 여러 IMG 파일을 응답하느라 CSS 파일의 응답이 느려지면 클라이언트는 렌더링을 하지 못하고 로딩이 길어지게 된다.

따라서 CSS 파일의 우선순위를 IMG 파일의 우선순위보다 높여 먼저 렌더링을 진행하고 IMG 파일은 도착하는 대로 불러온다면 더 효율적일 것이다.

![image (24)](https://github.com/42CSstudy/CS-Study/assets/69511382/28d666d0-32dc-44e9-9717-ddf51082ded4)


### Server Push

클라이언트가 요청하지도 않은 리소스를 서버가 보낼 수 있다.

예를 들어 클라이언트가 HTML문서를 요청했고 해당 HTML에 여러개의 리소스(CSS, Image)가 포함되어 있는경우 HTTP 1.1에서 클라이언트는 요청한 HTML문서를 수신한 후, HTML문서를 해석하면서 필요한 리소스를 재 요청하였다.

반면 HTTP 2.0에서는 Server Push기법을 통해서 클라이언트가 요청하지도 않은 (HTML문서에 포함된 리소스) 리소스를 클라이언트에 보낼 수 있다.

Server Push를 통해 클라이언트의 요청을 최소화 해서 성능 향상을 이끌어 낸다.

![image (25)](https://github.com/42CSstudy/CS-Study/assets/69511382/ab7ea56b-5f9e-4e78-8402-e648720b35fc)


## 2.0 VS 3.0

### QUIC

이전까지 HTTP는 TCP를 기반으로한 전송 계층 프로토콜을 사용했다.

TCP를 사용하면 Head of line Blocking가 발생하거나 Handshake같이 번거로운 통신과정을 거쳐야 하기 때문에 속도가 느리다.

HTTP 3.0은 이러한 문제를 해결하기 위해 UDP 기반의 프로토콜인 QUIC를 사용했다.

QUIC 프로토콜에서는 전송 계층에서 stream을 일급 시민으로 취급한다. QUIC stream들은 빠르게 연결된 하나의 통로를 공유하므로 많은 요청이 발생해도 추가적인 handshake가 필요하지 않는다.

또한 QUIC steram는 독립적이다. 만약 한 stream에서 패킷 손실이 발생한다고 하더라도 대부분의 경우 다른 stream에는 영향을 주지 않는다. 그래서 QUIC은 전송 계층에서 head of line blocking 문제를 겪지 않게 된다.

![image (26)](https://github.com/42CSstudy/CS-Study/assets/69511382/46022b85-9a87-47e2-a2ba-f2269d26efa6)


QUIC는 모바일에서의 많은 인터넷 사용량을 위해 설계되었다. 스마트폰을 들고 다니는 사람들은 이동하면서 한 네트워크에서 다른 네트워크로 끊임없이 전환(5G → 3G → 4G → WiFi → •••)한다. TCP를 사용하면 한 네트워크의 연결을 끊고 다른 네트워크로 재연결하는 과정이 오래걸릴 수 밖에 없다. 그래서 QUIC은 연결이 [IP 주소]와 [네트워크 인터페이스]간에 빠르고 안정적으로 이동할 수 있도록 하는 connection ID라는 개념을 구현하였다.

![image (27)](https://github.com/42CSstudy/CS-Study/assets/69511382/23d59206-cda5-4560-9e5e-1e7b6e8dce83)


![image (28)](https://github.com/42CSstudy/CS-Study/assets/69511382/ddd69b1e-5e4a-42c8-8d36-e6ff1e4947aa)


HTTP 1.0 ~ HTTP 3.0