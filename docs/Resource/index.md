

Về sau sẽ bổ sung các note về sở thích nhưng chưa có thời gian thực hiện ở đây 
Sẽ có dạng như dưới đây

### Mở gần đây 
---
```dataview
TABLE file.mtime AS "Time"
FROM #todo and "docs/Project"
SORT file.ctime DESCENDING
LIMIT 5
```

### Các hashtag chủ đề trong resources

```dataview
LIST file.tags
FROM "docs/Resource" 
```
