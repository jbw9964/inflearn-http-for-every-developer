
---

what is a node?
- what does the network consist of?
- what does the internet consist of?

인터넷이란 무엇인가?
- 인터넷은 전 세계의 컴퓨팅 장치를 연결하는 컴퓨터 네트워크이다.

인터넷과 연결된 모든 장치는 `host` 또는 `종단 시스템` `(end system)` 이 될 수 있다.
- 개인적으로 end system 이라는 용어로 보아 네트워크의 말단 장치? 가 더 와닫긴 하지만 모든 장치가 end system 이 **될 수는** 있을 것 같다.

end system 은 통신 링크 `(communication link)` 와 패킷 스위치 `(packet switch)` 네트워크에 연결된다. 

한 end system 이 또다른 end system 으로 보낼 때, 그 데이터를 segment 로 나누고 각 세그먼트에 header 를 붙인다.

이렇게 만들어진 정보 패키지는 **컴퓨터 네트워크에서** packet 이라 부른다.

> segment vs packet?
> 
> 사실 이 둘은 모두 동일한 data (payload) 이다.
> 
> 하지만 현재 그 "데이터" 가 어느 계층에 존재하는지에 따라 명칭이 다를 뿐이다.
> 
> segment 의 경우 `Host layer - Transport` 에서 데이터를 지칭하고, packet 은 `Media layer - Network` 에서 이렇게 지칭한다.
> 
> [데이터? 세그먼트? 패킷? 헷갈릴 땐 PDU 를 알아보자 - daehynlee's velog](https://velog.io/@hidaehyunlee/%EB%8D%B0%EC%9D%B4%ED%84%B0-%EC%84%B8%EA%B7%B8%EB%A8%BC%ED%8A%B8-%ED%8C%A8%ED%82%B7-%ED%97%B7%EA%B0%88%EB%A6%B4-%EB%95%90-PDU%EB%A5%BC-%EC%95%8C%EC%95%84%EB%B3%B4%EC%9E%90)

> ## Answer
> 
> 1. 링크 계층 프로토콜을 실행하는 장치를 node 라고 한다. 호스트, 라우터, 와이파이 access point 등이 노드가 될 수 있다.
> 
> 이 때 링크 계층은 `TCP/IP 4 계층` 중 `2 계층` 으로 우리집 공유기나 통신사 네트워크 처리소? 라 생각하면 쉽다.
> 
> 여담으로 `TCP/IP 모델` 은 원래 4 계층으로 설명됬었는데 근래에는 5 계층으로 더 세부화 된 것 같다.
> 
> 2. & 3. 확실하게 공부한 것이 아니라 틀린 내용일 수 있다. 인터넷은 다수의 종단 시스템과 패킷 교환기들의 집합으로 구성되어 있다.

---

what is internet protocol?
- how does it work?
- what algorithm does it use to travel node?

IP 프로토콜은 송신 호스트 (또는 종단 시스템) 와 수신 호스트간 패킷 교환 네트워크를 통해 정보를 주고받는 프로토콜이다. 

이 때 패킷 교환 네트워크는 여러 통신 지점 (node) 간 

---

what is a packet?

---

what is TCP?

---

what if third ACK has been lost?
- what if connection has been lost sending data?

---

what is UDP?
- what is Datagram?
- how many ports can have in a computer or an application?
- what is checksum?

---

what is TELNET?

---

what is DNS & Dynamic DNS?

---
