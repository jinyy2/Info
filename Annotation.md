## Spring boot - @Annotation

***

**@SpringBootApplication**

- 스프링 부트의 자동 설정, Spring Bean 읽기와 생성

**@RestController**

- 컨트롤러를 JSON을 반환하는 컨트롤러를 만들어준다.
- 예전에는 @ResponseBody를 각 메소드마다 선언했던 것을 한번에 사용할 수 있게 해준다.

**@GetMapping("/hello")**

- HTTP 메소드인 GET의 요청을 받을 수 있는 API를 만들어준다.

**@RunWith(SpringRunner.class)**

- 테스트를 진행할 때 JUnit에 내장된 실행자 외에 다른 실행자를 실행시킨다. => SpringRunner
- 즉, 스프링 부트 테스트와 JUnit 사이에 연결자 역할을 한다.

**@Autowired**

- 스프링이 관리하는 빈(Bean)을 주입 받는다.

**@Getter**

- 선언된 모든 필드의 get 메소드를 생성해준다.

**@RequiredArgsConstructor**

- 선언된 모든 final 필드가 포함된 생성자를 생성해준다.
- final이 없는 필드는 생성자에 포함되지 않는다.

**@RequestParam**

- 외부에서 API로 넘긴 파라미터를 가져오는 어노테이션입니다.

