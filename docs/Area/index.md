
# Mở gần đây trong Area
```dataview
TABLE 
without id
file.link as "Recent files ",
file.mtime AS "Time"
FROM "docs/Area"
SORT file.mtime DESCENDING
LIMIT 3
```

### Các hashtag chủ đề trong Area
```dataview
list
from "docs/Area"
flatten file.tags as flattags
group by flattags
```
