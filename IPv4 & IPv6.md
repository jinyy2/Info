# IPv4 & IPv6

#### **IP address?**

- IP 주소는 컴퓨터 네트워크에서 장치들이 서로를 인식하고 통신을 하기 위해서 사용하는 특수한 번호



### **[IPv4](https://xn--3e0bx5euxnjje69i70af08bea817g.xn--3e0b707e/jsp/resources/ipv4Info.jsp)** 

32bit 0.0.0.0 ~ 255.255.255.255 => 43억개



#### 구성

**A, B, C 클래스** : 일반 사용자에게 부여하는 네트워크 구성용

- A : 0 | Newtwork Address (0 ~ 127) | Host Address (0.0.0 ~ 255.255.255)

- B : 10 | Newtwork Address (128.0 ~ 191.255 ) | Host Address (0.0 ~ 255.255)

- C : 110 | Newtwork Address (192.0.0 ~ 223.255.255) | Host Address (0 ~ 255)

  

**D 클래스** : 멀티캐스트용 

- D : 1110 | Multicate Address (224.0.0.0 ~ 239.255.255.255) 
  

**E 클래스** : 향후 사용을 위하여 예약된 주소

- E : 11110 | Multicate Address (240.0.0.0 ~ 255.255.255.255) 



**IPv4의 한계** 

- 주소 공간의 고갈 
- 최소 지연과 자원의 예약 불가
- 암호화와 인증기능 미제공



### **[IPv6](https://xn--3e0bx5euxnjje69i70af08bea817g.xn--3e0b707e/jsp/resources/ipv6Info.jsp)**

IPv6주소는 IPv4의 주소 고갈 문제를 해결하기 위하여 기존의 IPv4주소 체계를 128비트 크기로 확장한 차세대 인터넷 프로토콜 주소



16비트씩 8부분으로 16진수 표시

예) 2001:0230:ffff:ffff:0000:0000:ffff:1111

 

#### 구성

1:2:3:4 | 5:6:7:8

64비트 네트워크 주소 | 64비트 인터페이스 주소 부분



1:2:3 | 4

48비트 상위 네트워크 주소 | 16비트 하위 네트워크 주소



