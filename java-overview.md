
#### Reference
[java-tutorial](https://github.com/VigneshOfficial2020/java-tutorial)

## What is Java?
<details>
<summary>:bulb:</summary>
	
```JS
Java is a programming language and a platform. Java is a high-level, robust, object-oriented, and secure programming language.
```
</details>

## TYPES OF JAVA APPLICATION
```JS
Standalone
Web Application
Enterprise
Mobile Application
```
## JDK, JRE & JVM
![image](https://user-images.githubusercontent.com/70185865/154610017-db1e064a-c8d6-46c8-8ee4-9a9d2418382f.png)

## Class
```JS
Syntax:-

class <<class_name>> {
      variables
      methods
}
```
## Variables
```JS
Syntax:=

<<access_modifier>> 
                    <<static>> ( optioanl )
                                            <<data_type>>
                                                          <<identifier_name>>
                                                                              =  <<value>>
```
## Variable Types
```JS
Local - Declared inside the body of the method
Instance - Declared inside the class and outside the method
Static - Same as instance variable but the memory allocation is happened only once when the class is loaded in memory
```
### Static
```JS
It can be used for blocks, variables, methods and classes

When a member is created as static, the memory allocation happens only once when the class is loaded.

When a member is declared as static, it can be accessed without any object reference.
```
```diff
- NOTE: Object reference is needed if we try to access the non-static members from static method. (E.g) main method.
```
```JS
package basics;

public class Practice {
	public static void main(String[] args) {
		Testing.m1();
		Testing t = new Testing();
		t.m1();
	}
}

class Testing {
	static void m1() {
		System.out.println("Testing - m1()");
	}
}

--------------

output:=

Testing - m1()
Testing - m1()

```

### JAVA CODE EXECUTION

![image](https://user-images.githubusercontent.com/70185865/158194434-26bc695d-dcf4-4069-8156-d96e1aa38751.png)

### Access Specifier

| Access Type | Within class | Within Package | Outside the package by subclass | Outside the package |
| --- | --- | --- | --- | --- |
| private | :heavy_check_mark: | :wavy_dash: | :wavy_dash: | :wavy_dash: |
| default | :heavy_check_mark: | :heavy_check_mark: | :wavy_dash: | :wavy_dash: |
| protected | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :wavy_dash: |
| public | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |

```JAVA
default -  If access type is not specified

protected - Variables, methods, and constructors, which are declared protected in a superclass can be accessed only by the subclasses in other package or any class within the package of the protected members' class. The protected access modifier cannot be applied to class and interfaces
```

### Non-Access Modifier
#### static
[static](https://github.com/VigneshOfficial2020/programming-overview-interview-questions-answers/blob/main/java-overview.md#static)

#### final
```JAVA
final variable -> to create constant variable
final methods  -> to prevent method overriding
final class    -> to prevent inheritance
````
```JAVA
we can initialize / decalare a final variable but it should be defined inside a block.

static variable into static block
non-static variable into noon-static block
but we can't initialize inside the main and other methods
```
##### final keyword example
https://github.com/VigneshOfficial2020/java-tutorial/commit/87d28acebf432a5bbe688dd01f8ea80c5ed3951c
```JAVA

package basics;

public class Practice {

	final int a;
	final static int b;
	final int c=10;
	final static int d=100;

	{
		a = 25;
		
//		ERROR : The final field Practice.b cannot be assigned -> static TO static concept
//		b = 25;
		
//		ERROR : The final field Practice.c cannot be assigned
//		c = 25;
		
//		ERROR : The final field Practice.d cannot be assigned
//		d = 25;
	}

	static {
		
//		ERROR : Cannot make a static reference to the non-static field a
//		a = 25;
		
		b = 25;
		
//		ERROR : Cannot make a static reference to the non-static field c
//		c = 25;
		
//		ERROR : The final field Practice.d cannot be assigned
//		d = 25;
	}

	private void assign() {
		
//		ERROR : The final field Practice.a b c d cannot be assigned
//		a = 25;
//		b = 25;
//		c = 25;
//		d = 25;
		
	}

	public static void main(String[] args) {
		
//		ERROR : Cannot make a static reference to the non-static field a
//		a = 25;
		
//		ERROR : The final field Practice.b cannot be assigned
//		b = 25;
		
//		ERROR : Cannot make a static reference to the non-static field c
//		c = 15;
		
//		ERROR : The final field Practice.d cannot be assigned
//		d = 15;
		
	}

}

```

#### abstarct
#### transient
```JS
It's a variable modifier used in the time of serialization.
It's used to mark the variable not to be serialized.
```
##### transient example

https://github.com/VigneshOfficial2020/java-tutorial/commit/a6ced66f247febc85b1983a13e9e9f6c64d4c813

```JAVA

package basics;

import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.ObjectInputStream;
import java.io.ObjectOutputStream;
import java.io.Serializable;

public class TransientExample implements Serializable {

	public int nonTrans = 0;

	public String nonTransStr = "nonTransStr";

	public transient int transInt = 0;

	private static void serialize() {

		TransientExample tr = new TransientExample();

		tr.nonTrans = 100;
		tr.nonTransStr = "edison";
		tr.transInt = 99;

		try {

			FileOutputStream fileOut = new FileOutputStream("D:\\testing\\transient-demo.txt");

			ObjectOutputStream out = new ObjectOutputStream(fileOut);
			out.writeObject(tr);
			out.close();
			fileOut.close();
			System.out.println("serialized data is stored in " + "D:\\testing\\transient-demo.txt");

		} catch (Exception e) {
			e.printStackTrace();
		}

	}

	private static void deserialize() {

		TransientExample objFromFile = null;

		try {

			FileInputStream fileIn = new FileInputStream("D:\\testing\\transient-demo.txt");

			ObjectInputStream in = new ObjectInputStream(fileIn);

			objFromFile = (TransientExample) in.readObject();

			in.close();
			fileIn.close();

			System.out.println("Deserialization completed :");
			System.out.println(" objFromFile.nonTransStr = " + objFromFile.nonTransStr);
			System.out.println(" objFromFile.nonTrans = " + objFromFile.nonTrans);
			System.out.println(" objFromFile.transInt = " + objFromFile.transInt);

		} catch (Exception e) {
			e.printStackTrace();
		}

	}
	
	
	public static void main(String[] args) {
		serialize();
		
		deserialize();
	}

}


OUTPUT:

serialized data is stored in D:\testing\transient-demo.txt
Deserialization completed :
 objFromFile.nonTransStr = edison
 objFromFile.nonTrans = 100
 objFromFile.transInt = 0

```


#### Synchronized
```
Synchronization is the process of controlling the accessibility of any shared resource by multiple threads.
So, the particular resource can be accessed by only one thread at a time.
This can be used for methods.
```

#### Volatile
```JS
It is used to mark the variable as being stored in main memory.
It is used modify the value of variable by different thread.
```

#### Native

## Datatype

### Primitive 
![image](https://user-images.githubusercontent.com/70185865/158251081-ad8f8ed2-158a-4a99-b8b1-e8a0495513c6.png)

#### Unicode System
`Unicode is a universal international standard character encoding`

### Non-Primitive
Classes, Interfaces, String, Array, Object

## Operators
![image](https://user-images.githubusercontent.com/70185865/158251974-9117b415-26a5-4777-aa56-ab1dbffa1f58.png)

### Operators example

https://github.com/VigneshOfficial2020/java-tutorial/commit/52d74b1c2d12e826898a37d6e0ae6102e41592b3

```JAVA
package basics;

public class OpertorsExample {

	public static void main(String args[]) {

		// Unary Operator Example: ++ and -- -->> starts

		int x1 = 10;
		int x2 = 10;
		int x3 = 10;
		int x4 = 10;

		System.out.println(" x1 = " + x1 + "  x1++ = " + x1++);// 10 (11)
		System.out.println(" x2 = " + x2 + "  ++x2 = " + (++x2));// 12
		System.out.println(" x3 = " + x3 + "  x3-- = " + x3--);// 12 (11)
		System.out.println(" x4 = " + x4 + "  --x4 = " + (--x4));// 10

		// Unary Operator Example: ++ and -- -->> ends

		// Shift Operator starts

		System.out.println(10 << 2);// 10*2^2=10*4=40 ==>> 1010 -> 0010 1000
		System.out.println(10 << 3);// 10*2^3=10*8=80 ==>> 1010 -> 0101 0000
		System.out.println(20 << 2);// 20*2^2=20*4=80
		System.out.println(15 << 4);// 15*2^4=15*16=240

		System.out.println(10 >> 2);// 1010 -> 0010 --> 2 , 10/(2^2)=10/4 = 2
		System.out.println(10 >> 3);// 1010 -> 0001 --> 1 , 10/(2^3)=10/8 = 1

		// Shift Operator ends

		// Logical and Bitwise Operator starts

		// The logical && operator doesn't check the second condition if the first
		// condition is false. It checks the second condition only if the first one is
		// true.

		// The bitwise & operator always checks both conditions whether first condition
		// is true or false.

		// The logical || operator doesn't check the second condition if the first
		// condition is true. It checks the second condition only if the first one is
		// false.

		// The bitwise | operator always checks both conditions whether first condition
		// is true or false.

		// Logical and Bitwise Operator ends

	}
}


OUTPUT:

 x1 = 10  x1++ = 10
 x2 = 10  ++x2 = 11
 x3 = 10  x3-- = 10
 x4 = 10  --x4 = 9
40
80
80
240
2
1

```

## Inheritance
```JS
Inheritance in Java is a mechanism in which one object acquires all the properties and behaviors of a parent object.
```

### Types of Inheritance

![image](https://user-images.githubusercontent.com/70185865/158423481-00057ea6-f27e-4852-93f2-e416c91ab656.png)

![image](https://user-images.githubusercontent.com/70185865/158423574-d6f6628f-e5b2-4011-8cf6-b28199323abc.png)


#### Single Inheritance Example

![image](https://user-images.githubusercontent.com/70185865/158428856-aa8af783-7fb3-4ee3-96c6-d64a52b2e75c.png)

```JS

package basics;

class ParentClass {

	void parentClassMethod() {
		System.out.println("ParentClass - parentClassMethod");
	}
}

public class SingleInheritanceExample extends ParentClass {
	
	
	void parentClassMethod1() {
		
		super.parentClassMethod();
		System.out.println("SingleInheritanceExample - parentClassMethod");
	}

	public static void main(String[] args) {

		SingleInheritanceExample si = new SingleInheritanceExample();
		
		si.parentClassMethod1();
		
		
	}

}


OUTPUT:
ParentClass - parentClassMethod
SingleInheritanceExample - parentClassMethod

```

#### Multilevel Inheritance Example

![image](https://user-images.githubusercontent.com/70185865/158428944-53e3b7cf-d76c-4bef-9d33-509d7d195586.png)

```JS
package basics;

class MLParentClass {

	void parentClassMethod() {
		System.out.println("MLParentClass - parentClassMethod");
	}
}

class MLParentClass1 extends MLParentClass {

	void parentClassMethod1() {
		super.parentClassMethod();
		System.out.println("MLParentClass1 - parentClassMethod1");
	}
}

class MLParentClass2 extends MLParentClass1 {
	
	void parentClassMethod2() {
		super.parentClassMethod1();
		System.out.println("MLParentClass2 - parentClassMethod2");
	}
}

public class MultilevelInheritanceExample{

	public static void main(String[] args) {
		
		MLParentClass2 mlp = new MLParentClass2();

		mlp.parentClassMethod2();

	}

}


OUTPUT:
MLParentClass - parentClassMethod
MLParentClass1 - parentClassMethod1
MLParentClass2 - parentClassMethod2


```

#### Hierarchial Inheritance

![image](https://user-images.githubusercontent.com/70185865/158430008-e821e58f-5b5d-438c-81dd-c7a9217a9965.png)

```JS
package basics;

class HIParentClass {

	void parentClassMethod() {
		System.out.println("HIParentClass - parentClassMethod");
	}
}

class HIParentClass1 extends HIParentClass {

	void parentClassMethod1() {
		super.parentClassMethod();
		System.out.println("HIParentClass1 - parentClassMethod1");
	}
}

class HIParentClass2 extends HIParentClass {
	
	void parentClassMethod2() {
		super.parentClassMethod();
		System.out.println("HIParentClass2 - parentClassMethod2");
	}
}

public class HierarchialInheritanceExample{

	public static void main(String[] args) {
		
		HIParentClass1 hip1 = new HIParentClass1();

		hip1.parentClassMethod1();
		
		System.out.println("-----------------------------");
		
		HIParentClass2 hip2 = new HIParentClass2();

		hip2.parentClassMethod2();

	}

}

OUTPUT:
HIParentClass - parentClassMethod
HIParentClass1 - parentClassMethod1
-----------------------------
HIParentClass - parentClassMethod
HIParentClass2 - parentClassMethod2

```

#### Multiple Inheritance Example


```JS
multiple and hybrid inheritance is supported through interface only. 

When one class inherits multiple classes, it is known as multiple inheritance.
```

##### QN-? Why multiple inheritance is not supported in java?
```JS
Consider a scenario where A, B, and C are three classes. The C class inherits A and B classes. If A and B classes have the same method and you call it from child class object, there will be ambiguity to call the method of A or B class.

So because of Ambiguity.
```

![image](https://user-images.githubusercontent.com/70185865/158431499-d5a307d4-36d9-4b66-81c0-9718bf8dcab4.png)

```JS

package basics;


interface MInterface {
	
	default void interfaceMethod() {
		System.out.println("MInterface - interfaceMethod");
	};
}

interface MInterface1 {
	
	default void interfaceMethod1() {
		System.out.println("MInterface1 - interfaceMethod1");
	};
}

// multiple inheritance achieved here
interface MInterface2 extends MInterface,MInterface1 {
	
	public default void interfaceMethod2() {
		interfaceMethod();
		interfaceMethod1();
	};
}

class MInterfaceClass  implements MInterface2{
	
	void mInterfaceClassMethod() {
		interfaceMethod2();
		System.out.println("MInterfaceClass - mInterfaceClassMethod");
	}
	
}


public class MultipleInheritanceExample{
	
	public static void main(String[] args) {
		
		MInterfaceClass ml = new MInterfaceClass();
		ml.mInterfaceClassMethod();
		System.out.println("MultipleInheritanceExample - main");
		
	}
	
}


OUTPUT :
MInterface - interfaceMethod
MInterface1 - interfaceMethod1
MInterfaceClass - mInterfaceClassMethod
MultipleInheritanceExample - main

```

#### Hybrid Inheritance

![image](https://user-images.githubusercontent.com/70185865/158437999-9874b14c-b0ef-4291-a6fd-6cedcdbb3ca3.png)


## Polymorphism
```JS
If one task is performed in different ways, it is known as polymorphism. 
In Java, we use method overloading and method overriding to achieve polymorphism.
```

### Method Overloading
```JS
By changing the no. of arguments.
By changing the data type of the arguments.
```
### Why Method overloading is not possible by changing the return type of method?
`Because of ambiguity.`
### Can we overload java main() method?
```JS
The main method can be overloaded but JVM will execute first the method with String args.
```

### Method Overriding
```JS
If a subclass has the same method as declared in the parent class is known as Method Overriding.
The overridden method must have the same name, return type, no. of args and data type of args
```
### Can we override the static method?
```JS
No, a static method cannot be overridden.
Static belongs to the class area, and an instance belongs to the heap area.
```
### Can we override java main method?
```JS
No, because the main is a static method.
```

## Abstraction
```JS
Hiding internal details and showing functionality is known as abstraction.
In Java, we use abstract class and interface to achieve abstraction.

```
### Abstract Class
```JS
Must be declared with abstract keyword.
An object can’t be created for this so it should be extended.
It can have both abstract and non-abstract methods.
The abstract method must be overridden in sub-class and non-abstract methods are not required to override.
Non-abstract methods must have a method body.
```

### Interface
```JS
It’s a blueprint of a class.
Interface fields are “public static final” by default.
Interface methods are “public abstract” by default.
We can have default methods but the method body should be written and it’s not required to override.
The final method is not allowed to define inside the interface.
```

### Difference between abstract class and interface
![image](https://user-images.githubusercontent.com/70185865/158518363-4b680319-aba5-46a0-a2c4-24ef50f0a496.png)


## STRING

[STRING](https://github.com/VigneshOfficial2020/programming-overview-interview-questions-answers/blob/main/java-and-springboot-db-qns-ans.md#explain-string-constant-pool)

![image](https://user-images.githubusercontent.com/70185865/158517984-2fe441c7-2999-4fa6-8807-1d957675828f.png)


## Exception Handling
[Exception Handling](https://github.com/VigneshOfficial2020/programming-overview-interview-questions-answers/blob/main/java-and-springboot-db-qns-ans.md#exceptions)

## Multithreads
```JS

Thread is a lightweight sub-process.
They are independent and if there are any exceptions that occur in one thread, it doesn’t affect other threads.
```
### By extends with Thread Class
```JAVA
package basics;

public class MultithreadExample extends Thread {

	@Override
	public void run() {
		super.run();
		System.out.println("Thread run method");
	}

	public static void main(String[] args) {

		MultithreadExample t = new MultithreadExample();
		t.start();
	}

}
```
### By implements with Runnable Interface
```JAVA
package basics.multithread;

public class MultithreadExample1 implements Runnable {

	@Override
	public void run() {
		System.out.println("Runnable run method");
	}

	public static void main(String[] args) {

		MultithreadExample1 t1 = new MultithreadExample1();
		Thread th = new Thread(t1);
		th.start();
	}

}

```
### Difference between Thread and Runnable in Java
| Thread | Runnable |
| --- | --- |
| Each thread has to create unique objects | Multiple threads can share same object |
| Needs more memory | Needs less memory |
| Java not supporting for Multiple inheritance of Class. So, a class can't be extended any more if a class extends with thread class | If a class is implementing the runnable interface then your class can extend another class. |
| [Thread Example](https://github.com/VigneshbabuOfficial/java-tutorial/blob/master/src/basics/multithread/MultithreadExample.java) | [Runnable Interface Example](https://github.com/VigneshbabuOfficial/java-tutorial/blob/master/src/basics/multithread/MultithreadExample1.java) |

### Life Cycle
#### [ New ](#new)
#### [ Running / Runnable ](#running--runnable)
#### [ Blocked / Waiting ](#blocked--waiting)
#### [ Timed Waiting ](#timed-waiting)
#### [ Terminated ](#terminated)

#### New
```JS
Whenever a new thread is created, it is always in the new state.
``` 
#### Running / Runnable
```JS
A thread, that is ready to run is then moved to the runnable state. In the runnable state, the thread may be running or may be ready to run at any given instant of time. 
```
#### Blocked / Waiting
```JS
Whenever a thread is inactive for a span of time (not permanently) then, either the thread is in the blocked state or is in the waiting state.
```
#### Timed Waiting
```JS
Sometimes, waiting for leads to starvation. For example, a thread (its name is A) has entered the critical section of a code and is not willing to leave that critical section. In such a scenario, another thread (its name is B) has to wait forever, which leads to starvation. To avoid such scenario, a timed waiting state is given to thread B. Thus, thread lies in the waiting state for a specific span of time, and not forever. A real example of timed waiting is when we invoke the sleep() method on a specific thread. The sleep() method puts the thread in the timed wait state. After the time runs out, the thread wakes up and start its execution from when it has left earlier.
```
#### Terminated
```JS
A thread reaches the termination state because of the following reasons:

When a thread has finished its job, then it exists or terminates normally.
Abnormal termination: It occurs when some unusual events such as an unhandled exception or segmentation fault.
```
### Thread Methods
![image](https://user-images.githubusercontent.com/70185865/160745674-f919b316-bede-4cb0-9c48-5a2d3584f669.png)
![image](https://user-images.githubusercontent.com/70185865/160745733-964e2796-ef3b-47db-b422-72bb9889e7d6.png)
![image](https://user-images.githubusercontent.com/70185865/160745794-f993d8d2-d0db-4846-8d67-aa3c2ba60438.png)

### Java Thread Pool
<details>
<summary>:bulb:</summary>

```JS
A group of fixed-size threads is created. A thread from the thread pool is pulled out and assigned a job by the service provider. After completion of the job, the thread is contained in the thread pool again.
	
```
</details>

### Synchronization in Java
<details>
<summary>:bulb:</summary>	

```JS
Synchronization in Java is the capability to control the access of multiple threads to any shared resource.
Java Synchronization is better option where we want to allow only one thread to access the shared resource.
```
</details>

### Thread Interview Qns
[multithread qns](https://github.com/VigneshbabuOfficial/programming-overview-interview-questions-answers/blob/main/java-and-springboot-db-qns-ans.md#multithread-qns)

### Thread reference
https://github.com/VigneshbabuOfficial/java-tutorial/commit/8db110840a2df90312a57be6a0ab54fe45e56c82
https://github.com/VigneshbabuOfficial/java-tutorial/commit/4c838565b6e7a25dce5c4c193fca0bcfaae89fb5


## Java Collection
```JS
The Collection is a framework that provides an architecture to store and manipulate the group of objects.
```
![image](https://user-images.githubusercontent.com/70185865/161088751-4866eac1-73ae-442b-99e9-2bf6c59c4d66.png)

### List Interface
#### [ArrayList](https://github.com/VigneshbabuOfficial/programming-overview-interview-questions-answers/blob/main/java-and-springboot-db-qns-ans.md#arraylist)
#### [LinkedList](https://github.com/VigneshbabuOfficial/programming-overview-interview-questions-answers/blob/main/java-and-springboot-db-qns-ans.md#linkedlist)
#### [ArrayList Vs LinkedList](https://github.com/VigneshbabuOfficial/programming-overview-interview-questions-answers/blob/main/java-and-springboot-db-qns-ans.md#arraylist-vs-linkedlist)
#### Vector
<details>
<summary>:bulb:</summary>
	
```JS
Vector uses a dynamic array to store the data elements.  
It is similar to ArrayList. However, It is synchronized.	
```
</details>

#### Stack
<details>
<summary>:bulb:</summary>
	
```JS
The stack is the subclass of Vector. It implements the last-in-first-out data structure, i.e., Stack. The stack contains all of the methods of Vector class and also provides its methods like boolean push(), boolean peek(), boolean push(object o), which defines its properties.	
```
</details>

### Queue Interface
```JS
The queue interface maintains the first-in-first-out order. It can be defined as an ordered list.
```
#### Priority Queue Class
<details>
<summary>:bulb:</summary>
	
```JS
The PriorityQueue class implements the Queue interface. PriorityQueue doesn't allow null values to be stored in the queue.	
```
</details>

#### Deque Interface
<details>
<summary>:bulb:</summary>
	
```JS
Deque interface extends the Queue interface. Deque stands for a double-ended queue which enables us to perform the operations at both ends.	
```
</details>

#### Array Deque Class
<details>
<summary>:bulb:</summary>
	
```JS
ArrayDeque class implements the Deque interface. ArrayDeque is faster than ArrayList and Stack and has no capacity restrictions.	
```
</details>

### Set Interface
#### HashSet
<details>
<summary>:bulb:</summary>
	
```JS
Java HashSet class is used to create a collection that uses a hash table for storage.
HashSet stores the elements by using a mechanism called hashing.
HashSet contains unique elements only.
HashSet allows null value.
HashSet class is non-synchronized.
HashSet doesn't maintain the insertion order. Here, elements are inserted on the basis of their hashcode.
HashSet is the best approach for search operations.
The initial default capacity of HashSet is 16, and the load factor is 0.75.
```
</details>

#### HashSet
<details>
<summary>:bulb:</summary>
	
```JS
Java HashSet class is used to create a collection that uses a hash table for storage.
HashSet stores the elements by using a mechanism called hashing.
HashSet contains unique elements only.
HashSet allows null value.
HashSet class is non-synchronized.
HashSet doesn't maintain the insertion order. Here, elements are inserted on the basis of their hashcode.
HashSet is the best approach for search operations.
The initial default capacity of HashSet is 16, and the load factor is 0.75.
```
</details>

##### Internal working of Set/HashSet 
![image](https://user-images.githubusercontent.com/70185865/161666372-7b720e5e-9c4d-4438-bedd-5df0717ea148.png)

#### LinkedHashSet
<details>
<summary>:bulb:</summary>
	
```JS
Stores unique elements.
Maintains insertion order.
Non-Synchronized.
```
</details>

#### SortedSet Interface
<details>
<summary>:bulb:</summary>
	
```JS
SortedSet is the alternate of Set interface that provides a total ordering on its elements. 
The elements of the SortedSet are arranged in the increasing (ascending) order
```
</details>

#### TreeSet
<details>
<summary>:bulb:</summary>
	
```JS
TreeSet class contains unique elements only like HashSet.
TreeSet class access and retrieval times are quiet fast.
TreeSet class doesn't allow null element.
TreeSet class is non synchronized.
TreeSet class maintains ascending order.
```
</details>

### Map Interface
<details>
<summary>:bulb:</summary>
	
```JS
Map stores elements in the form of key and value pairs.
A Map is useful if you have to search, update or delete elements on the basis of a key.
```
</details>

![image](https://user-images.githubusercontent.com/70185865/161807487-8913b02c-2088-485e-8704-e98b3f387b87.png)

#### HashMap
<details>
<summary>:bulb:</summary>
	
```JS
Java HashMap contains values based on the key.
Java HashMap contains only unique keys.
Java HashMap may have one null key and multiple null values.
Java HashMap is non-synchronized.
Java HashMap maintains no order.
The initial default capacity of the Java HashMap class is 16 with a load factor of 0.75.
```
</details>

#### Load Factor
<details>
<summary>:bulb:</summary>
	
```JS
The Load factor is a measure that decides when to increase the HashMap capacity to maintain the get() and put() operation complexity of O(1). 
The default load factor of HashMap is 0.75f (75% of the map size).
```
</details>

#### Hashing
<details>
<summary>:bulb:</summary>
	
```JS
It is the process of converting an object into an integer value. The integer value helps in indexing and faster searches.
```
</details>

#### Working of HashMAp
[working-of-hashmap-in-java](https://www.javatpoint.com/working-of-hashmap-in-java)
[internal-working-of-hashmap-java](https://www.geeksforgeeks.org/internal-working-of-hashmap-java/)

#### Concurrent HashMap
[concurrenthashmap](https://medium.com/javarevisited/comparing-hashmap-and-concurrenthashmap-in-java-e131769c2eec)
[concurrency-exception](https://github.com/VigneshbabuOfficial/programming-overview-interview-questions-answers/blob/main/java-and-springboot-db-qns-ans.md#concurrency-exception)

#### LinkedHashMap 
<details>
<summary>:bulb:</summary>
	
```JS
Java LinkedHashMap maintains insertion order.
Java LinkedHashMap is non-synchronized.
Java LinkedHashMap contains unique elements.
```
</details>

#### TreeMap
<details>
<summary>:bulb:</summary>
	
```JS
Java TreeMap contains only unique elements.
Java TreeMap cannot have a null key but can have multiple null values.
Java TreeMap is non-synchronized.
Java TreeMap maintains ascending order.
```
</details>

#### Comparable Interface
<details>
<summary>:bulb:</summary>
	
```JS
Java Comparable interface is used to order the objects of the user-defined class. 
This interface is found in java.lang package and contains only one method named compareTo(Object).
It provides a single sorting sequence only, i.e., you can sort the elements on the basis of single data member only. 
For example, it may be rollno, name, age or anything else. 

compareTo(Object obj) method

public int compareTo(Object obj): It is used to compare the current object with the specified object. It returns

    positive integer, if the current object is greater than the specified object.
    negative integer, if the current object is less than the specified object.
    zero, if the current object is equal to the specified object.

We can sort the elements of:

    String objects
    Wrapper class objects
    User-defined class objects
```
</details>


```JS
Comparable interface Exampple

```
<details>
<summary>:interrobang:</summary>
	
```JS
Note: String class and Wrapper classes implement the Comparable interface by default. So if you store the objects of string or wrapper classes in a list, set or map, it will be Comparable by default.
```
</details>

#### Comparator interface

<details>
<summary>:bulb:</summary>
	
```JS
Java Comparator interface is used to order the objects of a user-defined class and provides multiple sorting sequences, 
i.e., you can sort the elements on the basis of any data member, for example, rollno, name, age or anything else.

public int compare(Object obj1, Object obj2)

```
</details>


```JS
Comparator interface Exampple

```


## JAVA 8 FEATURES
[java-8-features](https://github.com/VigneshOfficial2020/programming-overview-interview-questions-answers/blob/main/java-and-springboot-db-qns-ans.md#java-8-features)

## JAVA 11 FEATURES
[java-11-features](https://github.com/VigneshOfficial2020/programming-overview-interview-questions-answers/blob/main/java-and-springboot-db-qns-ans.md#java-11-features)

## JAVA 16 FEATURES
[java-16-features](https://github.com/VigneshOfficial2020/programming-overview-interview-questions-answers/blob/main/java-and-springboot-db-qns-ans.md#java-16-features)

## Java programs for Practice
https://www.javatpoint.com/java-programs


## Java Interview Questions
[java-interview-questions--answers](https://github.com/VigneshOfficial2020/programming-overview-interview-questions-answers/blob/main/java-and-springboot-db-qns-ans.md#java-interview-questions--answers)

