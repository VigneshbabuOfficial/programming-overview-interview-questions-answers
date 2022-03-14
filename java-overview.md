
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
