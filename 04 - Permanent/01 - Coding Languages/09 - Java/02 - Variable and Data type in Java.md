---
date: 2025-07-28T02:22
tags: []
---

```java

int age = 37;
String name = "Nothing";
float weight = 70.5;
```

=> preferred to use upper-case for constant

### -> Data Type

-> Boolean
-> byte (-128 to 127)
        (-2^7  to  2^7 -1)
-> Short (-13768 to 32767)
         (OR -2^15 to 2^15 - 1)
-> int (-1247483648 to 2147483647)
       (-2^31 to 2^31)
-> long (-2^63 to 2^63 - 1)
-> float => single Precision 32 bits
-> double => Double Precision 32 bits
->char => 16 bit unicode ('140000' to  '14ffff' / 0 to 2^16 - 1)

### -> Non - Primitive

```java

Class Point{
    int x, y;
}
Class Text {
    public static void main(String []args){
        Point p = new Point();
        p.x = 10;
        p.y = 20;
        System.out.println(p.x + p.y);
    }
}

```

## -> Primitive and Non-Primitive

1. Non-primitive type variable are always reference
2. Memory for non-primitive is always allocated on Heap.
3. Memory of non-primitive get default value (like int variable get 0, boolean get false, etc.)

<u>Example</u>

```java

Class Text{
    public static void main(String[]args){
        int x1 = 10, x2 = x1;
        x2=20;
        System.out.println(x1);
        System.out.println(x2);
    }
}

```

<u>Note</u>

if we initialize
    `int x;` default will be 0


Java use reference that make Java more secure

#### -> Wrapper

| Primitive | Non-primitive |
| --------- | ------------- |
| Char      | Character     |
| byte      | Byte          |
| Short     | Short         |
| int       | Integer       |
| long      | Long          |
| float     | Float         |
| double    | Double        |
| boolean   | Boolean       |

Difference (`int x = 10; / Integer x2 = new Integer(10);`

Primitive are simple and  building block of code. Meanwhile non-primitive are derived from primitive type and ca be broken in part.

-> Auto Boxing and Unboxing 
```java
Class Text{
    public static vois main(String[]args){
        int x1 = 10;
        Integer x2 = x1; //auto boxing
        int x3 = x2;
    }
}
```

->type conversion
    ->Widening or Implicit Conversion
    |   Byte -> short -> int/char -> long -> float -> double
    |
    |
    ↳ this is fine but for
    -> Narrowing or Explicit Conversion
            `double d = 65.4;`
            `int i = (int)d;`


## ->Operator

Parenthesis
     ↓
postfix operator (++, --)
     ↓
Unary Operator (+, -, !, ~)
     ↓
Multiplicative (`*`, /, %)
     ↓
addition (+,-)
     ↓
shift operator (<<,>>,>>>)
     ↓
Relational Operator (double equals to,!=,>,<,<=,>=)
     ↓
Logical operator (&&, ||)
     ↓
Assignment operator (=,+=,-=,`*=`,/=,%=,<<=,>>=,&=,^=,|=)


## Bitwise Operator

(x&y)  or (x|y)

Process through Binary

->Right shift (shift by one)
->Unsigned right shift (Changed to positive)

