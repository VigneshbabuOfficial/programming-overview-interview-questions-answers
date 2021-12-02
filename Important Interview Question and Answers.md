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
By having private constructor we can't be extended to other classes.
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

## hashmap vs hashtable

## array list vs asList

## Set vs Map

## TreeMap vs HashMap

## Comparable vs comparator

## why java not support call by reference

hash table internal working
what is difference between comparable and comparator in java
difference between treemap and hashmap in java
Arraylist synchronised
Duplicate removal from list





Super method  and keyword - calling parent method
Constructor overloading

difference between classdefnotfoundexception and classnotfoundexception



why is rest api stateless

what is Serialization and its purpose
override static method possibilities

Design patterns and SOLID principles and Agile method

Java8 java 11 features
____________________________________________________________________________________________

# SPRING QUESTIONS & ANSWERS

## why rest api stateless

## @Qualifier

## how to access system properies

## what is singleton, how to achieve

## java 8 features

## what is AOP

## what are the beans available

## what are annotations used for controller class

## dependency injection

## IOC

## springboot authentication

what is functional interface in java
spring boot latest version features

what is purpose @qualifier in spring

concurrency exception

how to write a select query with 2 schema postgres

Jpa create table/column automatically configuration


#1 many to many / many to one
#2 left join - if condition not meet
#3 how to ignore a class in spring boot - https://stackoverflow.com/questions/55403688/exclude-configuration-from-spring-boot-application
#4 internal process of singleton and its purpose
#5 ways to connect DB in spring boot



difference b/w redirect and forward
RequestDispatcher - Forward - faster than redirect - lost original params and attributes - client side reflect will happen
HttpServletResponse  - Redirect -       - same request with original params and attributes used - client side no effect will happen




Spring boot cache

