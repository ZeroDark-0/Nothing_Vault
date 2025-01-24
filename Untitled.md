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
