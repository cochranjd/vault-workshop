---
date: <% tp.date.now("YYYY-MM-DD") %>
tags:
  - daily
---

## Due Tasks
```tasks
not done
(due before tomorrow) OR (scheduled before tomorrow) OR ((has start date) AND (starts before tomorrow))
(tags do not include #doit )
```

## Selected Tasks

```tasks
not done
(tags include #doit)
```

## Meetings


## PTO

```dataviewjs
const page = dv.page("06 - Tracking/00 - PTO")
const date = dv.current().file.name.split(',')[0]
const blocks = page.file.lists.filter(list => list.text.includes(date))

if (blocks.length > 0) {
	const list = []
	for (let block of blocks) {
		list.push(` ${block.text.match(/^\w+/)[0]}`)
	}
	dv.paragraph(`###### Out today: ${list.join(',')}`)
} else {
	dv.el('span', 'Nobody out today.', { cls: 'text-slight' })
}
```

```dataviewjs
const page = dv.page("06 - Tracking/01 - Key Dates")
const today = window.moment()   // now
const max = window.moment().add(7, 'days')  // 7 days ahead

let matches = []

for (let line of page.file.lists) {
	// each line looks like: `2025-11-20 Benefits enrollment`
	const m = line.text.match(/^(\d{4}-\d{2}-\d{2})\s+(.*)$/)
	if (!m) continue

	const date = window.moment(m[1], "YYYY-MM-DD")
	const event = m[2]

	if (date.isSameOrAfter(today, 'day') && date.isSameOrBefore(max, 'day')) {
		matches.push(`${m[1]} ${event}`)
	}
}

if (matches.length === 0) {
	dv.paragraph("No key dates")
} else {
	for (let m of matches) dv.paragraph(m)
}
```
