# Web Server & WAS(Web Application Server)

<img src="https://user-images.githubusercontent.com/47827028/99149319-93396f80-26d0-11eb-9924-37137defd7a6.png" style="zoom:50%;" />



## Web Server 

: 웹 브라우저와 같은 클라이언트로부터 HTTP 요청을 받아들이고, HTML 문서와 같은 웹 페이지를 반환하는 컴퓨터 프로그램

- html, css, javascript와 같은 정적인 페이지를 담당함 

ex) Apache Server, Nginx, IIS(Windows 전용 Web 서버) 등





## Web Application

- 웹에서 실행되는 응용 프로그램





## Web Application Server

: **웹 애플리케이션 서버**(Web Application Server, 약자 **WAS**)는 웹 애플리케이션과 서버 환경을 만들어 동작시키는 기능을 제공하는 소프트웨어 프레임워크이다

- php, jsp, asp와 같은 언어들을 사용해 동적인 페이지를 생성할 수 있는 서버

- DB 접속 및 조회, 비지니스 로직과 같은 동적인 페이지를 담당함
- 웹 서버 + 웹 컨테이너 (컨테이너: jsp, servlet을 실행시킬 수 있는 소프트웨어)

ex) tomcat, Jeus





## Web Server & Web Application Server 를 같이 사용하는 이유

- 기능을 분리하여 서버 부하 방지
  - was는 DB조회 등 페이지를 만들기 위한 다양한 로직을 처리하는데, 단순한 정적 콘텐츠를 WAS에서 제공한다면 다른 작업에 사용하는 리소스들로 인해 지연이 생겨날 수 있다.

- 물리적으로 분리하여 보안 강화
  - 여러대의 WAS 연결 가능

- SSL에 대한 암복호화 처리에 Web Server를 사용한다.

- 공격에 대해 Web Server를 앞단에 두어 중요한 정보가 담긴 DB나 로직까지(WAS) 전파되지 못하게 한다.

- WAS 포트에만 방화벽 가능