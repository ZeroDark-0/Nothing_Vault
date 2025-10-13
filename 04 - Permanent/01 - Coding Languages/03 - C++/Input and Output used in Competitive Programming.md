---
date: 2025-10-13T02:52
tags: []
---


### Basic I/O Setup

Always take fast input when it come to competitive programming 

```cpp
ios::sync_with_stdio(false);
cin.tie(nullptr);
``` 

##### Reason: This disable C and C++ Stream synchronization and untie `cin` and `cout`

### Basic Input Types

Float/Double 

```cpp
double x;
cin >> x;
cout << fixed << setpreecision(6) << x;
```

where the meaning of `fixed` is **displaying the number in fixed-point notation** (normal decimal format, not scientific).

### Input Until EOF

Used when number of test cases is unknown

```cpp
int x;
while(cin >> x){
    
    
}
```


### Fast Output

If you need to print large outputs quickly:

```cpp
for (int x : arr)     
cout << x << ' ';  // space separated 
cout << '\n';
```

Or faster with:

```cpp
ostringstream out; 
for (int x : arr) out << x << ' '; 
cout << out.str();
```

`ostringstream` comes from the header `<sstream>`
It works like `cout`, but instead of writing to the screen, it writes into an internal string buffer.
### Super-Fast I/O

Using `scanf`/`printf` 
```cpp
int a, b;
scanf("%d %d", &a, &b);
printf("%d\n", a + b);
```

Using `getchar_unlocked()` and `putchar_unlocked()` (Ultra-fast)

```cpp
inline int fastRead() {
    int x = 0, c = getchar_unlocked();
    while (c < '0' || c > '9') c = getchar_unlocked();
    while (c >= '0' && c <= '9') {
        x = x * 10 + c - '0';
        c = getchar_unlocked();
    }
    return x;
}
```


---
![[1-01 Map.gif]]

