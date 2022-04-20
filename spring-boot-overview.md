# SPRING BOOT OVERVIEW

DOCS
https://docs.spring.io/spring-boot/docs/current/api/org/springframework/boot/

#### @SpringBootApplication is combination of
<details>
  <summary>:bulb:</summary>
  
  ```JS
@Configuration (used for Java-based configuration)
@ComponentScan (used for component scanning)
@EnableAutoConfiguration (used to enable auto-configuration in Spring Boot).
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



