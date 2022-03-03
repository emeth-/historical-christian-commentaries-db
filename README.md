# historical-christian-commentaries-db

FILE NAME FORMAT:

[Father-Name]/[Book-Name] Chapter_Verse-Verse.json
[Father-Name]/[Book-Name] Chapter_Verse-Chapter_Verse.json

E.g.
A Commentary by Jerome on Matthew 23:35-41 = Jerome/Matthew 23_35-41.json
A Commentary by Jerome on Matthew 23:35-24:7 = Jerome/Matthew 23_35-24_7.json
[Basically, just replace colon (:) with underscore (_)]

FILE CONTENTS FORMAT:
[{
  quote: "...",
  time: "400",
  secondary_source: "Aquinas"
  sources: [
    {
      "url": "",
      "title": ""
    }
  ]
}]

The "time" field is optional - if not provided, it defaults to the author's death (if we have that recorded). Provide it if you have a more specific date. Positive = AD and negative = BC

The "secondary_source" field is also optional. Use it if you don't have the original source (e.g. Aquinas quotes Jerome as saying something, but we don't have the original source where Jerome said that. It still goes under Jerome, but with secondary_source=Aquinas)

You must add at least one source, indicating where you pulled the information from (even if it's just a quote inside a book or a scholarly article). If no primary sources are provided, it will remain in a holding place until someone reviews it and finds the primary source to confirm the validity of the commentary.