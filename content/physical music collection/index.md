
```dataview
TABLE WITHOUT ID official-image AS "image", file.link as "album", artists AS "artist(s)", type, date-obtained AS "date got", notes
FROM "physical music collection"
WHERE type
SORT date-obtained DESC
```
