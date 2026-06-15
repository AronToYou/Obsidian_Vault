
```dataview
TASK
FROM #jobs 
WHERE completed
GROUP BY file.name
SORT rows.file.name DESC
```