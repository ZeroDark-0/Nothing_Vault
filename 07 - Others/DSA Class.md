---
date: 2025-01-07T10:44
tags:
  - DSA
---


---
### <span font ="Blue"> Binary Search </span>

In this algo. we use the left, right and mid method to search in an array. For this algo. to work the array should be sorted.
How it work  - consider the following array
  `int a = [1,2,3,4,5,6,7,8,9]
  with the target value let's say `int target = 3`,
  first we check if the array sorted which is sorted making it eligible to use binary search.   
  Now we assign 3 variable as left_ele, right_ele, and mid_ele
  for `left_ele = index 0`, `right_ele = the length of array`, and `mid_ele = (right_ele + right_ele)/2`
and here the code for this
```java
import java.util.*;

class Main {
    public static void main(String[] args) {
        int arr[] = {6, 11, 15, 19, 23, 56, 89, 94};
        int target = 89;

        // Perform binary search
        int result = binarySearch(arr, target);

        // Output the result
        if (result != -1) {
            System.out.println("Element found at index: " + result);
        } else {
            System.out.println("Element not found in the array.");
        }
    }

    // Binary search method
    public static int binarySearch(int[] arr, int target) {
        int left = 0;
        int right = arr.length - 1;

        while (left <= right) {
            int mid = (left + right) / 2;

            if (arr[mid] == target) {
                return mid; // Target found
            } else if (arr[mid] < target) {
                left = mid + 1; // Search in the right half
            } else {
                right = mid - 1; // Search in the left half
            }
        }

        return -1; // Target not found
    }
}
```

Here, we search we the help of mid, right, left indexes.
If the target is less than arr(mid) meaning the right variable index will be mid - 1, or if target > arr(mid) than the left variable will be mid + 1 and if target == mid(mid) meaning to return the mid, and this is how the binary search work.

==Now the time complexity== 


| Time | --- | Search space |
| ---- | --- | ------------ |
| 1    | --> | n            |
| 2    | --> | n/2          |
| 3    | --> | n/(2^2)      |
| :    | --> | ---          |
| n    | --> | n/(2^k)      |

to prove it - 
n/2^k = 1
n = 2^k
log(n) = log(2^k)
log2(n) = k log2(2)
log2(n) = k // proved

--- 

### Selection sort

In this sorting we run a loop and sort 2 element at a time.
`int arr = {50,10,30,100,60}`
Selection sort the array by repeatedly selecting the smallest element from the  unsorted question and swapping it with the first unsorted element. 
Here we run a loop with two variable 
and here is the code - 
```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        int arr[] = {50, 10, 30, 100, 60};
        
        // Loop through the array
        for (int i = 0; i < arr.length - 1; i++) {
            int a, b;
            a = arr[i]; // Use square brackets [] to access array elements
            b = arr[i + 1]; // Use square brackets [] to access array elements
            
            // Compare and swap if necessary
            if (a > b) {
                arr[i] = b; // Use square brackets [] to assign values
                arr[i + 1] = a; // Use square brackets [] to assign values
            }
        }
        
        // Print the modified array
        System.out.println(Arrays.toString(arr));
    }
}
```

Here the time complexity for this will be = n^2

---

### Bubble sort 

Bubble sort work by repeatedly swapping the adjacent element if they are in a wrong order.


`arr[] = {50,40,100,20,10}` 

code - 
```java
for(int t = 0; t < n - 1; t++) {
    for(int i = 0; i < n - 1 - t; i++) { // Reduce the range as the largest elements bubble to the end
        if(arr[i] > arr[i + 1]) {
            // Swap arr[i] and arr[i + 1]
            int temp = arr[i];
            arr[i] = arr[i + 1];
            arr[i + 1] = temp;
        }
    }
}```

Here, the time complexity will - 
Worst - n^2
average - n^2
good - n

---

### Insertion sort

`arr[] = {17,6,100,20,5}`
Here we separate the array into two part - `{17}` and `6,100,20,5` in which the element with a single element is sorted meanwhile the other one is the unsorted array. Now we compare the first element(17)  with the two element (6), and then we shift the smallest element in front of the 17. Now that the we got two in the sorted array `6,17`. And this algo goes on - 

-{ `17` | 6, 100, 20, 5}
-{`6 , 17` | 100, 20, 5}
-{`6, 17, 100 `| 20, 5}
-{`6, 17, 20, 100 `| 5}
-{`5, 6, 17, 20, 100`}

Definition - Insertion sort that work while iterating insertion each element of an unsorted list into it's correct position in the sorted portion of it .

```java
for(int i = 1; i< n;i ++){
  int key = arr[i];
  int j = i -1;
 while (j>=0 && arr[i] > key){
  arr[j+1} = arr[j];
  j--;
  }
  arr[j+1] = key;
  }
  ```

Worst time complexity - n^2
average time complexity - n(n+1)/2 ~ n^2
best time complexity - n

question - take a string from a user and count the number of vowels
```java
Scanner sc = new Scanner (System.in);
String input = scanner.nextLine();
int vowelcount=0;
input = input.lowerCase();
for(int i = 0; i< input.length();i++){
char ch = input.charAt(i);
if(ch == 'a' || ch == 'e' || ch == 'i' || ch == 'o' || ch == 'u'){
vowelcount++;
}
}
```


---

### Base case

A recursion function must have terminating condition.

```java
import java.util.*;

Class Main{
 Public Static int fib(int n){
    if(n==0){
        return 0;}
    else if (n==1){
        return 1;}
    else{
        return fib(n-1) + fib(n-2);}
  }
 Public Static void main(String[] args){
    int n = 4;
    Sysem.out.print(fib(n));
 }
 }
 ```
 ---

Question - 
1. User input = 5. now print the series from 0 to input in ascending order and descending order 
  and there stack diagram
2. Fibonacci series 
3. print the first occurrence of an element of an array if element  not present in the array and print -1.
```java 
public static int firstoccurrence(int []arr,int target,int idx){
if(idx == arr.length) return -1;
if(arr[idx] == taarget) return idx;
return firstoccurrence(arr,target,idx+1)
```

---

Substring and the subsequences- 
```java 
public static void printsubseq(String s, String ans){
    if(s.length() == 0){
        System.out.println(ans);
        return;
    }
}

public static void main(String[] args){
    printsubseq(s.substring(1),ans);
    printsubseq(s.substring(1),ans+s.charAt(0));
}

```

---

