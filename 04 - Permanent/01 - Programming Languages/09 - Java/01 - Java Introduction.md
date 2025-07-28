---
date: 2025-07-27T21:42
tags: []
---

--> Released in 1995
--> Platform Independent

Before Java

<center>C/C++ Program
</center>
<center>↓</center>
<center>-----------------------------</center>

<div style="display: flex; justify-content: space-between;">
  <span style="margin-left: 300px;">↓</span>
  <span style="margin-right: 300px;">↓</span>
</div>
<div style="display: flex; justify-content: space-between;">
  <span style="margin-left: 250px;">Platform 1</span>
  <span style="margin-right: 250px;">Platform 2</span>
</div>

In java 
<u>Java Program</u>
           ↓
           Java Complier
           ↓
    Java ByteCode  <-- Platform Independent
    |          |
    ↓          ↳ <u>JVM Platform 2</u>
<u>JVM Platform 1</u>

JVM : Java Virtual Machine
-> Security in Java
-> Java -> Bytecode --> JVM {Secure data} 
-> have automatic garbage collector and multi-threading 

```java

public class Text{
    /*Multi-line 
    code
    comment
    */
    public static void main(String []args){
        System.out.println("Hello Nothing");
    }
}
```


--> Running Code
$ javac Text.java
$ Java Test