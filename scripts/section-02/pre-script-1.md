
# Section 02 - 인터넷 네트워크

- 인터넷에서 두 컴퓨터는 어떻게 통신할까?

두 컴퓨터가 로컬 네트워크에 존재할 수도 있고, 인터넷 망을 거쳐 지구 반대편에 존재할 수도 있다.

특히 인터넷 망을 거쳐 통신하기 위해선 수많은 `node` 들을 거쳐 통신해야 한다.

그렇다면 우리 컴퓨터는 도대체 어떻게 올바른 `node` 들을 거쳐 올바른 컴퓨터와 통신하는 걸까?

이를 알기 위해 우선 인터넷 프로토콜, IP 에 대해서 알아야 한다.

---

## IP : _Internet Protocol_

복잡한 인터넷을 거쳐 통신이 가능한 이유는 **IP 주소** 가 있기 때문이다.

두 컴퓨터가 통신하기 위해선 각 컴퓨터가 부여받은 IP 주소가 있어야 한다.

즉, IP 는 다음의 역할을 수행하기 위해 수립된 프로토콜이다.
- 특정한 IP 주소로 데이터를 전달
- Packet 이라는 통신 단위로 데이터를 전달

> IP 패킷 정보
>
> - 출발지 IP
> - 목적지 IP
> - 전송 데이터
> - 기타 등등

> IP 프로토콜의 한계
>
> 1. 비연결성
>
> 패킷을 받을 대상이 없거나 서비스 불능 상태여도 전송
> - 패킷 전달하려는 컴터 꺼져있어도 나는 알 수 없음
>
> 2. 비신뢰성
>
> - node 통해 패킷 전달 중, 어느 패킷이 유실되면?
> - 전달 받은 패킷들의 순서가 내가 보낸거랑 다르면?
>
> 참고로 1500 바이트 넘으면 패킷 끊어서 보낸다고 함.
>
> 3. 프로그램 구분
>
> - 같은 IP 를 사용하는 서버에서 통신하는 앱이 여러개면? (IP 주소만으로는 응답 받은 데이터를 어떤 앱에 넣어줘야 되는지 구별 불가능)

결국 IP 프로토콜 만으로는 몇몇 문제점이 있다.

그래서 나온게 TCP, UDP 이다.

> 인터넷 프로토콜 스택의 4 계층
>
> 1. 어플리케이션 계층 - HTTP, FTP
> 2. 전송 계층 - TCP, UDP
> 3. 인터넷 계층 - IP
> 4. 네트워크 인터페이스 계층 - 랜카드, 랜드라이버 등등

참고로 packet 이라는 단어는 (package + bucket) 의 합성어

> TC/IP 패킷 정보
>
> - 출발지 port
> - 목적지 port
> - 전송 제어
> - 전송 순서
> - 전송 검증 정보
> - 등등 (당연히 원본 데이터 포함)

> TCP 의 특징
>
> TCP - 전송 제어 프로토콜 _Transmission Control Protocol_
>
> - 연결 지향 : TCP 3 way handshake (가상 연결)
>
> 데이터를 보내기 전에 상대 컴퓨터가 살아 있는지를 확인함.
>
> - 데이터 전달 보증
>
> node 통해 데이터 전달 중 패킷이 누락되면 이를 내가 알 수 있음.
>
> - 순서 보장
> - 신뢰할 수 있는 프로토콜
> - 현재는 대부분 TCP 사용

> TCP 3 way handshake
>
> 1. SYN : synchronize
>
> 클라이언트가 서버로 SYN (접속 요청) 보냄.
>
> 2. SYN + ACK : Acknowledge
>
> 서버가 클라이언트의 SYN 을 받고, 클라이언트에게 ACK (요청 수락) 과 SYN 을 같이 보냄.
>
> 3. ACK
>
> 클라이언트가 서버의 (SYN + ACK) 를 받고 다시 클라이언트에게 ACK 보냄.
>
> 4. 데이터 전송
>
> 사실 요샌 최적화 되서 3 번째 ACK 때 데이터도 같이 보낸다고 함.
>
> 앞에 나온 가상연결은 무슨 뜻이지?

- 클라이언트가 서버로 데이터를 보내면, 서버도 데이터를 받았다 응답해줌.

- 패킷 순서가 꼬여서 서버로 전송되면, 서버가 클라이언트로 패킷 순서 잘 만들어서 보내라고 응답함.

> UDP 특징
>
> UDP - 사용자 데이터그램 프로토콜 _User Datagram Protocol_
>
> UDP 는 사실 아무 기능이 없음. 그래서 IP 랑 거의 똑같음.
>
> 하지만 TCP 에서처럼 port 정보가 추가됨.
> 더불어 "체크섬" 정도만 추가된다함.
>
> 그래서 UDP 는 어플리케이에서 추가 작업이 필요하고, TCP 보다 조금 더 빠름. (handshake 도 없고 부가 정보도 넣을 필요 없으니까)

- TCP 는 이미 손을 못 댐. 막 내 마음대로 최적화 하거나 그러기 힘듬.
- 그런데 UDP 는 아무것도 없으니까 내가 원하는대로 할 수 있음.
- 아 그래서 User 가 붙는건가?

Port 는 뭘까?

앞서 IP 프로토콜의 한계 중 `프로그램 구분` 을 생각해보자.
서버가 클라이언트로 응답 패킷을 보낼텐데, IP 만으로는 이 응답 받은 패킷들이 `어디에 필요한 패킷` 인지 확인할 수 없다.

이러한 상황을 port 를 통해 해결할 수 있다.
- 쉽게 생각해 port 는 같은 IP 내 프로세스를 구분하기 위한 것 이라 생각하면 편하다.

> Port 번호
>
> 0 ~ 65,535 할당 가능
> 그런데 0 ~ 1023 은 잘 알려진 포트 사용하지 않는 것이 좋음.
> - FTP : 20, 21
> - TELNET : 23
> - HTTP : 80
> - HTTPS : 443

DNS 는 뭘까?
Domain Name System 의 약어이다.

DNS 는 `"IP 주소를 이름으로 전환하는 시스템"` 이라 생각하면 편하다. 어느 서버의 IP 주소 그대로를 외우기는 어렵고, 무엇보다 IP 주소는 변할 수 있다.

> 인터넷 네트워크 정리
>
> 인터넷 통신은 IP 프로토콜과 IP 주소를 통해 이루어진다.
>
> 그런데 IP 프로토콜만으로는 여러가지 문제점이 있다.
>
> 그래서 TCP, UDP 프로토콜을 통해 이를 해결할 수 있다.

---

what is a node?
- what does the network consist of?
- what does the internet consist of?

what is internet protocol?
- how does it work?
- what algorithm does it use to travel node?

what is a packet?

what is TCP?

what if third ACK has been lost?
- what if connection has been lost sending data?

what is UDP?
- what is Datagram?
- how many ports can have in a computer or an application?
- what is checksum?

what is TELNET?

what is DNS & Dynamic DNS?

