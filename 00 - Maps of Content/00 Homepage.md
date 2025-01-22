---
banner: "![[night sky.gif]]"
cssclasses: 
banner_y: 0.325
---
# Home

Nothing includes Programming, Gamedev, 3D Art, DSA and the other stuff related to that.....

---

#### ->Start - [[01 Map]]


---
## Areas

```dataview
LIST
FROM #area
WHERE !contains(file.folder, "00 - Templates")
SORT file.name ASC
```
## Projects

```dataview
TABLE status, deadline, area
FROM #project
WHERE !contains(file.path, "00 - Templates")
SORT deadline ASC
```
