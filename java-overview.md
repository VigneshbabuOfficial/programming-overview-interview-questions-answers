
## What is Java?
```JS
Java is a programming language and a platform. Java is a high-level, robust, object-oriented, and secure programming language.
```
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

## STRING

[STRING](https://github.com/VigneshOfficial2020/programming-overview-interview-questions-answers/blob/main/java-and-springboot-db-qns-ans.md#explain-string-constant-pool)

![image](https://user-images.githubusercontent.com/70185865/158517984-2fe441c7-2999-4fa6-8807-1d957675828f.png)
