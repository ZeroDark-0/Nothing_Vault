---
date: 2025-01-01T10:16
tags:
  - "#Operating_System"
---
# Dual Boot Deletion 


1. Go to ***Disk Management*** 
2. In the disk management you will find the ==EFI and Root== file 
3. First we delete the ==Root== partition 
4. And for EFI partition there will be no delete option for that-
   1. Go to ==cmd==
   2. Type `diskpart` (show all the disc connect to your computer)
   3. Select the drive -  `select disc 0`
   4. Type `list partition` to get the partition in disc 0
   5. Type `select partition 5` (select the partition you wanna delete)
   6. Type `delete partition override` (to delete it)