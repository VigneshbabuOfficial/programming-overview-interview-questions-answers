## MICROSERVICE

## IMPLEMENTATION - CLIENT SERVICE - 1

```JS
Create a new Service with dependencies Web, Eureka Client as CLIENT-SERVICE-1
```

![image](https://user-images.githubusercontent.com/70185865/179579456-071538f5-c897-4950-b091-e5fc39c30c6d.png)


```JS
At ClientService1Application, add RestTemplate and Logger beans
```

![image](https://user-images.githubusercontent.com/70185865/179580162-9473c69d-dc61-44ee-ab4b-9f41964aefb3.png)

```JS
Implement 3 end-points @FirstClientController class
```

![image](https://user-images.githubusercontent.com/70185865/179576710-1266233d-ca41-4345-8bdc-2be3c2bcf955.png)

```JS
Add some properties in properties file
```

![image](https://user-images.githubusercontent.com/70185865/179580647-3e42c495-eb67-4b0f-a8c8-3bcd9539cfd9.png)


## IMPLEMENTATION - CLIENT SERVICE - 2

```JS
Implement the same on Client Service 2
```

![image](https://user-images.githubusercontent.com/70185865/179579456-071538f5-c897-4950-b091-e5fc39c30c6d.png)

![image](https://user-images.githubusercontent.com/70185865/179581444-355911f2-f257-419e-8cd6-7b17ab177332.png)

![image](https://user-images.githubusercontent.com/70185865/179577236-30ea786d-9ec4-45cf-a553-8bc893772a8b.png)

![image](https://user-images.githubusercontent.com/70185865/179581597-ae1a8c65-4bdf-4754-8c8f-79b91c41b810.png)



## IMPLEMENTATION - SERVICE REGISTRY

```JS
Add Eureka server as dependency to make service registry
```

![image](https://user-images.githubusercontent.com/70185865/179587990-4e4a1c05-4e00-461b-94fa-1d51c25dd10d.png)

![image](https://user-images.githubusercontent.com/70185865/179588749-e0ee8d84-a7d9-40de-b736-5cde5743a314.png)

![image](https://user-images.githubusercontent.com/70185865/179589818-d01c1fbd-174c-46db-8e99-045911001d3a.png)


## IMPLEMENTATION - API GATEWAY

![image](https://user-images.githubusercontent.com/70185865/179600957-b3cb9ef0-e907-4285-88ea-b5229ba0cba7.png)

![image](https://user-images.githubusercontent.com/70185865/179601153-8fe5e2fa-b746-47bc-993c-d98ad3a8c0b7.png)

![image](https://user-images.githubusercontent.com/70185865/179601252-b34530dc-4a4e-45db-9bb8-4640d1d178aa.png)


### EUREKA DASHBOARD

@ localhost:8761

![image](https://user-images.githubusercontent.com/70185865/179603809-746e88bf-69ac-499e-b064-8847c221ba7b.png)





### ELK

https://www.youtube.com/watch?v=5s9pR9UUtAU

https://www.javainuse.com/spring/springboot-microservice-elk


## Interview Questions

### What do you mean by Microservice?
<details>
  <summary>:bulb:</summary>
  
  ```JS
  Microservice is an architecture where large applications are built in collection of small functional modules. So, it's useful for continuous deployment and development without affecting the other services.
  
  ```
  </details>
  
### What are the benefits and drawbacks of Microservices?
<details>
  <summary>:bulb:</summary>
  
  ```JS
  Benefits: 

    Self-contained, and independent deployment module. 
    Independently managed services.   
    In order to improve performance, the demand service can be deployed on multiple servers.   
    It is easier to test and has fewer dependencies.  
    Better communication between developers and business users.   
    Development teams of a smaller size.
  ```
```JS
  Drawbacks: 

    Due to the complexity of the architecture, testing and monitoring are more difficult.  
    Pre-planning is essential.  
    Complex development.  
    Expensive compared to monoliths.   
    Security implications. 
```  
  </details>

### What is the role of actuator in spring boot?
<details>
  <summary>:bulb:</summary>
  
```JS
A spring boot actuator is a project that provides restful web services to access the current state of an application that is running in production. 
In addition, you can monitor and manage application usage in a production environment without having to code or configure any of the applications
 ```

  </details>
  
 REF : [Interview Bit](https://www.interviewbit.com/microservices-interview-questions/#main-role-of-docker-in-microservices)
  
  
  
  
  
  
