# Spring and Spring Boot (Study Guide + Examples)

## Contents
- Inversion of Control (IoC) and Dependency Injection (DI)
- Bean scopes and lifecycle
- Configuration styles (XML, Java Config, Component Scan)
- Stereotypes: @Component, @Service, @Repository, @Controller
- @Configuration, @Bean, @Profile
- Spring Boot starters and auto-configuration
- Externalized configuration (properties/yaml), profiles
- REST controllers and validation
- Exception handling (@ControllerAdvice)
- Data access with Spring Data JPA
- Caching (Redis)
- Actuator endpoints and security
- Testing with Spring Boot

---

## IoC and DI
```java
@Configuration
class AppConfig {
    @Bean Foo foo(Bar bar){ return new Foo(bar); }
}
```

## REST Example
```java
@RestController
@RequestMapping("/api/v1/users")
class UserController {
    private final UserService svc;
    UserController(UserService svc){ this.svc = svc; }

    @GetMapping("/{id}")
    public ResponseEntity<UserDto> get(@PathVariable Long id){
        return ResponseEntity.ok(svc.find(id));
    }
}
```
