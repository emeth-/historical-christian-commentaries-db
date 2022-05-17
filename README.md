# historical-christian-commentaries-db

## FILE NAME FORMATS:

```
[Father-Name]/[Book-Name] Chapter_Verse.json
[Father-Name]/[Book-Name] Chapter_Verse-Verse.json
[Father-Name]/[Book-Name] Chapter_Verse-Chapter_Verse.json
```

Examples:
- A commentary by Augustine on Matthew 23:35 = Filename: `Augustine/Matthew 23_35.json`
- A commentary by Jerome on Matthew 23:35-41 = Filename: `Jerome/Matthew 23_35-41.json`
- A commentary by Basil of Caesarea on 1 Kings 19:10-20:3 = Filename: `Basil of Caesarea/1 Kings 19_10-20_3.json`

So the basic rule is write the 'long form' name of everything (books/people), and replace colons (:) with underscores (_). That's it.

<details>
    <summary><b>Why do we use the long form of people's names? Why Augustine of Hippo, rather than just Augustine?</b></summary>

The reason for this is simple enough - In his Catena Aurea, Aquinas lists "Maximus" as the author for several commentaries. 

On a Maximus commentary of Luke 3:7-9, Aquinas prefixes the quotation with "lib. Ascet.", which easily enough points to Liber Asceticus, a writing by [Maximus the Confessor](https://en.wikipedia.org/wiki/Maximus_the_Confessor#Writings). 

However on a Maximus commentary on Luke 2:8-12 and Matthew 3:1-3, Aquinas prefixes the quotations with "in Serm. Nativ. 4." and "Hom. in Joan. Bap. nat. 1." - and it does not appear Maximus the Confessor left us any sermons or homilies [among his writings](https://en.wikipedia.org/wiki/Maximus_the_Confessor#Writings). However Maximus of Turin [left many of both](https://en.wikipedia.org/wiki/Maximus_of_Turin#Works), and is likely these source for these commentaries Aquinas quoted.

Having to dig into problems like that increase the rate at which my gray hair grows, therefore we seek the most descriptive names possible for each person in this repo.

We also accept that for some people, it is not possible/necessary. For example, `Jerome` is universally understood to refer to a single man, and he doesn't have any kind of commonly known longer-form name. However, while `Augustine` is universally understood to refer to a single man, he does have a common longer-form name which we therefore use, `Augustine of Hippo`.
</details>


## File Contents Format

- Each file contains a json value.
  - This can be a single object, or a list of objects, either is fine. 
- Mandatory keys
  - `quote`: The source quotation, can include unicode as HTML entities but should not include any html
  - `sources`: a list of objects with "url" and "title" values, should always include at least one source.
- Optional keys
  - `append_to_author_name`: Use this for things like when you are quoting from a secondary source, e.g. if Aquinas said that Jerome said something, put the quote under Jerome, but in append_to_author_name put the value " (as quoted by Aquinas, AD 1274)"
  - `time`: The year A.D. that the writing was written. Use a negative value for B.C. Should be just a single numerical value. If not supplied, defaults to metadata.json's death year for the Church Father.

Minimal Example:
```
{
    "quote": "commentary by a church father goes here.",
    "sources": [
        {
            "url": "https://example.com",
            "title": "Name of book church father wrote"
        }
    ]
}
```

Example with multiple quotes from 1 church father on 1 passage of scripture
```
[
    {
        "quote": "short quotation from a church father",
        "sources": [
            {
                "url": "https:\/\/www.ecatholic2000.com\/catena\/untitled-111.shtml",
                "title": "Catena Aurea by Aquinas"
            },
            {
                "url": "https:\/\/ccel.org\/ccel\/aquinas\/catena1\/catena1.i.html",
                "title": "Catena Aurea by Aquinas"
            }
        ],
        "append_to_author_name": " (as quoted by Aquinas, AD 1274)"
    },
    {
        "quote": "Long quotation from a church father\n\nThis text is on a new line",
        "sources": [
            {
                "url": "https://www.newadvent.org/fathers/3007.htm",
                "title": "Against Helvidius"
            }
        ],
        "time": "383"
    }
]
```
