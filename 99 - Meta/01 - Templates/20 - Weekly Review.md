---
date: <% tp.date.now("YYYY-MM-DD") %>
tags:
  - core/review
---

> [!weekly-review-tasks] Tasks
> - [ ] Complete weekly review 📅 <% tp.date.now("YYYY-MM-DD") %>
> 
> ### Open Tasks
> ```tasks
> not done
> (no start date) OR (starts before today)
> ```

> [!weekly-review-ideas] Ideas
> ```dataviewjs
> dv.table(
 >  ["Ideas", "Status"],
 >  dv.pages('"03 - Ideas"')
 >    .filter(p => p.status === "open")
 >    .map(p => [dv.fileLink(p.file.path), p.status])
 >);
 >```

> [!weekly-review-projects] Projects
 >```dataviewjs
 >dv.table(
 >  ["Projects", "Status"],
 >  dv.pages('"04 - Projects"')
 >    .filter(p => ["open", "active"].includes(p.status))
 >    .map(p => [dv.fileLink(p.file.path), p.status])
 >);
 >```
