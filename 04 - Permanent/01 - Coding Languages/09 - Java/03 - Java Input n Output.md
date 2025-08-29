---
date: 2025-07-28T22:18
tags: []
---

#### ->Input have two type

1. Buffered Reader (Character or sequence)
2. Scanner (Formatted input) (int , float, etc)

```java

import java.until.*;

class Test {
    public static void main(String args[])
        throws IO Exception{
            Buffered Reader br = new Buffered Reader(new Input Stream(System.Integer);
            int x = Integer.parseInt(br.readLine());
        }
    }
}

```

```java 
import java.util.*;

class Test {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String s = sc.nextLine(); 
        int x = sc.nextInt();
        sc.close(); 
    }
}
```


| Buffer Reader  | Scanner            |
| -------------- | ------------------ |
| big Data type  | Small Data type    |
| Can manupilate | can not manupilate |
| faster         | slower             |

#### --> Output
        |
        |-> `System.out.print();` // Primitve
        |-> `System.out.println();` //Primitive
        |-> `System.out.format() or System.out.printf()`

 
### --> Precision

```java
System.out.format("%d",x); //default
System.out.print("%0.2f",x); //3.14
System.out.print("%5.2f",x); //-3.14
System.out.print("%05.2f",x); //03.14
```

