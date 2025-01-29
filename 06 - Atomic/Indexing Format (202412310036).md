---
date: 2024-12-31T00:36
tags:
  - "#programming_depth"
cssclasses:
  - recolor-images
  - center-images
---
# Why in multiple programming languages we always start with index 0?

  As we know that every array have a similar behavior whether we are coding in JS, Python, Java, Ruby, and Rust which uses 0 indexing algo and there are exception to this. Languages like Lua, COBOL, Fortran, Julia and MATLAB uses 1 based indexing.  
  
  The main reason for o based indexing is  the design of the language like in ***C***, an array point to the location in memory, so the array of [n].  
  So, n should not be treated as an index but offset from array head.
  For example number 10 is stored in memory as following binary-
  `00000000 00000000 00000000 00000000`
  since one byte is 8 bits meaning an integer will take 4 bytes.
  
  Since array address is calculated using the base address which is first element of address:
  ![[1-Indexing Format (202412310036).png]]
  If we take an array in that each memory location is 1 byte next.
  Meaning the first memory is 0 element away from the second memory 
  