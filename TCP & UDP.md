# TCP & UDP

OSI 7 Transport Layer

End Point 간의 **신뢰성**있는 데이터 **전송**을 담당하는 계층

 

## TCP(Transmission Control Protocol)

- 신뢰성 있는 데이터 통신을 가능하게 해주는 프로토콜
- 특징 : Connection 연결 (3-way handshake) - 양방향 통신
- 데이터의 순차 전송을 보장
- Flow Control
- Congestion Control
- Error Detection (checksum)



Segment : TCP에서의 패킷

TCP Header



### 3-way handshake (connection)

<img src="/Users/jinyy2/Library/Application Support/typora-user-images/image-20201108201950493.png" alt="image-20201108201950493" style="zoom:50%;" />



### 데이터 전송

<img src="/Users/jinyy2/Library/Application Support/typora-user-images/image-20201108202011335.png" alt="image-20201108202011335" style="zoom:50%;" />



### **4-way handshake (Connection close)**

<img src="/Users/jinyy2/Library/Application Support/typora-user-images/image-20201108202031301.png" alt="image-20201108202031301" style="zoom:50%;" />



TCP의 문제점

매번 connection을 연결하여 시간 손실

패킷을 조금만 손실해도 재전송



## UDP(User Datagram Protocol)

- TCP보다 신뢰성이 떨어지지만 전송 속도가 일반적으로 빠른 프로토콜(순차 전송, 흐름 제어, 혼잡 제어x)
- Connectionless
- Error Detection(checksum)
- 비교적 데이터의 신뢰성이 중요하지 않을 때 사용 ex) 영상 스트리밍



User Datagram

UDP Header



### UDP의 데이터 전송 방식

<img src="/Users/jinyy2/Library/Application Support/typora-user-images/image-20201108202305381.png" alt="image-20201108202305381" style="zoom:50%;" />