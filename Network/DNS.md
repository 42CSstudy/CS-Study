# DNS

**Domain Name System**

네트워크에서 사용하는 시스템이다.

# ❗️DNS(Domain Name System)란?

> Domain Name System의 약자 DNS는 인터넷의 전화번호부이다. 사용자가 'naver.com' 또는 'google.com'과 같은 도메인 이름을 웹 브라우저에 입력하는 경우 DNS는 해당 사이트의 올바른 IP 주소를 찾는 역할을 한다.
> 

일반적으로 우리는 웹사이트에 접속 할 때 외우기 어려운 IP 주소 대신 도메인 이름을 사용한다.

인터넷에서 모든 장치는 고유한 IP 주소를 가지고 있지만, 우리는 IP 주소보다 도메인 이름을 더 쉽게 기억하고 이해할 수 있기 때문이다.

때문에 이 도메인은 일종의 **별명**으로 입력한 도메인을 실제 네트워크상에서 사용하는 IP 주소로 바꾸고 해당 IP 주소로 접속하는 과정이 필요하다.

**이러한 과정, 전체 시스템을 DNS(도메인 네임 시스템)라고 한다.**

DNS(도메인 네임 시스템)은 전세계적으로 약속된 규칙을 공유하는데 상위 기관에서 인증된 기관에게 도메인을 생성하거나 IP 주소로 변경할 수 있는 **‘권한’**을 부여한다.

DNS는 이처럼 상위 기관과 하위 기관과 같은 **‘계층 구조’**를 가지는 **분산 데이터베이스 구조**를 가진다.

### 왜 이런 계층 구조를 가지는 분산 데이터 베이스 구조를 가질까?

"이 도메인 좀 IP 주소로 바꿔줄래?”라고 할 수 있는 서버(네임서버)가 한 대만 있지 않기 때문이다.

한 대로 돌리려면 당연히 느릴 수 밖에 없고 비효율적이기 때문이다.

그렇다면 여러 서버(네임서버)를 만들면 되지 않을까?

그렇게 되면 해당 정보(도메인과 IP 주소)를 모든 서버에서 공유해야한다. 안그러면 어떤 서버(네임서버)에서는 ‘www.hanamon.kr’의 IP 주소를 모른다고 할 수도 있다.

그래서 도메인을 계층적으로 구분하는, 정보(도메인과 IP주소)를 분산하는 구조를 선택하게 되었다.

그래서 도메인에 닷(dot), 점이 있는 것이다. 점이 계층을 나타낸다.

> 쉽게 말해 단 한 권의 두꺼운 책에 모든 전화번호를 기입해 찾는 것보다 여러 권으로 나누되, 하위로 연관되어 있는 여러 권으로 나누는 방식을 채택한 것이다.
> 

# ❗️DNS의 구성 요소는?

DNS는 아래와 같이 크게 3가지로 분류 할 수 있다.

- **도메인 네임 스페이스**(Domain Name Space) : DNS가 저장 관리하는 계층적 구조
- **네임 서버**(Name Server) : 권한 있는 DNS 서버
- **리졸버**(Resolver) : 권한 없는 DNS 서버

DNS는 앞서 설명했듯이 도메인 이름을 웹 브라우저에 입력하는 경우 해당 사이트의 **올바른 IP 주소**를 찾는 역할을 수행하기 위해

“이 도메인 이름은 이 IP 주소이다”라는 ‘텍스트’를 저장하는 **데이터베이스**가 필요하다.

DNS는 계층적으로 구분하는, 정보(도메인과 IP주소)를 분산하는 구조를 갖기 때문에

분산된 데이터가 어디 저장되어 있는지 찾을 프로그램들이 필요하고 찾았으면 해당 IP 주소로 이동할 프로그램(브라우저 등)이 필요하다.

> 도메인 네임 스페이스라는 규칙(방법)으로 도메인 이름 저장을 분산한다.
> 

> 네임 서버(DNS 서버와 같은 말, 그런데 리졸버 서버 등 시스템 안에서 다른 역할을 하는 서버도 있기에 그냥 DNS 서버라고 하는 것보다 네임 서버라고 하는게 더 의미가 전달되는 듯)가 해당 도메인 이름의 IP 주소를 찾는다.
> 

> 리졸버가 DNS 클라이언트 요청을 네임 서버로 전달하고 찾은 정보를 클라이언트에게 제공하는 기능을 수행한다.
> 

**리졸버**는 어떤 **네임 서버**에서 찾아야하는지, 이미 **캐시 되어있는지** 등을 찾아서 **클라이언트**에게 찾았으면 찾은 것을 못 찾았으면 못 찾았다고 전달하는 역할을 수행한다고 생각하면 된다.

대표적인 것이 KT, LG 유플러스, SK 브로드밴드와 같은 ISP(통신사) DNS 있고, 브라우저 우회 용도로 많이 쓰는 구글 DNS, 클라우드플레어와 같은 Public DNS 서버가 있다.

그래서 거의 Resolver = Recursive DNS Server = Local Server(of ISP) = Recursor 라고 생각하면 될 것 같다.

자 조금 더 세부적으로 알아보자.

## 도메인 네임 스페이스

![image (29)](https://github.com/42CSstudy/CS-Study/assets/69511382/0ce27878-48a6-4a0e-bf52-b0f774fd0088)


> DNS는 전세계적인 거대한 분산 시스템으로 도메인 네임 스페이스는 이러한 DNS가 저장 관리하는 계층적 구조를 의미한다.
> 

도메인 네임 스페이스는 최상위에 루트 DNS 서버가 존재하고 그 하위로 연결된 모든 노드가 연속해서 이어진 계층 구조로 되어있다.

폴더 구조와 상당히 흡사하다.

### 계층적 도메인 레벨 (Hierarchical Domain Level)

위의 사진과 같이 도메인 네임 스페이스는 일반적으로 트리 구조를 하고 있으며 최상위 레벨부터 순차적으로 계층적 소속 관계를 나타낸다.

하위 조직의 네임 스페이스를 할당하고 관리하는 방식은 각 하위 기관의 관리 책임자에게 위임된다.

- 예를 들어, zinukk.kr 도메인은 kr 도메인을 관리하는 네임 서버에 등록되어 있고 www.zinukk.kr은 zinukk.kr 을 관리하는 네임서버에 등록되어 관리된다.

zinukk.kr은 kr 도메인을 관리하는 네임 서버에 등록되어있는데 해당 하위 기관은 가비아로 되어있다.

### Fully Qualified Domain Name(FQDN) 전체 도메인 이름

> 도메인의 전체 이름을 표기하는 방식
> 

일반적으로 도메인 이름은 www.zinukk.kr에서 zinukk.kr을 의미하기 때문에 이러한 용어가 나왔다.

- 도메인 이름 : zinukk.kr
- 호스트 이름 : www
- FQDN : www.zinukk.kr

## 네임 서버(Name Server = DNS Server)

> 문자열로 표현된 도메인 이름을 실제 컴퓨터가 통신할 때 사용하는 IP 주소로 변환시키기 위해서는 도메인 네임 스페이스의 트리 구조에 대한 정보가 필요한데 이러한 정보를 가지고 있는 서버를 네임 서버라고 한다.
> 

일반적으로 **데이터베이스 역할**(저장, 관리), **찾아주는 역할**, **요청 처리 응답 구현**의 역할을 수행한다.

전 세계에 13개의 Root DNS 서버가 구축되어 있으며 이 **네임 서버를 복사하여 같은 기능을 담당하는 미러서버가** 존재한다.

네임 서버는 총 네 가지로 분류할 수 있다. 한 번 살펴보자.

### 1. Root DNS Server

> DNS 서버의 최상위 네임서버로 DNS 해석부터 발생한 DNS 요청에 대하여 적절한 TLD 네임서버 정보를 반환한다.
> 

### 2. Top-Level Domain(TLD) DNS Server

> 도메인 등록 기관이 관리하는 서버로 Authoritative DNS 서버의 주소를 저장하고 안내하는 역할을 한다.
> 

도메인 판매 업체(가비아 등)의 DNS 설정이 변경되면 도메인 등록 기관으로 전달되기 때문에 어떤 도메인이 어떤 판매업체(가바이 등)에서 구매했는지 알수 있다.

### 3. Second-Level Domain(SLD) DNS Server (Authoritative DNS Server)

> 실제 개인 도메인과 IP 주소의 관계가 기록(저장, 변경)되는 서버다.
> 

그래서 권한의 의미인 Authoritative가 붙었으며 일반적으로 도메인/호스팅 업체의 네임서버를 말한다.

### 4. Anauthoritative DNS Server

> 권한이 없는 DNS 서버로 리졸버 서버, 리컬시브 서버, 리커서가 있다.
> 

DNS 서버는 도메인 네임 스페이스를 위한 권한 있는 DNS 서버와 권한이 없는 DNS 서버로 구분된다.

위 1,2,3은 권한 있는 DNS 서버(Authoritative DNS Server)이다.

네임 스페이스를 위한 권한 있는 DNS 서버는 IP 주소와 도메인 이름을 매핑한다.

하지만 네임 스페이스를 위한 권한 없는 DNS 서버는 질의를 통해 IP 주소를 알아내거나 캐시한다(리졸버의 역할).

리졸버의 역할을 자세히 알아보자.

### DNS Resolver

> DNS Resolver는 사용자의 컴퓨터나 네트워크에 위치한 DNS 클라이언트이다.
> 

DNS Resolver는 사용자가 도메인 이름을 입력하면, 해당 도메인 이름을 IP 주소로 변환하기 위해 DNS 서버에 요청하여 질문하는 역할을 한다.

![image (30)](https://github.com/42CSstudy/CS-Study/assets/69511382/3dfd8d92-3dac-46ea-a3bb-23b20c607806)


### 브라우저는 어떻게 DNS 서버를 조회할 수 있고 IP 정보를 받을수 있는 것일까?

DNS 서버에 요청하여 조회한다는 것은 DNS 서버에 요청을 하고 반송되는 응답을 받는과정이 이루어진다는 것이다.

이러한 과정은 DNS 서버에 대해 클라이언트로 동작한다고 볼 수 있으며 이 역할을 **DNS Resolver**가 수행한다.

> 간단하게 DNS Resolver는 도서관의 어딘가에서 특정한 책을 찾아달라고 요청받는 사서로 생각할 수 있다.
> 

DNS Resolver는 어떤 네임 서버에서 찾아야하는지, 이미 캐시 되어있는지 등 어떻게든 찾아서 클라이언트에게 찾았으면 찾은 것을 못 찾았으면 못 찾았다고 전달하는 역할을 한다.

대표적인 것이 KT/LG/SK와 같은 ISP(통신사) DNS 있고, 브라우저 우회 용도로 많이 쓰는 구글 DNS, 클라우드플레어와 같은 Public DNS 서버가 있다.

그래서 거의 Resolver = Recursive DNS Server = Local DNS Server(of ISP) = Recursor 라고 생각하면 될 것 같다.

## 왜 이런식으로 나누어 놨을까?

답은 생각보다 간단하다.

> 도메인을 IP 주소로 바꿔줄 수 있는 네임 서버가 한 대만 있지 않기 때문이다.
> 

단 한 대의 네임 서버에서 모두 관리하게 되면 너무나 당연하게도 속도 저하의 문제도 발생한다.

그래서 도메인을 계층적으로 구분하는, 정보(도메인과 IP주소)를 분산하는 구조를 선택하게 되었는데 이를 닷(dot)으로 구분한다.

점이 계층을 의미한다.

# ❗️DNS 동작 방식

![image (31)](https://github.com/42CSstudy/CS-Study/assets/69511382/0fe9a7c8-90af-4dfc-be06-7474816d28ff)


## 1. 브라우저 ➢ DNS Resolver

사용자가 웹 브라우저에 도메인 이름을 입력하면, DNS Resolver는 우선 자신의 캐시에 해당 도메인 이름에 대한 IP 주소가 저장되어 있는지 확인한다.

캐시에 저장된 IP 주소가 있다면, DNS Resolver는 바로 해당 IP 주소를 반환한다.

하지만 캐시에 저장된 IP 주소가 없거나, 캐시에 저장된 IP 주소가 만료되었다면, DNS Resolver는 DNS 서버에 요청한다.

## 2. DNS Resolver ➢ Root DNS Server ➢ DNS Resolver

먼저, DNS Resolver는 Root DNS Server에 요청한다.

Root DNS Server는 전 세계에 13개가 존재하며, 각각의 Root DNS Server는 모든 도메인 이름에 대한 IP 주소를 가지고 있지는 않는다.

대신 Root DNS Server는 TLD DNS Server에 대한 정보를 가지고 있으며, 해당 TLD DNS Server의 IP 주소를 DNS Resolver에게 전달한다.

## 2. DNS Resolver ➢ TLD DNS Server ➢ DNS Resolver

DNS Resolver는 이제 TLD DNS Server에 대해 질의를 수행한다.

예를 들어, 사용자가 입력한 도메인 이름이 "example.com"이라면, DNS Resolver는 .com TLD DNS Server에 요청한다.

TLD DNS Server는 해당 도메인 이름의 Authoritative DNS Server의 IP 주소를 DNS Resolver에게 반환한다.

## DNS Resolver ➢ Authoritative DNS Server ➢ DNS Resolver ➢ 브라우저

마지막으로, DNS Resolver는 Authoritative DNS Server에 요청한다.

Authoritative DNS Server는 해당 도메인 이름에 대한 IP 주소를 가지고 있으며, 이를 DNS Resolver에게 반환한다.

DNS Resolver는 이제 해당 IP 주소를 캐시에 저장하고, 이후 동일한 도메인 이름에 대한 질의가 들어올 때 캐시에 저장된 IP 주소를 사용한다.

이러한 과정을 통해, DNS 시스템은 사용자가 도메인 이름을 입력할 때마다 해당 도메인 이름에 대한 IP 주소를 찾아서 반환하게 된다.

이를 통해, 사용자는 도메인 이름을 쉽게 기억하고 입력할 수 있으며, 인터넷 서비스 제공자는 서버의 IP 주소를 변경하더라도 도메인 이름을 유지할 수 있다.

좀 더 쉽게 대화 형식으로 설명하자면,

웹브라우저는 리졸버에게 아래와 같이 요청한다.

- 웹 브라우저 : www.zinukk.kr의 IP 주소를 줘!

리졸버는 최상위 기관에서 관리하는 Root DNS Server 에게 요청한다.

- 리졸버 : 알겠어 기다려봐! 흠 저장된 캐시에는 없네,, 그럼 요청해야겠다! 야 Root DNS Server야 www.zinukk.kr의 IP 주소 갖고 있어?

최상위 기관에서 관리하는 Root DNS Server는 응답한다.

- Root DNS Server : 야 내가 www.zinukk.kr의 IP는 없고 대신 .kr 한국 국가 도메인 이라는 건 알아 냈어! .kr TLD DNS Server로 가서 한 번 물어봐.

리졸버는 이제 .kr TLD DNS Server에게 요청한다.

- 리졸버 : 야 www.zinukk.kr IP 주소 있어?? 너한테 있다는데?

.kr TLD DNS Server는 응답한다.

- TLD DNS Server : 야 너가 찾는 www.zinukk.kr IP 주소는 없고 내가 zinukk.kr이 어디있는지는 알아냈어! Authoritative DNS Server로 가봐

리졸버는 이제 Authoritative DNS Server에게 요청한다.

- 리졸버 : 야 야 www.zinukk.kr IP 주소 있어??

Authoritative DNS Server는 응답한다.

- Authoritative DNS Server : 야 너가 찾는 거 여기 있다! 12.345.678.999야~

리졸버는 이제 웹 브라우저에게 알려준다.

- 리졸버 : 일단 캐시에 저장부터 하고~ 야 브라우저야 너가 찾는 www.zinukk.kr IP 주소는 12.345.678.999이야~

이런 방식으로 작동된다.

> 그리고 우리는 여기서 한 가지 사실을 발견할 수 있다.
> 

바로 역트리 구조로 최상위 Root DNS Server로부터 Top-Level DNS Server, Authoritative DNS Server 방향으로 원하는 주소를 단계적으로 찾아간다는 점이다.

예를 들어 hwan.co.kr 이라는 URL을 뜯어보면

![image (32)](https://github.com/42CSstudy/CS-Study/assets/69511382/85750fcc-02b1-489a-b2d7-079f80ed2db8)


이런식으로 구성되어 있는 걸 알 수 있다.

DNS Resolver에서 Root DNS Server로 도메인 주소를 물으면,

Root DNS Server에서 다 알아서 찾아 주는것이 아니라,

Root DNS Server 자신에 등록되어 있는 최상위 도메인(TLD)에서 해당 도메인에 붙어있는 TLD 주소를 찾아서

DNS Resolver 에게 준다.

그럼 기지국 DNS Resolver는 Root DNS Server에게 받은 TLD Server에게 다시 물어본다.

이하 찾을때 까지 반복한다.

> 즉, 재귀적으로 순환을 반복하며 이를 Reculsive Query라고 한다.
> 

Reculsive Query에 대해 자세히 알아보기 전, 먼저 DNS Query에 대해 알아보자.

## DNS Query란?

> DNS Query(쿼리)는 사용자가 도메인 이름을 입력하고 IP 주소를 얻기 위해 DNS 서버에 보내는 요청을 말한다. 이 요청은 DNS Resolver가 사용자 컴퓨터에서 생성하고 DNS 서버에 전송한다.
> 

DNS Query는 DNS 서버에 보내지며, DNS 서버는 이를 처리하고 응답을 반환한다.

이 응답에는 사용자가 요청한 정보(IP 주소 등)가 포함되는데, DNS Query와 DNS 응답은 일반적으로 UDP(User Datagram Protocol)를 사용하여 전송된다.

DNS Query의 결과는 DNS Resolver에게 반환되는데 이를 통해 DNS Resolver는 사용자에게 도메인 이름에 대한 IP 주소를 반환하거나, 이를 찾을 수 없을 경우 에러를 반환한다.

DNS 쿼리는 **Recursive(재귀적)** 또는 **Iterative(반복적)**으로 구분된다.

### Reculsive Query

> 재귀적 질의라고 하며 결과물(IP 주소)를 돌려주는 작업이다. (결과적으로 Recursive 서버가 Recursive 쿼리를 웹 브라우저 등에게 돌려주는 역할을 한다.)
> 

Recursive 쿼리를 받은 Recursive 서버는 Iterative 하게 권한 있는 네임 서버로 Iterative 쿼리를 보내서 결과적으로 IP 주소를 찾게 되고 해당 결과물을 응답한다.

사전적 의미로써 재귀로, 응답을 돌려주는 쿼리라고 생각하자.

### Iterative Query

> 반복적 질의 라고 하며 Recursive DNS 서버가 다른 DNS 서버에게 쿼리를 보내어 응답을 요청하는 작업이다.
> 

Recursive 서버가 권한 있는 네임 서버들에게 반복적으로 쿼리를 보내서 결과물(IP 주소)를 알아낸다.

만약 Recursive 서버에 이미 IP 주소가 캐시 되어있다면 이 과정은 건너 뛴다.

## 차이점

### DNS Resolver

DNS Resolver는 일반적으로 사용자의 컴퓨터나 모바일 디바이스에 포함되어 있으며, 사용자가 도메인 이름을 입력하면 해당 Resolver는 DNS 쿼리를 생성하고, 이를 인터넷 상의 다른 DNS 서버에 전송한다.

Resolver는 일반적으로 캐시된 DNS 정보를 사용자의 컴퓨터나 모바일 디바이스에 저장하며, 이를 사용하여 DNS 쿼리를 처리한다.

즉, Resolver는 사용자의 컴퓨터와 DNS 서버 사이의 중개자 역할을 한다.

### Local DNS Server

반면 Local DNS Server는 네트워크에서 사용되며, 일반적으로 기업, 학교, 공공기관 등에서 사용된다.

Local DNS Server는 네트워크 내에서 DNS 쿼리를 처리하고, 이를 인터넷 상의 다른 DNS 서버에 전달한다.

또한 Local DNS Server는 네트워크 내에 캐시된 DNS 정보를 저장하며, 이를 사용하여 **네트워크 내 모든 사용자의 DNS 쿼리를** 빠르게 처리할 수 있다.

성능 측면에서 Local DNS Server는 DNS Resolver 보다 더 높은 처리량을 처리할 수 있으며, 다양한 DNS 정보를 캐시하여 더 빠른 DNS 쿼리 응답을 제공한다.

## 결론

Resolver는 일반적으로 하나의 사용자를 위해 동작하지만, Local DNS Server는 네트워크 내의 모든 사용자를 위해 동작한다.

때문에 Local DNS Server는 더 많은 DNS 정보를 캐시하고, 더 많은 DNS 쿼리를 처리할 수 있다.

결론적으로, Resolver는 개인 사용자에게 DNS 서비스를 제공하는 데 중점을 둔 반면, Local DNS Server는 네트워크 내 모든 사용자에게 DNS 서비스를 제공하는 데 중점을 둔다.

Resolver와 Local DNS Server는 비슷한 역할을 하지만, 그 역할을 하는 위치와 대상이 다르기 때문에 서로 다른 기능과 기술을 사용한다.

# 정리

1. DNS란 주소창에 입력한 도메인을 실제 네트워크상에서 사용하는 IP 주소로 바꾸고 해당 IP 주소로 접속하는 과정을 의미한다.
2. DNS는 크게 DNS가 저장 관리하는 계층적 구조인 Domain Name Space, 권한이 있는 DNS Server, 권한이 없는 DNS Resolver로 구성되어 있다.
3. 유저가 주소창에 URL을 입력하면 DNS Resolver는 이전에 방문한 적이 있는 주소인지 캐시를 확인하고 방문한 적이 있다면 캐싱된 IP 주소를 곧바로 돌려준다.
4. 만약 방문한 적이 없다면 DNS Resolver는 제일 먼저 Root DNS Server에 요청하고 최종적으로 Authoritative DNS Server 로부터 올바른 IP주소를 받는다.
5. DNS Resolver는 캐시에 저장하고 이를 웹브라우저에 전달한다.