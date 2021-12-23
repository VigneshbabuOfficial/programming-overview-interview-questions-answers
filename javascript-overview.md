## Variables
| var | let | const |
| --- | --- | --- |
| global scope | block scope | block scope |
| re-assign and redeclare is acceptable | re-assign and redeclare is not acceptable | re-assign and redeclare is not acceptable |
| value initialization is not compulsory | value initialization is not compulsory | value initialization is compulsory |

## Datatypes

1. Primitive data type
    ```
    String, Number, Boolean, Undefined and Null
    ```

2. Non-primitive (reference) data type
    ```
    Object, Array and RegExp
    ```
    ```
    Arrays :  const cars = ["Saab", "Volvo", "BMW"];
    Objects : const person = {firstName:"John", lastName:"Doe", age:50, eyeColor:"blue"};
    typeof "John"         // Returns "string"
    typeof (3)            // Returns "number"
    ```

## Operators
```JS
JavaScript Arithmetic Operators
```
![image](https://user-images.githubusercontent.com/70185865/147258890-7416e63e-c47e-4c00-98ae-55dc386d04db.png)

```JS
JavaScript Comparison Operators
```
![image](https://user-images.githubusercontent.com/70185865/147259145-55c99bc3-eadf-4795-9acc-83e949817ae9.png)

```JS
JavaScript Bitwise Operators & JavaScript Logical Operators
```
![image](https://user-images.githubusercontent.com/70185865/147259388-ab7bfeb4-10e0-4cb5-acee-08c1b5af0bee.png)

```JS
JavaScript Special Operators
```
![image](https://user-images.githubusercontent.com/70185865/147259489-c576a3bc-adc1-441c-a22e-891d5b0cb5c2.png)

## JavaScript Loops
```JS
for loop
while loop
do-while loop
for-in loop
for-of loop
```
```JS
If counters/indexes are needed while accessing an array or indexes related logical stuff are there it is better to go ahead with for loop.
If there is a need to access properties/keys regardless of the order for-in will help.
If you just need to iterate through data items of an iterable(also if you need to apply some changes maybe) for-of is an obvious choice.
```

## JavaScript break and continue with label
```JS
let i, j;

loop1:
for (i = 0; i < 3; i++) {      //The first for statement is labeled "loop1"
   loop2:
   for (j = 0; j < 3; j++) {   //The second for statement is labeled "loop2"
      if (i === 1 && j === 1) {
         continue loop1;
      }
      console.log('i = ' + i + ', j = ' + j);
   }
}


OUTPUT:
i = 0, j = 0
i = 0, j = 1
i = 0, j = 2
i = 1, j = 0
i = 2, j = 0
i = 2, j = 1
i = 2, j = 2
```

```JS
let i, j;

loop1:
for (i = 0; i < 3; i++) {      //The first for statement is labeled "loop1"
   loop2:
   for (j = 0; j < 3; j++) {   //The second for statement is labeled "loop2"
      if (i === 1 && j === 1) {
         break loop1;
      }
      console.log('i = ' + i + ', j = ' + j);
   }
}

OUTPUT:
i = 0, j = 0
i = 0, j = 1
i = 0, j = 2
i = 1, j = 0
```

## Object
## Array














