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

**@RequestParam**

- 외부에서 API로 넘긴 파라미터를 가져오는 어노테이션입니다.

  

### LOMBOK

***

자바 개발할 때 자주 사용하는 코드 Getter, Setter, 기본생성자, toString 등을 어노테이션으로 자동 생성



**@Getter**

- 선언된 모든 필드의 get 메소드를 생성해준다.

**@RequiredArgsConstructor**

- 선언된 모든 final 필드가 포함된 생성자를 생성해준다.
- final이 없는 필드는 생성자에 포함되지 않는다.

**@NoArgsConstructor**

- 기본 생성자 자동 추가 

**@Builder**

- 해당 클래스의 빌더 패턴 클래스 생성
- 생성자 상단에 선언시 생성자에 포함된 필드만 빌더에 포함



### JPA 

***

**@Entity** 

- 테이블과 링크될 클래스임을 나타낸다.
- SalesManager.java -> sales_manager table
- Entity 클래스에서는 절대 Setter를 만들지 말것

**@Id**

- 해당 테이블의 PK 필드를 나타낸다.

**@GeneratedValue**

- PK의 생성 규칙을 나타낸다.
- 스프링 부트 2.0에서는 GenerationType.IDENTITY 옵션을 추가해야 audo_increment가 된다.

**@Column**

- 변경사항이 필요할 때만 이용 ex) content, size 등

- 문자열의 경우 VARCHAR(255)가 기본

**@MappedSuperclass**

- JPA Entity 클래스들이 BaseTimeEntity를 상속할 경우 필드들(createdDate, modifiedDate)도 칼럼으로 인식하도록 한다.

**@EntityListeners(AuditingEntityListener.class)**

- BaseTimeEntity 클래스에 Auditing 기능을 포함한다.

**@CreatedDate**

- Entity가 생성되어 저장될 때 시간이 자동으로 저장된다.

**@LastModifiedDate**

- 조회한 Entity의 값을 변경할 때 시간이 자동 저장된다.



Repository.save

- 테이블 insert/update 쿼리 실행
- id 값이 있다면 update, 없다면 insert

Repository.findAll()

- 테이블에 있는 모든 데이터를 조회해오는 메소드