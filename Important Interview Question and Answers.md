# JAVA Interview Questions & Answers
## Explain interface default methods

```
Interface is the blueprint of the class. Inorder to use it must be inherited with a class.
It may have both fields and methods.
All the Fields are public static final.
Methods are public abstract by default.
Non-static and default methods must have body. And also we can override into the inherited methods.
Interface static methods and fields can be used inside the inherited static methods only.
All the Interface methods must be overriden except default methods.
```
### Code Snippet :

 ```
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
____________________________________________________________________________________________

## Difference between Interface and Abstract class

### What is Abstract Class
```
Must be declared with abstract keyword.
An object can’t be created for this so it should be extended.
It can have both abstract and non-abstract methods. 
The abstract method must be overridden in sub-class and non-abstract methods are not required to override.
Non-abstract methods must have a method body.
It allows final methods also.
```
### Differences

| Abstract class | Interface |
| --- | --- |
| Abstract class doesn't support multiple inheritance. | Interface supports multiple inheritance. |
| Abstract class can have final, non-final, static and non-static variables. | Interface has only static and final variables. |
| Abstract class can have final methods. | Interface must have only non-final methods. |
| Abstract class can have constructors. | Interface can't have constructors. |

____________________________________________________________________________________________

## Abstract and Normal ( Concrete ) class

| Abstract class | Concrete Class |
| --- | --- |
| An abstract class cannot be directly instantiated using the new keyword. | A concrete class can be directly instantiated using the new keyword. |
| An abstract class may or may not contain abstract methods. | A concrete class cannot contain an abstract method. |
| An abstract class cannot be declared as final. | A concrete class can be declared as final. |
| Implement an interface is possible by not providing implementations of all of the interface’s methods. For this a child class is needed.. | Easy implementation of all of the methods in the interface. |


____________________________________________________________________________________________

## Why JAVA is not supporting the call by reference?

```
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

```
before - method call - a - 10
after - method call - a - 10
```

____________________________________________________________________________________________

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

## How to override static method possibilities?

```
Can we Override static methods in java? We can declare static methods with the same signature in the subclass, but it is not considered overriding as there won't be any run-time polymorphism. Hence the answer is 'No'.
```


## What is functional interface in java?

## What is the use of marker interface in java with example?

____________________________________________________________________________________________
____________________________________________________________________________________________

# Collections

## hashmap vs hashtable

## array list vs asList

## Set vs Map

## TreeMap vs HashMap

## Comparable vs comparator

hash table internal working

what is difference between comparable and comparator in java

difference between treemap and hashmap in java

Arraylist synchronised

Duplicate removal from list

why is rest api stateless

Design patterns and SOLID principles and Agile method

Java8 java 11 features

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

## springboot authentication

## spring boot latest version features

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

____________________________________________________________________________________________
____________________________________________________________________________________________


# JPA / Hibernate / DB Questions and Answers

## Spring boot cache

## How to write a select query with 2 schema postgres

## Jpa create table/column automatically configuration

## many to many / many to one

## left join - if condition not meet


