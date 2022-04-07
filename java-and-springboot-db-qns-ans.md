# JAVA Interview Questions & Answers
## Explain interface default methods
<details>
<summary>:bulb:</summary>

```JS
Interface is the blueprint of the class. Inorder to use it must be inherited with a class.
It may have both fields and methods.
All the Fields are public static final by default.
Methods are public abstract by default.
Static and Default methods must have body.
Interface static methods and fields can be used inside the inherited static methods only.
All the Interface methods must be overriden except default and static methods.
```
```JAVA
 public interface TestingInterface {
	
	// public static final
	int a = 10;
	
	// public abstract
	void print();
	
	public default void show() {}

	static void showStatic() { System.out.println("Static Method Executed");}
	
	// Illegal modifier for the interface method showFinal; only public, private, abstract, default, static and strictfp are permitted
	//public static final void showFinal() {}

}

public class TestingInterfaceClass implements TestingInterface {

	@Override
	public void print() {
		// TODO Auto-generated method stub

	}

	// Cannot reduce the visibility of the inherited method from TestingInterface
	/*
	 * @Override public default void show() { // TODO Auto-generated method stub
	 * 
	 * }
	 */

	@Override
	public void show() {

	}

	// The method showStatic() of type TestingInterfaceClass must override or
	// implement a supertype method
	/*
	 * @Override static void showStatic() {
	 * 
	 * 
	 * }
	 */

	public static void main(String args[]) {

		// Interface static methods and fields can be used inside the inherited static methods only
		TestingInterface.showStatic();

		// The final field TestingInterface.a cannot be assigned
		// TestingInterface.a = 20;
	}
 
 ```	
</details>

## Difference between Interface and Abstract class

### What is Abstract Class
<details>
	<summary>:bulb:</summary>
	
```JS
Must be declared with abstract keyword.
An object can’t be created for this so it should be extended.
It can have both abstract and non-abstract methods. 
The abstract method must be overridden in sub-class and non-abstract methods are not required to override.
Non-abstract methods must have a method body.
It allows final methods also.
```
</details>

### Differences
<details>
	<summary>:bulb:</summary>
	
| Abstract class | Interface |
| --- | --- |
| Abstract class doesn't support multiple inheritance. | Interface supports multiple inheritance. |
| Abstract class can have final, non-final, static and non-static variables. | Interface has only static and final variables. |
| Abstract class can have final methods. | Interface must have only non-final methods. |
| Abstract class can have constructors. | Interface can't have constructors. |
</details>	


## Abstract and Normal ( Concrete ) class
<details>
	<summary>:bulb:</summary>
	
| Abstract class | Concrete Class |
| --- | --- |
| An abstract class cannot be directly instantiated using the new keyword. | A concrete class can be directly instantiated using the new keyword. |
| An abstract class may or may not contain abstract methods. | A concrete class cannot contain an abstract method. |
| An abstract class cannot be declared as final. | A concrete class can be declared as final. |
| Implement an interface is possible by not providing implementations of all of the interface’s methods. For this a child class is needed.. | Easy implementation of all of the methods in the interface. |
</details>


## Why JAVA is not supporting the call by reference?

https://youtu.be/L94X_orDVWw
<details>
	<summary>:bulb:</summary>
	
```JS
public class Exercises {
	
	static void callByReference(int b) {
		
		b = 100;
	}
	
	
	public static void main(String[] args) {
		
		int a = 10;
		
		System.out.println("before - method call - a - "+a);
		
		callByReference(a);
		
		System.out.println("after - method call - a - "+a);
	}

}

```

```JS
OUTPUT:
	
before - method call - a - 10
after - method call - a - 10
```
</details>


## How to achieve Immutable class?

```
The class must be declared as final so that child classes can’t be created.
Data members in the class must be declared private so that direct access is not allowed.
Data members in the class must be declared as final so that we can’t change the value of it after object creation.
A parameterized constructor should initialize all the fields performing a deep copy so that data members can’t be modified with an object reference.
There should be no setters or in simpler terms, there should be no option to change the value of the instance variable.
```
____________________________________________________________________________________________

## Explain string constant pool

```
String s1 = "java";
String s2 = "java";
String s3 = "java";
String s4 = new String("java");
------------------------------
s1 == s2
true
------------------------------
s1==s3
true
------------------------------
s1==s4
false
------------------------------
s1 = s1 + "J2EE";
s1==s2
false
------------------------------
```
![IMG_20211030_073830](https://user-images.githubusercontent.com/70185865/144313392-823498bf-ac22-48af-95f8-b578513b9305.jpg)
![IMG_20211030_073846](https://user-images.githubusercontent.com/70185865/144313480-1b03a2e9-0e5c-4b44-abfd-592f449e5ec7.jpg)

____________________________________________________________________________________________

## Exceptions

```
In Java, an exception is an event that disrupts the normal flow of the program which is thrown at runtime.
```

![IMG_20211030_080236](https://user-images.githubusercontent.com/70185865/144315203-ce13405a-3c8c-47f4-9600-0e2c203d8a5b.jpg)

____________________________________________________________________________________________

## Difference between super method  and keyword 

| Super method - super() | super keyword - super |
| --- | --- |
| The super() in Java is a reference variable that is used to refer parent class constructors. | The super keyword in Java is a reference variable that is used to refer parent class objects. |
| super can be used to call parent class’ variables and methods.| super() can be used to call parent class’ constructors only. |
| The variables and methods to be called through super keyword can be done at any time inside the **static** methods only. | Call to super() must be first statement in Derived(Student) Class constructor. |
| If one does not explicitly invoke a superclass variables or methods, by using super keyword, then nothing happens. | If a constructor does not explicitly invoke a superclass constructor by using super(), the Java compiler automatically inserts a call to the no-argument constructor of the superclass. |
____________________________________________________________________________________________

## Calling parent method and constructor

```
Parent constructor can be called by using super().
Parent methods and variables can be called from super keyword
```

### Code Snippet
```
public class Exercises2 {

	int Exercises2Var = 100;

	public Exercises2() {

		super();
		System.out.println("Exercises2 constructor is called");
	}

	public Exercises2(int b) {

		super();
		System.out.println("Exercises2 parameterized constructor is called - b = "+b);
	}

	public static void main(String[] args) {

	}

}

public class Exercises extends Exercises2{
	
	private Exercises() {
		
		// this will call the parent class constructor
		//super();
		
		// this will call the parent class parameterized constructor
		//super(1000);
		
		// if no super method is available then parent class default  constructor will be called 
		System.out.println("Exercises constructor is called");
	}
	
	void callByReference1(int b) {
		
		b = super.Exercises2Var;
	}
	
	
	public static void main(String[] args) {
		
		new Exercises();
		
		// ERR: Cannot use super in a static context
		// int b = super.Exercises2Var;
	}

}
```
____________________________________________________________________________________________

## Constructor overloading

```
public class Exercises extends Exercises2 {

	private Exercises() {

		// this will call the parent class constructor
		// super();

		// this will call the parent class parameterized constructor
		 super(1000);

		// if no super method is available then parent class default constructor will be
		// called
		System.out.println("Exercises constructor is called");
	}

	private Exercises(int a) {

		// if no super method is available then parent class default constructor will be called
		System.out.println("Exercises parameterized constructor is called - a ="+a);
	}

	void callByReference1(int b) {

		b = super.Exercises2Var;
	}

	public static void main(String[] args) {

		new Exercises();
		System.out.println("-----------------------------------------------");
		new Exercises(100);

	}

}
```

```
Exercises2 parameterized constructor is called - b = 1000
Exercises constructor is called
-----------------------------------------------
Exercises2 constructor is called
Exercises parameterized constructor is called - a =100
```
____________________________________________________________________________________________

## Difference between classdefnotfoundexception and classnotfoundexception

```
ClassNotFoundException is an exception that occurs when you try to load a class at run time using Class.
NoClassDefFoundError is an error that occurs when a particular class is present at compile time, but was missing at run time.
```
____________________________________________________________________________________________

## Concurrency exception

```
The ConcurrentModificationException occurs when an object is tried to be modified concurrently when it is not permissible. This exception usually comes when one is working with Java Collection classes.
```
```
NOTE : 
whenever using for-each loop, iterator is using behind. So, when we change the original collection values, iterator.next() will be executed and checks modCount. And so if any difference occurs it'll throw an error.
But, if we use normal for loop with index, it'll directly add / remove element original collection and the size will changed dynamically based on the operations. So, we won't get any exceptions.
```

### Code Snippet
```
package basics;

import java.util.ArrayList;
import java.util.List;

public class Exercises {

	public static void main(String[] args) {

		List<String> listOfBooks = new ArrayList<>();
		listOfBooks.add("Programming Pearls");
		listOfBooks.add("Clean Code");
		listOfBooks.add("Effective Java");
		listOfBooks.add("Code Complete");
		// Using forEach loop to iterate and removing
		// element during iteration will
		// throw // ConcurrentModificationException in Java
		for (String book : listOfBooks) {
			if (book.contains("Code"))
			{
				listOfBooks.remove(book);
			}
		}

	}

}

OUTPUT:
Exception in thread "main" java.util.ConcurrentModificationException
	at java.base/java.util.ArrayList$Itr.checkForComodification(ArrayList.java:1013)
	at java.base/java.util.ArrayList$Itr.next(ArrayList.java:967)
	at basics.Exercises.main(Exercises.java:18)


---------------------------------------------------------------------------

package basics;

import java.util.ArrayList;
import java.util.List;

public class Exercises {

	public static void main(String[] args) {

		List<String> listOfBooks = new ArrayList<>();
		listOfBooks.add("Clean Code");
		listOfBooks.add("Effective Java");
		listOfBooks.add("Code Complete");
		listOfBooks.add("Programming Pearls");

		System.out.println("List before : " + listOfBooks);
		for (int i = 0; i < listOfBooks.size(); i++) {
			System.out.println("listOfBooks.size() = "+listOfBooks.size()+" - index ="+i);
			String book = listOfBooks.get(i);
			if (book.contains("Programming")) {
				System.out.println("Removing " + book);
				listOfBooks.remove(i); // will throw CME
				System.out.println("after removed - listOfBooks.size() = "+listOfBooks.size()+" - index ="+i);
			}
		}
		System.out.println("List after : " + listOfBooks);
	}
}

OUTPUT:
List before : [Clean Code, Effective Java, Code Complete, Programming Pearls]
listOfBooks.size() = 4 - index =0
listOfBooks.size() = 4 - index =1
listOfBooks.size() = 4 - index =2
listOfBooks.size() = 4 - index =3
Removing Programming Pearls
after removed - listOfBooks.size() = 3 - index =3
List after : [Clean Code, Effective Java, Code Complete]
```

____________________________________________________________________________________________

## what is Serialization and its purpose
```
Serialization is the process of converting an object into a stream of bytes to store the object or transmit it to memory, a database, or a file. Its main purpose is to save the state of an object in order to be able to recreate it when needed.
```
____________________________________________________________________________________________

## Override static methods?
```
Can we Override static methods in java? We can declare static methods with the same signature in the subclass, but it is not considered overriding as there won't be any run-time polymorphism. Hence the answer is 'No'.
```

## What is Functional Interface in java?
```
A functional interface has only one abstract method but it can have multiple default methods.
@FunctionalInterface annotation is used to ensure an interface can’t have more than one abstract method. The use of this annotation is optional.

The major benefit of java 8 functional interfaces is that we can use lambda expressions to instantiate them and avoid using bulky anonymous class implementation.
```
### Code Snippet
```
// Java program to demonstrate lambda expressions to implement
// a user defined functional interface.

@FunctionalInterface
interface Square
{
	int calculate(int x);
}

class Test
{
	public static void main(String args[])
	{
		int a = 5;

		// lambda expression to define the calculate method
		Square s = (int x)->x*x;

		// parameter passed and return type must be
		// same as defined in the prototype
		int ans = s.calculate(a);
		System.out.println(ans);
	}
}


Output: 
25
```

## What is the use of Marker Interface in java with example?
```
A marker interface is an interface that has no methods or constants inside it. It provides run-time type information about objects, so the compiler and JVM have additional information about the object. A marker interface is also called a tagging interface.

Example: In DTO fields we can enable the validation for the specific fields by using marker interface.
```

## Design patterns and SOLID principles and Agile method

## Java8, Java 11 & Java 16 features

### JAVA 8 FEATURES

Reference:
```JAVA
package basics;

interface Sayable{  
    public String say();  
} 

interface Sayable1{  
    public void say1();  
} 

public class Java8Features {
	
	
	public static void saySomething(){  
        System.out.println( "This is an example for Method Reference");  
    }  

	public static void main(String[] args) {

		// Lambda expressions
		Sayable s=()->{  
	        return "This is an example for Lambda expressions";  
	    };  
	    System.out.println(s.say());  
	    
	    
	    // Method Reference
	    Sayable1 sayable = Java8Features::saySomething;  
        // Calling interface method  
        sayable.say1();  
		
	}

}


OUTPUT:
This is an example for Lambda expressions
This is an example for Method Reference

```

	
#### Lambda Expression
`
A lambda expression is a short block of code which takes in parameters and returns a value. Lambda expressions are similar to methods, but they do not need a name and 	they can be implemented right in the body of a method.
`
#### Method Reference
`
Its a new technique where we can use method name along with class name or interface like InterFace::methodName / ClassName::methodName inorder to complete a specific task.
`
##### Code Snippet
```
class MRClass {
	
	static String showMethod(String str) {
		return "MRClass - "+str+" - ";
	}
}

interface MRInterface {
	
	static String showMethod(String str) {
		return "MRInterface - "+str+" - ";
	}
}


public class Exercises2 {


public static void main(String[] args) {

List<String> strList = Arrays.asList("aaaa","bbbb","cccc");

System.out.println("====================MRClass::showMethod==============================");
strList.stream().map(MRClass::showMethod).forEach(System.out::println);
		
System.out.println("====================MRInterface::showMethod==============================");
strList.stream().map(MRInterface::showMethod).forEach(System.out::println);

}

}

OUTPUT:
====================MRClass::showMethod==============================
MRClass - aaaa - 
MRClass - bbbb - 
MRClass - cccc - 
====================MRInterface::showMethod==============================
MRInterface - aaaa - 
MRInterface - bbbb - 
MRInterface - cccc - 
```

#### Functional interfaces
[what-is-functional-interface-in-java](https://github.com/VigneshOfficial2020/programming-overview-interview-questions-answers/blob/main/java-and-springboot-db-qns-ans.md#what-is-functional-interface-in-java)

#### Stream API
`
Java provides a new additional package in Java 8 called java.util.stream. This package consists of classes, interfaces and enum to allows functional-style operations on the elements. 
`

#### Default methods
[interface-default-methods](https://github.com/VigneshOfficial2020/programming-overview-interview-questions-answers/blob/main/java-and-springboot-db-qns-ans.md#explain-interface-default-methods)

#### Static methods in interface

#### Optional class
[optional class](https://github.com/VigneshOfficial2020/programming-overview-interview-questions-answers/blob/main/java-and-springboot-db-qns-ans.md#optional-hands-on)

#### Collectors class
`
Collectors is a final class that extends Object class. It provides reduction operations, such as accumulating elements into collections, summarizing elements according to various criteria 
`

#### ForEach() method

## Java 11 features

#### Running Java File with single command - java Classname, means we dont need to compile using javac.
#### Java String Methods - .isBlank(), .lines(), strip(), stripLeading(), stripTrailing()
#### Collection to an Array
```JAVA
List sampleList = Arrays.asList("Java", "Kotlin");
String[] sampleArray = sampleList.toArray(String[]::new);
```
#### Not Predicate Method
```JAVA
List<String> sampleList = Arrays.asList("Java", "\n \n", "Kotlin", " ");
List withoutBlanks = sampleList.stream()
  .filter(Predicate.not(String::isBlank))
  .collect(Collectors.toList());
```
#### Local-Variable Syntax for Lambda
```JAVA
List<String> sampleList = Arrays.asList("Java", "Kotlin");
String resultString = sampleList.stream()
  .map((@Nonnull var x) -> x.toUpperCase())
  .collect(Collectors.joining(", "));
```

#### Nested Based Access Control
```
public class Main {
 
    public void myPublic() {
    }
 
    private void myPrivate() {
    }
 
    class Nested {
 
        public void nestedPublic() {
            myPrivate();
        }
    }
}

```

## Java 16 features

#### Sealed Classes

## How to use generic for arguments in method

## How to send HTTP request and receive HTTP response
#### Java 11 HttpClient
```
package basics;

import java.net.URI;
import java.net.URLEncoder;
import java.net.http.HttpClient;
import java.net.http.HttpRequest;
import java.net.http.HttpResponse;
import java.nio.charset.StandardCharsets;
import java.util.HashMap;
import java.util.Map;

public class HttpClientExample {

	// one instance, reuse
    private final HttpClient httpClient = HttpClient.newBuilder()
            .version(HttpClient.Version.HTTP_2)
            .build();

    public static void main(String[] args) throws Exception {

    	HttpClientExample obj = new HttpClientExample();

        System.out.println("Testing 1 - Send Http GET request");
        obj.sendGet();

        System.out.println("Testing 2 - Send Http POST request");
        obj.sendPost();

    }

    private void sendGet() throws Exception {

        HttpRequest request = HttpRequest.newBuilder()
                .GET()
                .uri(URI.create("https://httpbin.org/get"))
                .setHeader("User-Agent", "Java 11 HttpClient Bot")
                .build();

        HttpResponse<String> response = httpClient.send(request, HttpResponse.BodyHandlers.ofString());

        // print status code
        System.out.println(response.statusCode());

        // print response body
        System.out.println(response.body());

    }

    private void sendPost() throws Exception {

        // form parameters
        Map<Object, Object> data = new HashMap<>();
        data.put("username", "abc");
        data.put("password", "123");
        data.put("custom", "secret");
        data.put("ts", System.currentTimeMillis());

        HttpRequest request = HttpRequest.newBuilder()
                .POST(buildFormDataFromMap(data))
                .uri(URI.create("https://httpbin.org/post"))
                .setHeader("User-Agent", "Java 11 HttpClient Bot") // add request header
                .header("Content-Type", "application/x-www-form-urlencoded")
                .build();

        HttpResponse<String> response = httpClient.send(request, HttpResponse.BodyHandlers.ofString());

        // print status code
        System.out.println(response.statusCode());

        // print response body
        System.out.println(response.body());

    }

    private static HttpRequest.BodyPublisher buildFormDataFromMap(Map<Object, Object> data) {
        var builder = new StringBuilder();
        for (Map.Entry<Object, Object> entry : data.entrySet()) {
            if (builder.length() > 0) {
                builder.append("&");
            }
            builder.append(URLEncoder.encode(entry.getKey().toString(), StandardCharsets.UTF_8));
            builder.append("=");
            builder.append(URLEncoder.encode(entry.getValue().toString(), StandardCharsets.UTF_8));
        }
        System.out.println(builder.toString());
        return HttpRequest.BodyPublishers.ofString(builder.toString());
    }
}

```

## Optional Hands on 

```JS
This type of execution mostly usedin API side. the value will be retrieved and update if value is present in payload otherwise not.
```

### Fields declaration

```JS
private String				testField1;
private Optional<String>	testField2;
private Boolean				testFieldBool1;
private Optional<Boolean>	testFieldBool2;


public String getTestField1() {

	return testField1;
}


public void setTestField1( String testField1 ) {

	this.testField1 = testField1;
}


public Optional<String> getTestField2() {

	return testField2;
}


public void setTestField2( Optional<String> testField2 ) {

	this.testField2 = testField2;
}


public Boolean getTestFieldBool1() {

	return testFieldBool1;
}


public void setTestFieldBool1( Boolean testFieldBool1 ) {

	this.testFieldBool1 = testFieldBool1;
}


public Optional<Boolean> getTestFieldBool2() {

	return testFieldBool2;
}


public void setTestFieldBool2( Optional<Boolean> testFieldBool2 ) {

	this.testFieldBool2 = testFieldBool2;
}
```

------------------------------------------

### PAYLOAD

```JS
{
    "testField1":"testField1",
    "testField2":"testField1",
    "testFieldBool1":false,
    "testFieldBool2":true  
}

```

------------------------------------------------

### CODE SNIPPET

```JS
System.out.println( " userDTO.getTestField1()  = " + userDTO.getTestField1() );
System.out.println( " userDTO.getTestField2() = " + userDTO.getTestField2() );
System.out.println( " Optional.ofNullable( userDTO.getTestField2() ).isPresent() = " + Optional.ofNullable( userDTO.getTestField2() ).isPresent() );
System.out.println( " userDTO.getTestField2().isPresent() = " + userDTO.getTestField2().isPresent() );
System.out.println( " userDTO.getTestField2().get() = " + userDTO.getTestField2().get() );
System.out.println( " userDTO.isTestFieldBool1() = " + userDTO.getTestFieldBool1() );
System.out.println( " Optional.ofNullable( userDTO.getTestFieldBool2() ).isPresent() = " + Optional.ofNullable( userDTO.getTestFieldBool2() ).isPresent() );
System.out.println( " userDTO.getTestFieldBool2().isPresent() = " + userDTO.getTestFieldBool2().isPresent() );
System.out.println( " userDTO.getTestFieldBool2().get() = " + userDTO.getTestFieldBool2().get() );
```

------------------------------------------

### OUTPUT

```JS
userDTO.getTestField1()  = testField1

userDTO.getTestField2() = Optional[testField1]

Optional.ofNullable( userDTO.getTestField2() ).isPresent() = true

userDTO.getTestField2().isPresent() = true

userDTO.getTestField2().get() = testField1

userDTO.isTestFieldBool1() = false

Optional.ofNullable( userDTO.getTestFieldBool2() ).isPresent() = true

userDTO.getTestFieldBool2().isPresent() = true

userDTO.getTestFieldBool2().get() = true
```

____________________________________________________________________________________________

# Multithread Qns

## What if we call Java run() method directly instead start() method?
<details>
<summary>:bulb:</summary>
	
```JS
    class TestCallRun2 extends Thread{  
     public void run(){  
      for(int i=1;i<5;i++){  
        try{Thread.sleep(500);}catch(InterruptedException e){System.out.println(e);}  
        System.out.println(i);  
      }  
     }  
     public static void main(String args[]){  
      TestCallRun2 t1=new TestCallRun2();  
      TestCallRun2 t2=new TestCallRun2();  
       
      t1.run();  
      t2.run();  
     }  
    }  

OUTPUT:
1
2
3
4
1
2
3
4
			    
As we can see in the above program that there is no context-switching because here t1 and t2 will be treated as normal object not thread object.
```
			    
</details>

## Can we start a thread twice?
<details>
<summary>:bulb:</summary>
	
```JS
No. After starting a thread, it can never be started again. If you does so, an IllegalThreadStateException is thrown. In such case, thread will run once but for second time, it will throw exception.
	
```
			    
</details>

## Dead Lock?
<details>
<summary>:bulb:</summary>
	
```JS
It’s a situation where a thread is waiting for an object lock that is acquired by another thread and 2nd thread is also waiting for an object lock that is acquired by another thread. So process execution stops since both threads are waiting for each other.
To Avoid : 
Avoid nested locks.
Use the join method.
```
</details>

____________________________________________________________________________________________

# Collections Interview Questions and Answers

## What is Collection?
```JS
The Collection in Java is a framework that provides an architecture to store and manipulate the group of objects.
```
![image](https://user-images.githubusercontent.com/70185865/149058901-ce95e647-676b-4a19-9c9e-1d5dc209c12e.png)

## ArrayList
```JS
Implements List interface. 
Uses a dynamic array internally to store the elements. 
Allows duplicate element of different data types. 
Allows null values.
Maintains the insertion order.
Non-Synchronized. 
Best for accessing randomly.
```

## LinkedList
```JS
Implements List and Queue.
Uses a doubly linked list internally to store the elements. 
Allows duplicate elements. 
Allows null values.
Maintains the insertion order
Non-Synchronized.
Best for manipulating the data.
```
## ArrayList Vs LinkedList
![image](https://user-images.githubusercontent.com/70185865/149060098-5914b8ac-f6fd-4a71-b046-0cbdaf8f272a.png)




## Hashmap vs hashtable

## ArrayList vs Arrays.asList

## Set vs Map

## TreeMap vs HashMap

## Hash table internal working

## What is difference between comparable and comparator in java

## Difference between Treemap and Hashmap in java

## How to create Arraylist as Synchronised

## Duplicate removal from list

## Difference between collecctions/stream

____________________________________________________________________________________________
____________________________________________________________________________________________

# SPRING QUESTIONS & ANSWERS

## why rest api stateless?
```
REST stands for representational state transfer.
Being stateless makes REST APIs less complex – by removing all server-side state synchronization logic. A stateless API is also easy to cache as well. ... The server never loses track of “where” each client is in the application because the client sends all necessary information with each request.
```

## What is stateless and stateful in REST API?

```
Stateless Protocol does not require the server to retain the server information or session details. Stateful Protocol require server to save the status and session information. In Stateless Protocol, there is no tight dependency between server and client.
```

## What is @Qualifier and it's usage and what is purpose @qualifier in spring?
```
The @Qualifier annotation is used to resolve the autowiring conflict, when there are multiple beans of same type. The @Qualifier annotation can be used on any class annotated with @Component or on method annotated with @Bean . This annotation can also be applied on constructor arguments or method parameters
```

## How to access system properties?
```
System.getProperty("library.system.property")
@value(${library.system.property})
```

## What is Singleton?  
```
A singleton is a class that allows only a single instance of itself to be created and gives access to that created instance.
```

## How to achieve Singleton?

```
Make constructor private.
Write a static method that has return type object of this singleton class.
```
### Code Snippet

```
// Java program implementing Singleton class
// with using getInstance() method

// Class 1
// Helper class
class Singleton {
	// Static variable reference of single_instance
	// of type Singleton
	private static Singleton single_instance = null;

	// Declaring a variable of type String
	public String s;

	// Constructor
	// Here we will be creating private constructor
	// restricted to this class itself
	private Singleton()
	{
		s = "Hello I am a string part of Singleton class";
	}

	// Static method
	// Static method to create instance of Singleton class
	public static Singleton getInstance()
	{
		if (single_instance == null)
			single_instance = new Singleton();

		return single_instance;
	}
}

// Class 2
// Main class
class GFG {
	// Main driver method
	public static void main(String args[])
	{
		// Instantiating Singleton class with variable x
		Singleton x = Singleton.getInstance();

		// Instantiating Singleton class with variable y
		Singleton y = Singleton.getInstance();

		// Instantiating Singleton class with variable z
		Singleton z = Singleton.getInstance();

		// Printing the hash code for above variable as
		// declared
		System.out.println("Hashcode of x is "
						+ x.hashCode());
		System.out.println("Hashcode of y is "
						+ y.hashCode());
		System.out.println("Hashcode of z is "
						+ z.hashCode());

		// Condition check
		if (x == y && y == z) {

			// Print statement
			System.out.println(
				"Three objects point to the same memory location on the heap i.e, to the same object");
		}

		else {
			// Print statement
			System.out.println(
				"Three objects DO NOT point to the same memory location on the heap");
		}
	}
}

------------------------------------------------------------------------------------

OUTPUT:
Hashcode of x is 558638686
Hashcode of y is 558638686
Hashcode of z is 558638686
Three objects point to the same memory location on the heap i.e, to the same object
```

## What is AOP?

```
AOP (Aspect-Oriented Programming) is a programming pattern that increases modularity by allowing the separation of the cross-cutting concern.
```

## What are annotations used for controller class
```
@RestController is a convenience annotation for creating Restful controllers
```

## What is Dependency Injection?
```
It's a technique work done by the use of another class. It can be done by normal setter, by constructor and by @Autowired.
```

## What is IOC?
```
It's a framework for implementing automatic dependency injection. The IoC container creates an object of the specified class and also injects the dependency objects through a constructor, a property or a method at run time and disposes it at the appropriate time.
```

## Spring-boot Authentication

## Spring-boot latest version features

## How to ignore a class in spring boot 
https://stackoverflow.com/questions/55403688/exclude-configuration-from-spring-boot-application

```
@SpringBootApplication(exclude= {WorkerExecutors.class, Worker.class,WorkerConfig.class})
public class Application {
```

## Internal process of singleton and its purpose

[singleton](https://github.com/VigneshOfficial2020/interview-questions-answers/blob/main/Important%20Interview%20Question%20and%20Answers.md#what-is-singleton)

## Ways to connect DB in spring boot
```
From Application.properties file

spring.jpa.hibernate.ddl-auto=none
spring.datasource.url=<<JDBC_URL>>
spring.datasource.username=<<user_name>>
spring.datasource.password=<<password>>
```

## Difference b/w Redirect and Forward

| Forward | Redirect |
| --- | --- |
| The client isn't impacted by forward, URL in a browser stays the same. | The client will see the URL change after the redirect. |
| Request attributes and  parameters will be the same. | A new request is created. So, params and aattributes will get lost. |
| RequestDispatcher rd = request.getRequestDispatcher(request.getContextPath()); rd.forward(request, response); | resp.sendRedirect(req.getContextPath() + "/redirected"); |


## Spring security in spring boot

## How to communicate between applications in spring boot
```
That depends on your choice, weather you want sync communication or async communication between your services.

For sync services you can use either of these 3rd party tools:
Hashcorp Consul
Netflix Eureka [You may client load balancing using Netflix RIBBON ]
NATS etc

For Async you can use messaging solutions like:
Redis [use list/streams]
ActiveMQ
RabitMQ
Kafka
NATS etc
```

## Fail fast and fail safe difference
```
The major difference is fail-safe iterator doesn’t throw any Exception, contrary to fail-fast Iterator.This is because they work on a clone of Collection instead of the original collection and that’s why they are called as the fail-safe iterator.
```
### Fail fast - Code Snippet
```
// Java code to demonstrate remove
// case in Fail-fast iterators

import java.util.ArrayList;
import java.util.Iterator;

public class FailFastExample {
	public static void main(String[] args)
	{
		ArrayList<Integer> al = new ArrayList<>();
		al.add(1);
		al.add(2);
		al.add(3);
		al.add(4);
		al.add(5);

		Iterator<Integer> itr = al.iterator();
		while (itr.hasNext()) {
			if (itr.next() == 2) {
				// will not throw Exception
				itr.remove();
			}
		}

		System.out.println(al);

		itr = al.iterator();
		while (itr.hasNext()) {
			if (itr.next() == 3) {
				// will throw Exception on
				// next call of next() method
				al.remove(3);
			}
		}
	}
}


OUTPUT:
[1, 3, 4, 5]
Exception in thread "main" java.util.ConcurrentModificationException
    at java.util.ArrayList$Itr.checkForComodification(ArrayList.java:901)
    at java.util.ArrayList$Itr.next(ArrayList.java:851)
    at FailFastExample.main(FailFastExample.java:28)
```

### Fail safe - Code Snippet
```
// Java code to illustrate
// Fail Safe Iterator in Java
import java.util.concurrent.CopyOnWriteArrayList;
import java.util.Iterator;

class FailSafe {
	public static void main(String args[])
	{
		CopyOnWriteArrayList<Integer> list
			= new CopyOnWriteArrayList<Integer>(new Integer[] { 1, 3, 5, 8 });
		Iterator itr = list.iterator();
		while (itr.hasNext()) {
			Integer no = (Integer)itr.next();
			System.out.println(no);
			if (no == 8)

				// This will not print,
				// hence it has created separate copy
				list.add(14);
		}
	}
}


OUTPUT:
1
3
5
8
```
## What is Spring boot Auto configuration
```
Spring Boot auto-configuration automatically configures the Spring application based on the jar dependencies that we have added.

For example, if the H2 database Jar is present in the classpath and we have not configured any beans related to the database manually, the Spring Boot's auto-configuration feature automatically configures it in the project.

We can enable the auto-configuration feature by using the annotation @EnableAutoConfiguration. But this annotation does not use because it is wrapped inside the @SpringBootApplication annotation. The annotation @SpringBootApplication is the combination of three annotations: @ComponentScan, @EnableAutoConfiguration, and @Configuration. However, we use @SpringBootApplication annotation instead of using @EnableAutoConfiguration.

@SpringBootApplication=@ComponentScan+@EnableAutoConfiguration+@Configuration
```

## Differnece between Spring And Spring boot
![image](https://user-images.githubusercontent.com/70185865/144986167-5aa51ca3-8a01-402e-8afb-b5a8382c1ba3.png)

## How to exclude classes in spring boot
```
@ComponentScan(excludeFilters  = {@ComponentScan.Filter(
              type = FilterType.ASSIGNABLE_TYPE, classes = {WorkerConfig.class, WorkerExecutors.class, Worker.class})})
```

## How Spring boot application works internally?
![spring-boot-internal-working-diag](https://user-images.githubusercontent.com/70185865/146032786-004189ff-480a-45e1-96f1-b6ff980800e3.png)


____________________________________________________________________________________________
____________________________________________________________________________________________


# JPA / Hibernate / DB Questions and Answers

## Spring boot cache
https://github.com/VigneshOfficial2020/spring-boot-cache-demo-app

## How to write a select query with 2 schema postgres

## Jpa create table/column automatically configuration
```
# if any table or column is missing in DB below command will create them specifically during build process
spring.jpa.generate-ddl=true

# if any table or column is missing in DB below command will drop and create them during build process
#spring.jpa.hibernate.ddl-auto = update 
#spring.jpa.hibernate.ddl-auto = create
```

## many to many / many to one / one to many associations
```
many to one
-----------
===== >>> in the table_1

@JsonIgnore
@ManyToOne(fetch = FetchType.LAZY, cascade = CascadeType.MERGE)
@JoinColumn(name = "table_2_id")
private Table_2									table_2;


One To Many / ManyToMany
-------------------------
===== >>>> in the table_2

@JsonManagedReference
@OneToMany(fetch = FetchType.LAZY, mappedBy = "table_1", cascade = { CascadeType.MERGE })
@Where(clause = "status <> 'deleted'")
@OrderBy(value = "name ASC")
private List<Table_1>				table_1						= new ArrayList<>();

```

## What will return on left outer join - if condition not meet with table_2
```
table_2 values will be shown as null.
```
ref: https://towardsdatascience.com/what-is-the-difference-between-an-inner-and-an-outer-join-in-sql-5b5ec8277377

## Postgres cheat-sheet

![image](https://user-images.githubusercontent.com/70185865/145044344-bddd2f6e-4180-4028-a990-7f25564a6b12.png)

![image](https://user-images.githubusercontent.com/70185865/145044398-6c172bea-a4bb-4e32-90dc-dd0de4a351f2.png)

![image](https://user-images.githubusercontent.com/70185865/145044446-d620a8fc-34a4-43d3-9470-1fe983dc0289.png)


## Difference between Truncate, DROP & DELETE
```
The DELETE statement scans every row before deleting it. Thus it is slower as compared to TRUNCATE command. If we want to delete all the records of a table, it is preferable to use TRUNCATE in place of DELETE.

A DROP statement in SQL removes a component from a relational database management system (RDBMS). DROP is a DDL Command. Objects deleted using DROP are permanently lost and it cannot be rolled back.
```
ref : https://afteracademy.com/blog/what-is-the-difference-between-truncate-delete-and-drop-statements

## Rename the column name and change the type
```
ALTER TABLE public.clients
    ALTER COLUMN client_name_1 type int
	using client_name_1::integer;
	
ALTER TABLE public.clients
    ALTER COLUMN client_name_1 type varchar;	
	
	
ALTER TABLE public.clients RENAME COLUMN client_name_1 to client_name_2;
```

## Postgres queries examples
https://www.enterprisedb.com/postgres-tutorials/postgresql-query-introduction-explanation-and-50-examples

## Explain Transactional annnotation ( @Transactional )
`It used to provide database transaction for the queries which we used to execute or by using jpa methods. So, whenever exception occurs this will be roll back automatically.`

### Propagation
#### Required , Nested  SUPPORTS , MANDATORY , NEVER , NOT_SUPPORTED , REQUIRES_NEW 

### Isolation
#### READ_UNCOMMITTED , READ_COMMITTED , 
	
## How to find second max in sql


![image](https://user-images.githubusercontent.com/70185865/145718507-9a82a743-39fa-4614-84a2-cb9a91883679.png)

```
SELECT
	product_id,
	product_name,
	group_name,
	price,
	RANK () OVER ( 
		PARTITION BY p.group_id
		ORDER BY price DESC
	) price_rank ,
	p.group_id 
FROM
	product p
	INNER JOIN product_group g 
		ON g.group_id = p.group_id;
```
![image](https://user-images.githubusercontent.com/70185865/145718631-3438b2a6-cd4d-4133-a142-35c0aa07d304.png)

```
SELECT 
    product_id,
    product_name,
    price,
    group_id,
	RANK () OVER ( 
		PARTITION BY group_id
		ORDER BY price DESC
	) price_rank ,
    NTH_VALUE(product_name, 2) 
    OVER(
        PARTITION BY group_id
        ORDER BY price DESC
        RANGE BETWEEN 
            UNBOUNDED PRECEDING AND 
            UNBOUNDED FOLLOWING
    ) 
FROM 
    product;
```
![image](https://user-images.githubusercontent.com/70185865/145718771-b5abc0e6-0461-4356-a40f-033b57dae086.png)

SECOND MAXIMUM
```
SELECT p.product_name 
FROM (
      SELECT product_name,
          DENSE_RANK() OVER ( ORDER BY price DESC ) AS RANK 
      FROM product
	  WHERE group_id = 1
      ) as p 
WHERE p.rank = 2


OUTPUT:
Nexus
```


## why indexes used

# POSTGRES NOTES

```JS

BEGIN;
SAVEPOINT MY_SAVE;
DELETE FROM table1;
SAVEPOINT MY_SAVE1;
SELECT * FROM table1;
ROLLBACK TO SAVEPOINT MY_SAVE;
SELECT * FROM table1;
COMMIT;

```

## HTTP STATUS CODES
### Information responses
#### 100
<details>
<summary>:bulb:</summary>
	
```JS
100 Continue,  indicates that everything so far is OK and that the client should continue with the request or ignore it if it is already finished. 
```
</details>
	
#### 101
<details>
<summary>:bulb:</summary>
	
```JS
101 Switching Protocols,indicates a protocol to which the server switches. The protocol is specified in the Upgrade request header received from a client. 
```
</details>
	
#### 102
<details>
<summary>:bulb:</summary>
	
```JS
102 Processing, indicates that the server has received and is processing the request, but no response is available yet.
```
</details>

### Successful responses
#### 200	
<details>
<summary>:bulb:</summary>
	
```JS
200 OK    The request succeeded. 
```
</details>
	
#### 201
<details>
<summary>:bulb:</summary>
	
```JS
201 Created, The request succeeded, and a new resource was created as a result. This is typically the response sent after POST requests, or some PUT requests.
```
</details>
	
#### 202
<details>
<summary>:bulb:</summary>
	
```JS
202 Accepted, The request has been received but not yet acted upon. It is intended for cases where another process or server handles the request, or for batch processing. 
```
</details>	
	
#### [203](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/203)
	
#### 204
<details>
<summary>:bulb:</summary>
	
```JS
204 No Content. There is no content to send for this request, but the headers may be useful. 
```
</details>
	
#### 205
<details>
<summary>:bulb:</summary>
	
```JS
The HTTP 205 Reset Content response status tells the client to reset the document view, so for example to clear the content of a form, reset a canvas state, or to refresh the UI. 
```
</details>
	
#### 206
<details>
<summary>:bulb:</summary>
	
```JS
206 Partial Content success status response code indicates that the request has succeeded and the body contains the requested ranges of data, as described in the Range header of the request.  
```
</details>
	
### Redirection messages
#### 301
<details>
<summary>:bulb:</summary>
	
```JS
301 Moved Permanently, The URL of the requested resource has been changed permanently. The new URL is given in the response.  
```
</details>
	
#### 302
<details>
<summary>:bulb:</summary>
	
```JS
302 Found, This response code means that the URI of requested resource has been changed temporarily. Further changes in the URI might be made in the future. Therefore, this same URI should be used by the client in future requests.

```
</details>
