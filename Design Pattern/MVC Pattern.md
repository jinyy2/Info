# MVC Pattern (Model & View & Controller)

: 개발할 때 3가지 형태로 역할을 나누 개발하는 방법론

사용자가 Controller를 조작하면 Controller는 Model을 통해서 데이터를 가져오고, 그 정보를 바탕으로 시작적인 표현을 담당하는 View를 제어해서 사용자에게 전달



**Model**: 어떠한 동작을 수행하는 코드

**View**: 클라이언트 측 기술인 html/css/javascript들을 모아둔 컨테이너

**Controller**: 사용자가 접근 한 URL에 따라서 사용자의 요청사항을 파악한 후에 그 요청에 맞는 데이터를 Model에 의뢰하고, 데이터를 View에 반영해서 사용자에게 알려준다. 



## 모델 1

구성: JSP + JavaBean(Service) => 뷰와 로직이 섞임



### 장점

- 구조가 단순

### 단점

- 출력과 로직코드의 혼합으로 JSP코드가 복잡해짐 
- 분업이 용이하지 않음
- 유지보수가 어려움



## 모델 2

구성: JavaBean(Service) + JSP + Servlet



### 장점

- 뷰와 로직의 분리
- 분업이 용이
- 유지보수가 쉬움



### 단점

- 모델1에 비해 습득이 어렵다
- 작업량이 많음

