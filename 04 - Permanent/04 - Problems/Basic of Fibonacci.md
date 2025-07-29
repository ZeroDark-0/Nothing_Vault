---
date: 2025-07-29T16:00
tags: []
---

Series :- 0 1 1 2 3 5 8 13 21 .....

The sum of last two digits. and have the default number 0 and 1.

Two ways to do this is my Loop or Recursion

-> By Looping 

```cpp
for(int i = 0; i<n; i++){

    std :: cout << a << std::endl;
    temp = a;
    a = b;
    b = temp + b;
}
```

Here temp = 0, a= 0, b = 1. now , n is the positive position of a Fibonacci element..

-> By Recursion

![[1-Basic of Fibonacci (dp).png]]



The above eqn come from 
 fib(5) =fib(n-1) + fib(n-2)
and this is overlapping property..

The reason we use dynamic programming is to decrease like we did above from O(2^n)
but this only work for small inputs

```cpp
long fibo(int x){ // x is  input
    if(x==0) { return 0;} //condition
    if(x==1) { return 1;} //condition
    return fibo(x-1) + fibo(x-2);
}
```

