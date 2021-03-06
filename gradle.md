

Gradle Project

```
plugins {
    id 'java'
}

group 'com.jinyy2.book'
version '1.0-SNAPSHOT'

repositories {
    mavenCentral()
}

dependencies {
    testImplementation 'org.junit.jupiter:junit-jupiter-api:5.6.0'
    testRuntimeOnly 'org.junit.jupiter:junit-jupiter-engine'
}

test {
    useJUnitPlatform()
}
```



```
buildscript{
    ext{
        springBootVersion = '2.1.9.RELEASE'
    }
    repositories{
        mavenCentral()
        jcenter()
    }
    dependencies {
        classpath("org.springframework.boot:spring-boot-gradle-plugin:${springBootVersion}")
    }
}
apply plugin: 'java'
apply plugin: 'eclipse'
apply plugin: 'org.springframework.boot'
apply plugin: 'io.spring.dependency-management'

group 'com.jinyy2.book'
version '1.0-SNAPSHOT'

repositories {
    mavenCentral()
    jcenter()
}

dependencies {
    compile('org.springframework.boot:spring-boot-starter-web')
    compile('org.projectlombok:lombok')
    compile('org.springframework.boot:spring-boot-starter-data-jpa')
    compile('com.h2database:h2')
    testCompile('org.springframework.boot:spring-boot-starter-test')
}
```



ArtifactId : 프로젝트의  이름

`ext` : build.gradle의 전역변수 설정

`io.spring.dependency-management` : 스프링 부트의 의존들을 관리 #**꼭 추가할 것!**

```
apply plugin: 'java'
apply plugin: 'eclipse'
apply plugin: 'org.springframework.boot'
apply plugin: 'io.spring.dependency-management'
```

자바와 스프링 부트를 사용하기 위한 필수 플러그인

`repositories` : 각종 의존성(라이브러리)들을 어떤 원격 저장소에서 받을지 설정

mavenCentral -> jcenter 



`dependencies ` : 특정버전을 명시하지 않아여 전역변수에서 선언한 버전을 따라감

dependencies{

lombok추가 

```
compile('org.projectlombok:lombok') 
```

JPA 추가

```
compile('org.springframework.boot:spring-boot-starter-data-jpa')
```

:스프링 부트용 Spring Data JPA 추상화 라이브러리

```
compile('com.h2database:h2')
```

: 인메모리 관계형 데이터베이스, 재시작시 초기화됨 - 테스트 용도

}