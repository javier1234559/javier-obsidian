

Về sau sẽ bổ sung các note về sở thích nhưng chưa có thời gian thực hiện ở đây 
Sẽ có dạng như dưới đây

### Mở gần đây trong Resource
---
```dataview
TABLE file.mtime AS "Time"
FROM "docs/Resource"
SORT file.mtime DESCENDING
LIMIT 3
```

### Các hashtag chủ đề trong resources

```dataview
TÁ 
FROM "docs/Resource" 
FLATTEN file.tags
GROUP BY file.tags as "TAG - 2 "
```
