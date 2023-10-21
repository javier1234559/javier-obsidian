

Về sau sẽ bổ sung các note về sở thích nhưng chưa có thời gian thực hiện ở đây 
Sẽ có dạng như dưới đây

### Mở gần đây 
---
```dataview
TABLE file.mtime AS "Time"
FROM "docs/Resource"
SORT file.mtime DESCENDING
LIMIT 3
```

### Các hashtag chủ đề trong resources

```dataview
TABLE file.tags as "Tags"
FROM "docs/Resource" 
```
