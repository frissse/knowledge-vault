---
type: MT dataview
alias: list of youTube videos
---
[[MT dataview]]

```dataview
TABLE alias, type
FROM "videos"
WHERE [contains(file.type, "MT youtube-video") = true]
```


