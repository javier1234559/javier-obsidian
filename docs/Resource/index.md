

Về sau sẽ bổ sung các note về sở thích nhưng chưa có thời gian thực hiện ở đây 
Sẽ có dạng như dưới đây

### Mở gần đây 
---
```dataview
TABLE file.ctime AS "Time"
FROM #todo and "docs/Project"
SORT file.ctime DESCENDING
LIMIT 5
```

### Các hashtag chủ đề trong resources

```dataview
TABLE file.tags as tags
FROM "docs/Resource" 
WHERE file.name != this.file.name
```
