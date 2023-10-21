

Về sau sẽ bổ sung các note về sở thích nhưng chưa có thời gian thực hiện ở đây 
Sẽ có dạng như dưới đây

### Mở gần đây 
---
```dataview
TABLE 
default(finished, date(today)) AS "Time"
FROM #todo
SORT file.ctime DESCENDING
LIMIT 5
```

### Các hashtag chủ đề trong resources
#life #book #book/finace

