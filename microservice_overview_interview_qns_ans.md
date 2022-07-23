## MICROSERVICE

## IMPLEMENTATION - SERVICE REGISTRY

```JS
Add Eureka server as dependency to make service registry
```

![image](https://user-images.githubusercontent.com/70185865/179587990-4e4a1c05-4e00-461b-94fa-1d51c25dd10d.png)

![image](https://user-images.githubusercontent.com/70185865/179588749-e0ee8d84-a7d9-40de-b736-5cde5743a314.png)

![image](https://user-images.githubusercontent.com/70185865/179589818-d01c1fbd-174c-46db-8e99-045911001d3a.png)

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


## IMPLEMENTATION - API GATEWAY

![image](https://user-images.githubusercontent.com/70185865/179600957-b3cb9ef0-e907-4285-88ea-b5229ba0cba7.png)

![image](https://user-images.githubusercontent.com/70185865/179601153-8fe5e2fa-b746-47bc-993c-d98ad3a8c0b7.png)

![image](https://user-images.githubusercontent.com/70185865/179601252-b34530dc-4a4e-45db-9bb8-4640d1d178aa.png)


### EUREKA DASHBOARD

@ localhost:8761

![image](https://user-images.githubusercontent.com/70185865/179603809-746e88bf-69ac-499e-b064-8847c221ba7b.png)


### ADDED ZIPKIN & SLEUTH

![image](https://user-images.githubusercontent.com/70185865/179609416-d7146a86-6406-44f3-9f7e-0812e15e7640.png)


```JS
goto - https://zipkin.io/pages/quickstart.html
```

```JS
download jar and execute using the command in cmd <<dir_location_path>>java -jar <<zipkin_file_name>>.jar 

and note the port number which is running on. most probably it'll be 9411

add this property on all client services

spring.zipkin.base-url=http://localhost:9411

then hit localhost:9411/zipkin to see the zipkin dashboard.

do some end-points request of our client services

then we can select the service and provide the trace-id to see the propagation of request.
```

![image](https://user-images.githubusercontent.com/70185865/179655936-0e8a4558-9ac3-4306-b564-c7747498e498.png)

![image](https://user-images.githubusercontent.com/70185865/179656002-4f3ad7c7-e930-49f9-bc88-05362abec051.png)

![image](https://user-images.githubusercontent.com/70185865/179656046-4b00a503-4149-4a3d-ae7f-392a073ab786.png)


REF :  https://www.youtube.com/watch?v=BnknNTN8icw&t=4118s

## ELK - Elastic Search , Logstash & Kibana

## Elastic Search

```JS

Elastic search is a NoSql database which is used store the logs
Download Elastic search from https://www.elastic.co/downloads/elasticsearch 
Extract and goto the bin folder from there open CMD
type elasticsearch.bat

after some time check at the browser localhost:9200

```

![image](https://user-images.githubusercontent.com/70185865/179820737-bbfaf14e-df2d-44cd-9ed2-e6a02edbcf99.png)

## Kibana

```JS
Kibana is a UI layer which helps developer to monnitor the application logs.

Download kibana from https://www.elastic.co/downloads/kibana

goto config folder and open the yml file and un-comment the line 
elasticsearch.hosts: ["http://localhost:9200"]

goto the bin folder and open cmd from there and type kibana.bat

check at the browser on localhost:5601

```

## Logstash

```JS
Logstash is log pipeline tool where it accepts inputs/logs from various sources and exports to various targets

```

```JS
Open the client service application.properties file and add the log path as
logging.file:<<location-path>>

so, whenever application is hit logs will be generated in that file.
```

```JS
Need to create a logstash.config file
```
![image](https://user-images.githubusercontent.com/70185865/179833918-21bf98f0-6cf0-4112-b43f-f89fcd32a744.png)

After config file is created, paste into bin folder. And open CMD
type logstash -f logstash.config

![image](https://user-images.githubusercontent.com/70185865/179835098-321528dd-c344-4df2-b356-de1a99b2ce7b.png)

![image](https://user-images.githubusercontent.com/70185865/179835204-e6ed6973-25ce-4ecd-8e4f-0ada3dc5e8df.png)

![image](https://user-images.githubusercontent.com/70185865/179835297-00a46b6e-7259-411d-87be-1fd5ac31eecd.png)

![image](https://user-images.githubusercontent.com/70185865/179835502-44d631de-37db-46d2-b925-5b03331f5e26.png)

![image](https://user-images.githubusercontent.com/70185865/179835679-2fffaad0-4021-4a8f-9473-bc994d475b80.png)

![image](https://user-images.githubusercontent.com/70185865/179835815-c7d3b7d3-6ebf-4c0a-86dd-6addd00593cc.png)


REF :

https://www.youtube.com/watch?v=5s9pR9UUtAU

https://www.javainuse.com/spring/springboot-microservice-elk


---------------------------------------------------------------------------------------------------------


## Fault Tolerance
<details>
  <summary>:bulb:</summary>
  
```JS
In Microservice application, there may be receive an error response if any error or exception occurs to the request. So, at that time application needs to be recovered and ready to be used immediately with zero downtime.
So, there we can have zero downtime and cost is higher.
  ```
</details>

## High Availability
<details>
  <summary>:bulb:</summary>
  
```JS
In Microservice application, there may be receive an error response if any error or exception occurs to the request. So, at that time application needs to be recovered with mins to hours of downtime and also cost is lesser.
  ```
</details>

## Circuit Breaker
<details>
  <summary>:bulb:</summary>
  
```JS
The circuit breaker is design pattern when the a praticuler microservice experiences failures or slowness the Circuit Breaker trips for a particular duration, so that clients don't waste their valuable resources handling requests that are likely to fail. Using this concept, you can give the server some spare time to recover.
  ```
</details>

## Circuit Breaker with Hystrix





## Circuit Breaker with Resilience4J

--------------------------------------------------------------------------------------------------------

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
  
  
  
  
  
  
