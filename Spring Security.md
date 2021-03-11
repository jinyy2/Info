# Spring Security

Spring Security : 인증과 인가 기능을 가진 프레임워크



> spring-security-oauth2-autoconfigure

CommonOAuth2Provider enum 추가 구글, 깃허브, 페이스북의 기본값을 제공해줌



구글 서비스 등록

https://console.cloud.google.com

프로젝트 생성 - (메뉴) API 및 서비스 [사용자 인증 정보]

사용자 인증 정보 만들기 - OAuth 클라이언트 ID



애플리케이션 이름 : 구글 로그인 시 사용자에게 노출될 애플리케이션 이름
지원 이메일 : 사용자 동의 화면에서 노출될 이메일 주소 (서비스의 이메일)
Google API의 범위 : 구글 서비스에서 사용할 범위 목록 (기본값 : email/profile/openid)



애플리케이션 유형

- 웹 애플리케이션

- Andriod

- Chrome

- iOS

- 기타

승인된 리디렉션 URI [ http://localhost:8080/login/oauth2/code/google ]

- 서비스에서 파라미터로 인증 정보를 주었을 때 인증이 성공하면 구글에서 리다이렉트할 URL입니다.
- 스프링 부트 2 버전의 시큐리티에서는 기본적으로 {도메인}/login/oauth2/code/{소셜서비스코드}로 리다이렉트 URL을 지원



클라이언트 ID

클라이언트 보안 비밀

src/main/resources/[application-oauth.properties]

```
spring.security.oauth2.client.registration.google.client-id=클라이언트 ID
spring.security.oauth2.client.registration.google.client-secret=클라이언트 보안 비밀
spring.security.oauth2.client.registration.google.scope=profile,email
```



**.gitignore 추가**

```
application-oauth.properties 
```



application-xxx.properties로 만들면 xxx라는 이름의 profile이 생성되어 이를 통해 관리 가능

src/main/resources/[application.properties]

```
spring.profiles.include=xxx
```





User 클래스

id, name, email, picture, @Enumeratre(EnumType.STRING) role

```
public enum Role {

    GUEST("ROLE_GUEST","손님"),
    USER("ROLE_USER","일반 사용자");

    private final String key;
    private final String title;
}
```



UserRepository

```
Optional<User> findByEmail(String email);
```

소셜 로그인으로 반환되는 값 중 email을 통해 이미 생성된 사용자인지 처음 가입하는 사용자인지 판단하기 위한 메소드



## 스프링 시큐리티 설정

build.gradle

```
spring-boot-starter-oauth2-client
```

- 소셜 로그인 등 클라이언트 입장에서 소셜 기능 구현 시 필요한 의존성



@EnableWebSecurity

- Spring Security 설정들을 활성화







> 스프링 부트와 AWS로 혼자 구현하는 웹 서비스를 참고



