---
created: <% tp.file.creation_date() %>
---
tags:: [[+Daily Notes]]

# <% moment(tp.file.title,'YYYY-MM-DD').format("dddd, MMMM DD, YYYY") %>

<< [[<% fileDate = moment(tp.file.title, 'YYYY-MM-DD-dddd').subtract(1, 'd').format('YYYY-MM-DD-dddd') %>|Yesterday]] | [[<% fileDate = moment(tp.file.title, 'YYYY-MM-DD-dddd').add(1, 'd').format('YYYY-MM-DD-dddd') %>|Tomorrow]] >>

---
# 💪 Tasks

## 😞 Missed
```tasks
not done
due before today
sort by due
sort by priority
sort by scheduled
```
## 🤝Due After today
```tasks
not done
due after today
sort by due
sort by priority
sort by scheduled
```

## 💆‍♂️No Due Date
```tasks
not done
no due date
sort by due
sort by priority
sort by scheduled
```
---
# 🕵️‍♂️ TODOs

## 🚀 General TODOs
- 


## 💼 Crescer TODOs
- 

---
# 📝 Notes
- 
---
# 💡 Plans for tomorrow
- 
---
### Notes created today
```dataview
List FROM "" WHERE file.cday = date("<%tp.date.now()%>") SORT file.ctime asc
```

### Notes last touched today
```dataview
List FROM "" WHERE file.mday = date("<%tp.date.now()%>") SORT file.mtime asc
```

---

