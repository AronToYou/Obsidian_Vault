Yeah!

- [ ] links to bash, git, ... suche
- [ ] make opening page
- [ ] list daily notes?

```dataview
TASK
FROM "DailyNotes"
WHERE !completed
GROUP BY file.name
SORT rows.file.name DESC
```
