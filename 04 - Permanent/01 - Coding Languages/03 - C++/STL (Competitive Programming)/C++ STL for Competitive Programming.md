---
date: 2025-10-18T02:32
tags: []
---

This is a internal implemented library in the C++..

there are four part in this:-

### 1. Container 

These are the data structure that are pre-implemented in the STL..
which includes..

-> Sequential Container

    --> Vectors
    --> Stack
    --> Queue
    --> Pair

-> Ordered Container

    --> Maps
    --> Multimap
    --> Set
    --> Multiset

-> Unordered Container

    --> Unordered map
    --> Unordered set

-> Nested Container

    --> vector<vector<int>>
    --> map<int, vector, or int>
    --> set<pair<int, string>>
    --> vector<map<int, set<int>>>



### 2. Iterator

Similar to pointers.. but they are implemented in the STL to the point the element../

--> begin(), end()
--> `vector<int> :: iterator it`


### 3. Algorithm

+ upper bound
+ lower bound
+ sort (comparator - {custom sorting behaviour})
+ max_element
+ min_element
+ accumulator
+ reverse
+ count
+ find
+ next_permutation
+ prev_permutation

### 4. Functors

Class which can act as functions..//
