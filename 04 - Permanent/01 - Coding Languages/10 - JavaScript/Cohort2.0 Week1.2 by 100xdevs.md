---
date: 2025-08-20T01:32
tags: []
---

### What is Complier?

Complier convert high level developer friendly code into 0s and 1s.


| Complied Languages                                     | Interpreted Languages                      |
| ------------------------------------------------------ | ------------------------------------------ |
| First need to compile, then need to run                | Usually go line by line                    |
| Usually don't compile if there is an error in the code | Can run partially if the error comes later |
| Example-C++, Java, Rust, Golang                        | Example - JavaScript, Pythyon              |

The basic code for JavaScript
```js
console.log("hello world")
console.log(a) //error
```

The above code will able to run partially

![[1-Cohort2.0 Week1.2 by 100xdevs.png]]

## Resource:- 

![[1-Cohort2.0 Week1.2 by 100xdevs.pdf]]


### Basic Syntax of the JavaScript

```js
let firstname = "alex"
let age = 18;
let isMarried = false;

console.log("this person name is " + firstname + " and their age is " + age)
```

```js 

let answer = 0;
for(let i = 0;i<10;i = i+1){
    answer = answer + i;
}
console.log(answer);
```

```js
const personArray = ["alex","rina","micheal"];          //these are the array
const generArray = ["male","female","male"];


const user1 = {                      
    firstName : "ellen",
    gender : "female"
}
console.log(user1["gender"]);

const alluser = [{                          //these are the objects
    firstName : "ellen",
    gender : "female"
}, {
    firstName : "jane",
    gender : "female"
},{
    firstName : "pan",
    gender : "male"
},{
    firstName : "wise",
    gender : "male"
}]
```

### Functions

```js

function sum(a,b){
    //do things
    return a+b;
}

console.log(sum(1,2));
```

