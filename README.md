
# Introduction to Javier's Obsidian

This is a repository for saving my note

```dataview
TABLE
without id
file.link as "Recent files ",
dateformat(file.mtime,"ff") as "Time"
FROM "docs"
SORT file.mtime DESC
LIMIT 5
```

