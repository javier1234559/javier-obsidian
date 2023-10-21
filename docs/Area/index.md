
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
LIST
FROM "docs/Area" 
FLATTEN file.tags
GROUP BY file.tags as "TAG - 2 "
```
