---
date: 2025-10-13T21:42
tags: []
---


### Split Function

Break a string into parts
Dividing the string into multiple smaller strings, based on the space or symbols 

##### <code style="color:cyan">python</code> 
```python
s = "10 20 30"
nums = s.split()       # ['10', '20', '30']
```

##### <code style="color:blue">C++</code> 
```cpp
// C++

#include <bits/stdc++.h>
using namespace std;

int main(){
    string = "10 20 30";
    istringstream iss(s); // create input stream from string 
    
    vector<string>parts;
    string word;
    
    while(iss >> word)  //extract words by space
        part.push_back(word);
        
    for (string p : parts) cout << p << '\n';
}```

If you want to split by a **custom delimiter** (like a comma `,`)

```cpp
string s = "apple,banana,cherry";
stringstream ss(s);
string item;
vector<string> fruits;

while (getline(ss, item, ','))   // split by comma
    fruits.push_back(item);
```



### Map 

Apply a function to each element
##### <code style="color:cyan">python</code> 
```python
nums = [1, 2, 3]
squares = list(map(lambda x: x*x, nums))
# [1, 4, 9]
```

##### <code style="color:blue">C++</code> 
there are two ways loop or `std:transform`
//with loop
```cpp 
//C++

vector<int> nums = {1, 2, 3};
vector<int> squares;

for (int x : nums)
    squares.push_back(x * x);

```

//with `std::transform`
```cpp
//C++

vector<int> nums = {1, 2, 3};
vector<int> squares(nums.size());

transform(nums.begin(), nums.end(), squares.begin(),
          [](int x) { return x * x; }); //lambda function

for (int s : squares) cout << s << ' ';
```



### Filter

Keep only items that meet a condition

removal of element which do not satisfy the condition

##### <code style="color:cyan">python</code> 
```python
nums = [1, 2, 3, 4, 5]
evens = list(filter(lambda x: x % 2 == 0, nums))
# [2, 4]
```


##### <code style="color:blue">C++</code> 
using with loop:
```cpp

vector<int> nums = {1, 2, 3, 4, 5};
vector<int> evens;

for (int x : nums)
    if (x % 2 == 0)
        evens.push_back(x);
```

Using with `copy_if` (from `<algorithm>`):
```cpp
vector<int> nums = {1, 2, 3, 4, 5};
vector<int> evens;

copy_if(nums.begin(), nums.end(), back_inserter(evens),
        [](int x) { return x % 2 == 0; });

for (int e : evens) cout << e << ' ';
```


---

