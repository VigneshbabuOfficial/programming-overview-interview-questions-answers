# SPRING BOOT OVERVIEW

DOCS
https://docs.spring.io/spring-boot/docs/current/api/org/springframework/boot/

#### @SpringBootApplication is combination of
<details>
  <summary>:bulb:</summary>
  
  ```JS
@Configuration (used for Java-based configuration) - if not written means, no issues. But ComponentScan should be written.
@ComponentScan (used for component scanning)  - if not written means, Server will not be accessed.
@EnableAutoConfiguration (used to enable auto-configuration in Spring Boot) - if not written means, Application itself will not  build successfully / deployed.
```
REF: https://docs.spring.io/spring-boot/docs/current/api/org/springframework/boot/autoconfigure/SpringBootApplication.html

![image](https://user-images.githubusercontent.com/70185865/164116420-7d4d863c-7e0d-4406-a7ff-33d9ec58c3e3.png)

</details>

#### @EntityScan(basePackages =
<details>
  <summary>:bulb:</summary>
  
  ```JS
 Using @EntityScan will cause auto-configuration to Set the packages scanned for JPA entities.  
```
REF: 
https://docs.spring.io/spring-boot/docs/current/api/org/springframework/boot/autoconfigure/domain/EntityScan.html

</details>

#### @EnableJpaRepositories(basePackages =
<details>
  <summary>:bulb:</summary>
  
  ```JS
 Annotation to enable JPA repositories. Will scan the package of the annotated configuration class for Spring Data repositories by default.  
```
REF: 
https://docs.spring.io/spring-data/jpa/docs/current/api/org/springframework/data/jpa/repository/config/EnableJpaRepositories.html

</details>

#### @RestController
#### @Bean
#### @RequestMapping
#### @Validated
#### @Autowired
#### @GetMapping
#### @PostMapping
#### @RequestBody
#### @PutMapping(value = "/{id}")
#### @PathVariable(name = "id")
#### @DeleteMapping("/{ids}")
#### @Service
#### @Scope
#### @Entity
#### @Table
#### @DynamicInsert
#### @DynamicUpdate
#### @SequenceGenerator(allocationSize = 1,name = "students_seq",sequenceName = "students_seq")
#### @Id
#### @NotNull(message="id must not be null")
#### @Column(name = "id", columnDefinition = "default nextval('students_seq'::regclass)")
#### @GeneratedValue(generator = "students_seq",strategy = GenerationType.SEQUENCE)
#### @JsonFormat(pattern = "yyyy-MM-dd")
#### @Repository
#### @ControllerAdvice
#### @ResponseStatus(HttpStatus.INTERNAL_SERVER_ERROR)
#### @ExceptionHandler({Exception.class})




