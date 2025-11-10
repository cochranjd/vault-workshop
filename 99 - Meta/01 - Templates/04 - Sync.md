---
person: <% tp.file.title.slice(11) %>
when: <% tp.date.now("YYYY-MM-DD") %>
tags:
  - core/1-on-1
  - people/<% tp.file.title.slice(11).toLowerCase().replace(/\ /, '-') %>
---

```tasks
not done
(tags include people/<% tp.file.title.slice(11).toLowerCase().replace(/\ /, '-') %>)
```
