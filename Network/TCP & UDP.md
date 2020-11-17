# TCP & UDP



## Layer4: Transport Layer

End Point 간의 **신뢰성**있는 데이터 **전송**을 담당하는 계층

PDU(Protocol Data Unit) : Segement

 

## TCP(Transmission Control Protocol)

- Connection-oriented
- Reliable
- 특징 : Connection 연결 (3-way handshake) - 양방향 통신
- 데이터의 순차 전송을 보장
- Flow Control(Stop and Wait, Sliding Window)
- Congestion Control
- Error Detection (checksum)



#### 



### TCP Header

<img src="/Users/jinyy2/Library/Application Support/typora-user-images/image-20201109000845732.png" alt="image-20201109000845732" style="zoom:50%;" />



![image-20201109000229300](/Users/jinyy2/Library/Application Support/typora-user-images/image-20201109000229300.png)



### 3-way handshake (connection)

<img src="/Users/jinyy2/Library/Application Support/typora-user-images/image-20201108201950493.png" alt="image-20201108201950493" style="zoom: 33%;" />



### 데이터 전송

<img src="/Users/jinyy2/Library/Application Support/typora-user-images/image-20201108202011335.png" alt="image-20201108202011335" style="zoom: 33%;" />



### **4-way handshake (Connection close)**

<img src="/Users/jinyy2/Library/Application Support/typora-user-images/image-20201108202031301.png" alt="image-20201108202031301" style="zoom: 33%;" />



TCP의 문제점

매번 connection을 연결하여 시간 손실

패킷을 조금만 손실해도 재전송



## UDP(User Datagram Protocol)

- Connectionless(순차 전송, 흐름 제어, 혼잡 제어x)
- Unreliable
- 비교적 데이터의 신뢰성이 중요하지 않을 때 사용 ex) 영상 스트리밍



### UDP Header

<img src="/Users/jinyy2/Library/Application Support/typora-user-images/image-20201109001225051.png" alt="image-20201109001225051" style="zoom:50%;" />

![image-20201109000116866](/Users/jinyy2/Library/Application Support/typora-user-images/image-20201109000116866.png)



### UDP의 데이터 전송 방식

<img src="/Users/jinyy2/Library/Application Support/typora-user-images/image-20201108202305381.png" alt="image-20201108202305381" style="zoom: 33%;" />