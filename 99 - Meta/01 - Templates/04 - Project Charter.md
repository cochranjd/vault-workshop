---
title:
description:
due-date:
status: open
---

# Todos

```tasks
status.type is NOT DONE
(tags include #topics/project-placeholder)
sort by due reverse
```

# Index

```dataview
table file.cday as "Created"
from ""
where contains(tags, "topics/project-placeholder")
sort file.cday desc
```