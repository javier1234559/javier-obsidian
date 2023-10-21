
# Mở gần đây trong Resource
```dataview
TABLE file.mtime AS "Time"
FROM "docs/Resource"
SORT file.mtime DESCENDING
LIMIT 3
```

### Các hashtag chủ đề trong resources
```dataview
LIST
FROM "docs/Resource" 
FLATTEN file.tags
GROUP BY file.tags as "TAG - 2 "
```
