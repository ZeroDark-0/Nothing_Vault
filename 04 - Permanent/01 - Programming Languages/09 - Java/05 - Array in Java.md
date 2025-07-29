---
date: 2025-07-29T15:27
tags: []
---

```java
int arr[] = {10, 20, 30, 40, 50};
a.length;
```

--> Different ways to create Array

1. ``` int []arr; //stack
   a = new int[3];```
2. ```int []arr = new int[3];```
3. by using Loop

```java
int []arr = new  int[4];
int arr[] = new int [4];
both are same
```

-> all element should be same
->uninitialized array element have 0
-> Primitive are stored at contiguous location
->Non-Primitive Reference are stored at contiguous location

### Array Type

Dimension
    |
    |-> 1D
    |-> 2D
Size
|
|->Fixed size(normal array)
|-> Dynamic size (ArrayList, Vector)

### ->Multi-Dimentional Array

    `int arr[][] = [[ ],[ ]];`

```java
for(int i = 0; i<arr.length; i++){
    for(int  j = 0; i<arr[i].length; j++){
        arr[i][j] = 10;
        System.out.print(arr[i][j] + " ");
    }
    System.out.println();
}
```
