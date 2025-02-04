---
banner: "![[blue night sky.gif]]"
banner_y: 0.84
cssclasses:
  - center-images
---
# <code style="color:Blue">Main Force</code>


![[starfall.jpg]]



## **<code style="color:cyan">Projects -</code>**  
  
  ```dataview
TABLE status, deadline, area
FROM #project
WHERE !contains(file.path, "00 - Templates")
SORT deadline ASC
```
  
## <code style="color:blue">Areas</code>

```dataview
LIST
FROM #area
WHERE !contains(file.folder, "00 - Templates")
SORT file.name ASC
```

