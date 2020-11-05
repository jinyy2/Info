# HTTP & HTTPS

- **HTTP**(Hyper Text Transfer Protocol) :  정보를 주고받을 수 있는 프로토콜

OSI 7계층 중 응용계층에 위치하고 있는 프로토콜



- **HTTPS** (Hypertext Transfer Protocol Over Secure Socket Layer)

HTTPS는 소켓 통신에서 일반 텍스트를 이용하는 대신에, [SSL](https://ko.wikipedia.org/wiki/SSL)이나 [TLS](https://ko.wikipedia.org/wiki/트랜스포트_레이어_보안) 프로토콜을 통해 [세션](https://en.wikipedia.org/wiki/Session_(computer_science)) 데이터를 암호화한다.

HTTPS의 기본 [TCP/IP](https://ko.wikipedia.org/wiki/TCP/IP) 포트는 443이다.



- **SSL**

SSL(Secure Sockey Layer)란 보안 소켓 계층을 이르는 것으로, 인터넷 상에서 데이터를 안전하게 전송하기 위한 인터넷 암호화 통신 프로토콜을 말한다.

2019년 2월, [방송통신위원회](https://ko.wikipedia.org/wiki/방송통신위원회)는 [대한민국 정부](https://ko.wikipedia.org/wiki/대한민국_정부)와 협력하여 불건전한 내용과 저작권 침해를 원천 차단하겠다는 명목으로 HTTPS를 통한 해외 사이트 접속을 막는 [인터넷 검열](https://ko.wikipedia.org/wiki/인터넷_검열) 방안을 발표 및 실시하였다. 이 방식은 암호화의 인증 과정에서 주고받게 되는 [SNI](https://ko.wikipedia.org/wiki/SNI) 패킷을 보고 웹사이트 접속을 차단하는 방식으로, 본래 [방송통신심의위원회](https://ko.wikipedia.org/wiki/방송통신심의위원회)에서는 해당 위원회에서 지정한 '유해 사이트'에 국민들이 접속하지 못하도록 URL 접근을 특수한 사이트로 강제 우회시키고 있었는데[[8\]](https://ko.wikipedia.org/wiki/HTTPS#cite_note-8), HTTPS를 통한 접속이 많아지면서 실용성이 없어지자 이같은 방안을 따르도록 국내 통신사들에 명령하였다

SSL3.0을 이용해TLS(Transport Layer Security)로 표준화

SSL/TLS는 응용계층과 전송계층 사이에서 동작하는 독립적인 프로토콜이라고 생각하면 좋다. 자세한 동작 방식을 설명하기 전에 간단한 SSL 플로우를 이야기하자면 응용계층의 HTTP 프로토콜에서 사용자의 데이터를 받고 전송계층으로 캡슐화되기 이전에 SSL 프로토콜에 의해서 사용자의 데이터가 암호화된다. 그리고 서버는 전송계층에서 세그먼트를 받아 SSL 계층에서 데이터를 복호화하여 응용계층까지 보낸다. 즉, 우리는 SSL 프로토콜만 적용하면 마치 애플리케이션은 SSL을 TCP로 인식하고 TCP는 SSL을 애플리케이션으로 인식하는 것처럼 통신하기 때문에 우리가 별도로 통신에 대해 손댈것은 없다.



- **인증서**



- **인증기관(CA)**





