
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
[static](https://github.com/VigneshOfficial2020/programming-overview-interview-questions-answers/edit/main/java-overview.md#static)

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


	
