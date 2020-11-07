# Process & Thread



프로세스는 운영체제로부터 자원을 할당받는 작업의 단위이고 스레드는 할당받은 자원을 이용하는 실행의 단위





## Process

1. Code(fixed size) : 일반 코드가 존재
2. Data(fixed size) : 변수 / 초기화 된 데이터가 존재 (global, static 변수)
3. Heap(variable size) : 코드에서 동적으로 생성되는 데이터 (new instance)
4. Stack(variable size) : 임시 데이터(함수 호출, 로컬 변수 등)이 존재



| Stack |
| :---: |
|       |
| Heap  |
| Data  |
| Code  |





멀티태스킹 & 멀티프로세싱

멀티태스킹 : 운영체제에서 여러개의 프로세스를 실행시키는 것

멀티프로세싱 : 어떤 작업을 하나 이상의 프로세스에서 병렬로 처리하는 것



1Process 최소 1Thread



## Thread

- 프로세스 내에서 실행되는 흐름의 단위

- CPU 이용의 기본 단위
- Text, Data, Heap을 공유 (각 Thread는 별도의 stack 영역을 가짐)





**Multi-Thread**

2개 이상의 Thread를 가진 Process를 Multi-Thread 

- 프로세스의 자원을 공유
- 향상된 응답성
- context switching 비용이 적음
- 자원을 공유하는만큼 충돌을 주의

ex) Web Server



![img](https://blog.kakaocdn.net/dn/J20S0/btqyDCUGaNc/r2OmX2Un7enf0KAYkjhHEK/img.png)





**Multi-Process**

- 하나의 작업을 여러 개의 프로세스가 처리

- 프로세스간 통신(IPC, Interprocess communication) ex) socket 

- context switching 비용이 큼

- 자식 프로세스 중 하나가 문제가 생겨도 다른 프로세스에 영향이 없음

  Ex) Google Chrome (Browser, GPU, Renderer, Plugin process)





Context Switching 이란 CPU가 한 개의 Task(Process / Thread) 를 실행하고 있는 상태에서 Interrupt 요청에 의해 다른 Task 로 실행이 전환되는 과정에서 기존의 Task 상태 및 Register 값들에 대한 정보 (Context)를 저장하고 새로운 Task 의 Context 정보로 교체하는 작업을 말한다.

