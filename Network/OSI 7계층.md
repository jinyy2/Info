# OSI(Open System Interconnection) 7계층



## 물리 계층(Physical Layer)

 네트워크의 기본 네트워크 하드웨어 전송 기술

네트워크 어댑터, 리피터(중계기), 네트워크 허브, 모뎀



## 데이터링크 계층(DataLink Layer)

 포인트 투 포인트(Point to Point) 간 신뢰성있는 전송을 보장하기 위한 계층

네트워크 브릿지나 스위치, 이더넷

에러검출 / 재전송 / 흐름제어 



## 네트워크 계층(Network Layer)

 여러개의 노드를 거칠때마다 경로를 찾아주는 역할을 하는 계층

라우팅, 흐름 제어,  세그멘테이션, 오류 제어, 인터네트워킹 



IP/ICMP

주소 부여(IP)

경로 설정(Route)



## 전송 계층(Transport Layer)

양 끝단(End to end)의 사용자들이 신뢰성있는 데이터를 주고 받을 수 있도록 해 주어, 상위 계층들이 데이터 전달의 유효성이나 효율성을 생각하지 않도록 해준다. 

흐름제어

패킷 생성



TCP

UDP



## 세션 계층(Session Layer)

양 끝단의 응용 프로세스가 통신을 관리하기 위한 방법을 제공

TCP/IP 세션을 만들고 없애는 책임을 진다.

코드 간의 번역을 담당하여 사용자 시스템에서 [데이터](https://ko.wikipedia.org/wiki/데이터)의 형식상 차이를 다루는 부담을 응용 계층으로부터 덜어 준다.



## 표현 계층(Presentation Layer)

코드 간의 번역을 담당하여 사용자 시스템에서 [데이터](https://ko.wikipedia.org/wiki/데이터)의 형식상 차이를 다루는 부담을 응용 계층으로부터 덜어 준다.



## 응용 계층(Application Layer)

응용 프로세스와 직접 관계하여 일반적인 응용 서비스를 수행



HTTP, SMTP, SNMP, FTP, telnet

