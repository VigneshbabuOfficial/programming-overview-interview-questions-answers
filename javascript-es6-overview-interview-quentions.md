
# OVERVIEW
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
## String
## Class
## Object
## Exception Handling

# ES6
## var vs let vs const
## DEFAULT PARAMETERS
```JS
function say(message='Hi') {
    console.log(message);
}

say(); // 'Hi'
say(undefined); // 'Hi'
say('Hello'); // 'Hello'
```
## REST PARAMETERS
```JS
ES6 provides new kind of parameter so-called Rest Parameter that has a prefix of 3 dots   ( . . . )

function fnc(a,b,...args) {
  console.log(args)
}
fnc(1,2,3,'A','B','C'); // [3, "A", "B", "C"]
fnc(1,2); // [ ]
```
## SPREAD OPERATOR
```JS
ES6 provides new operator called spread allows to concatenate values

const oddArr = [1,2,3]
const comArr = [ ...oddArr,2,4,6]
console.log(comArr)  //  [1, 2, 3, 2, 4, 6]

```
## Objects Literal
```JS
var sharedType = {
'all': '[none,allUsers,specificGroupOfUsers]',
'none': 'none'
}
sharedType["all"]  // [none,allUsers,specificGroupOfUsers]

```
## DESTRUCTURING
```JS
OBJECT 
------

function getPerson() {
    return null;
}
let {
    firstName,
    lastName
} = getPerson();
console.log(firstName, lastName);
TypeError: Cannot destructure property 'firstName' of 'getPerson(...)' as it is null.
let {
    firstName,
    lastName
} = getPerson() || {};

firstName // undefined
lastName // undefined

==============================================================

const ratings = [
    {user: 'John',score: 3},
    {user: 'Jane',score: 4},
    {user: 'David',score: 5},
    {user: 'Peter',score: 2},
];

let sum = 0;
for (const {score} of ratings) {
    sum += score;
}

console.log(`Total scores: ${sum}`); // 14

--------------------------------------------------------------------------------------------

ARRAY DESTRUCTURING
-------------------

function getItems() {
    return null;
}
let [a = 10, b = 20] = getItems() || [];
console.log(a); // 10
console.log(b); // 20

```
## map function
```JS
const colors = ['red', 'green', 'blue'];
const items = colors.map(function(color){
  return '<li>'+color+'</li>';
});
console.log(items);

O/P:
(3) ["<li>red</li>", "<li>green</li>", "<li>blue</li>"]
0: "<li>red</li>"
1: "<li>green</li>"
2: "<li>blue</li>"
```

## Classes
```JS
class Person {
  constructor(name){
    this.name = name
  }
  walk() {
    console.log(this.name+' is walking');
  }
}

const person = new Person('Vignesh');
const walkFn = person.walk();
console.log(walkFn);

O/P:
VM113:6 Vignesh is walking

```
## Class Inheritance
```JS
class Person {
  constructor(name){
    this.name = name
  }
  walk() {
    console.log(this.name+' is walking !!');
  }
}

class Teacher extends Person{
  constructor(name, degree){
    super(name);
    this.degree = degree;
  }
  teach(){
    console.log(this.name+' is teaching degree '+this.degree);
  }
}

const teacher = new Teacher('Vignesh', 'B.Tech');
console.log(teacher.name);
console.log(teacher.degree);
console.log(teacher.teach());
console.log(teacher.walk());


O/P:
Vignesh
B.Tech
Vignesh is teaching degree B.Tech
Vignesh is walking !!

```
## Modules
```JS

person.js
---------
export class Person {
    constructor(name){
      this.name = name
    }
    walk() {
      console.log(this.name+' is walking !!');
    }
  }
=============================================  
  
teacher.js
-----------
import {Person} from './person';

export class Teacher extends Person{
    constructor(name, degree){
      super(name);
      this.degree = degree;
    }
    teach(){
      console.log(this.name+' is teaching degree '+this.degree);
    }
  }
================================================

index.js
--------

import {Teacher} from './teacher';

const teacher = new Teacher('Vignesh', 'Apple');
console.log(teacher.name);
console.log(teacher.degree);
console.log(teacher.teach());
console.log(teacher.walk());

O/P:
Vignesh
B.Tech
Vignesh is teaching degree B.Tech
Vignesh is walking !!

```
## Named and Default Exports
```JS
Default -> import ... from '';
Named -> import {...} from '';
```
## Arrow function
## Map + Set + WeakMap + WeakSet
```JS
A WeakMap accepts only objects as keys whereas a Map,in addition to objects, accepts primitive datatype such as strings, numbers etc.
```
## TEMPLATE LITERALS/STRINGS:

```JS

Template literals also provides concatenation additionally text with some format.

var a = 123, str = `---
   a is: ${a}
---`;
console.log(str);

O/P:
---
   a is: 123
---

```
## Promises
```JS
let myPromise = new Promise((resolve,reject) => {

let theDecider = true

if(theDecider){ resolve('success') }
else { reject('error') }


}
)


myPromise.then(res => {

console.log('res = ',res)
})
.catch(err => {
console.log('error = ',err)

})
.finally(() => {
    console.log('Experiment completed');
  })


O/P:
res =  success
Experiment completed

```



# Interview Questions

## What's the difference between event.stopPropagation and event.preventDefault?
```JS
stopPropagation prevents further propagation of the current event in the capturing and bubbling phases.

preventDefault prevents the default action the browser makes on that event.
```
## What is the use of Void (0)?
```JS
Void(0) is used to prevent the page from refreshing, and parameter “zero” is passed while calling.

Void(0) is used to call another method without refreshing the page.
```
https://www.youtube.com/watch?v=iccdL8-SF7c

## What is the difference between call() and apply() and bind() methods ?

### call method 
```JS
let printFullName = function() {
    console.log(this.firstName+" "+this.lastName)
}

let name = {
    firstName: "Vicky",
    lastName: "Steve"
}

printFullName.call(name);

O/P:
Vicky Steve

---------------------------------------------------------------------

let printFullNameWithStateAndCountry = function(state,country) {
    console.log(this.firstName+" "+this.lastName+" from "+state+" "+country)
}

let name = {
    firstName: "Vicky",
    lastName: "Steve"
}

printFullNameWithStateAndCountry.call(name,'Cupertino', "California");

O/P :
Vicky Steve from Cupertino California
```
### apply method
```JS
let printFullName = function() {
    console.log(this.firstName+" "+this.lastName)
}

let name = {
    firstName: "Vicky",
    lastName: "Steve"
}

printFullName.apply(name);

O/P:
Vicky Steve

----------------------------------------------------------------------

let printFullNameWithStateAndCountry = function(state,country) {
    console.log(this.firstName+" "+this.lastName+" from "+state+" "+country)
}

let name = {
    firstName: "Vicky",
    lastName: "Steve"
}

printFullNameWithStateAndCountry.apply(name,['Cupertino', "California"]);

O/P:
Vicky Steve from Cupertino California
```
### bind method 
```JS
it's just similar to call method but it'll return a copy of function description not action done by that function. So, by storing into another variable a nd call it as function will return the outout of the invoked function.


let printFullNameWithStateAndCountry = function(state,country) {
    console.log(this.firstName+" "+this.lastName+" from "+state+" "+country)
}

let name = {
    firstName: "Vicky",
    lastName: "Steve"
}

let printThis = printFullNameWithStateAndCountry.bind(name,'Cupertino', "California");
printThis()

O/P :
Vicky Steve from Cupertino California
```

## What is the difference between innerHTML & innerText ?
```JS
innerText returns all text contained by an element and all its child elements. innerHtml returns all text, including html tags, that is contained by an element.
```

## What is an event bubbling in JavaScript ?
```JS
Event bubbling is a method of event propagation in the HTML. When an event is triggered in an element inside another element, and both elements have registered a handle to that event. In event bubbling, the event is first captured and handled by the innermost element and then propagated to outer elements.
```









