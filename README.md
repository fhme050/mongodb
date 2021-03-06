# ID:208602086
## mongodb project
#### 1.Create DB 
```sql
use mongo_practice
```
result:
```sql
switched to db mongo_practice
```
#### 2.Insert data to movies collection.
```sql
db.movies.insert({"title":"Fight Club","writer":"Chuck Palahniuk","year":1999,"actors": ["Brad Pitt","Edward Norton"]})
db.movies.insert({"title":"Pulp Fiction","writer":"Quentin Tarantino","year":1994,"actors": ["John Travolta","Uma Thurman"]})
db.movies.insert({"title":"The Hobbit: An Unexpected Journey","writer":"J.R.R. Tolkein","year":2012,"franchise":"The Hobbit"})
db.movies.insert({"title":"The Hobbit: The Desolation of Smaug","writer":"J.R.R. Tolkein","year":2013,"franchise":"The Hobbit"})
db.movies.insert({"title":"The Hobbit: The Battle of the Five Armies","writer":"J.R.R. Tolkein","year":2012,"franchise":"The Hobbit","synopsis":"Bilbo and Company are forced to engage in a war against an array of combatants and keep the Lonely Mountain from falling into the hands of a rising darkness."})
db.movies.insert({"title":"Pee Wee Herman's Big Adventure"})
db.movies.insert({"title":"Avatar"})
```
#### 3.get all documents
```sql
 db.movies.find().pretty()
```
result:
```sql
{
        "_id" : ObjectId("5c43e46ecb79af652b10b769"),
        "title" : "Fight Club",
        "writer" : "Chuck Palahniuk",
        "year" : 1999,
        "actors" : [
                "Brad Pitt",
                "Edward Norton"
        ]
}
{
        "_id" : ObjectId("5c43e77ecb79af652b10b76a"),
        "title" : "Pulp Fiction",
        "writer" : "Quentin Tarantino",
        "year" : 1994,
        "actors" : [
                "John Travolta",
                "Uma Thurman"
        ]
}
{
        "_id" : ObjectId("5c43e82bcb79af652b10b76b"),
        "title" : "Inglorious Basterds",
        "writer" : "Quentin Tarantino",
        "year" : 2009,
        "actors" : [
                " Brad Pitt",
                "Diane Kruger",
                "Eli Roth"
        ]
}
{
        "_id" : ObjectId("5c43e8eecb79af652b10b76c"),
        "title" : "The Hobbit: An Unexpected Journey",
        "writer" : "J.R.R. Tolkein",
        "year" : 2012,
        "franchise" : "The Hobbit"
}
{
        "_id" : ObjectId("5c43ea59cb79af652b10b76d"),
        "title" : "The Hobbit: The Desolation of Smaug",
        "writer" : "J.R.R. Tolkein",
        "year" : 2013,
        "franchise" : "The Hobbit"
}
{
        "_id" : ObjectId("5c43eaabcb79af652b10b76e"),
        "title" : "The Hobbit: The Battle of the Five Armies",
        "writer" : "J.R.R. Tolkein",
        "year" : 2012,
        "franchise" : "The Hobbit",
        "synopsis" : "Bilbo and Company are forced to engage in a war against an array of combatants and keep the Lonely Mountain from falling into the hands of a rising darkness."
}
{
        "_id" : ObjectId("5c43eb0dcb79af652b10b76f"),
        "title" : "Pee Wee Herman's Big Adventure"
}
{ "_id" : ObjectId("5c43eb3fcb79af652b10b770"), "title" : "Avatar" }
```
#### 4.get all documents with writer set to "Quentin Tarantino"
```sql
 db.movies.find({"writer":{$regex:'Quentin Tarantino.*'}}).pretty()
```
result:
```sql
{
        "_id" : ObjectId("5c43e77ecb79af652b10b76a"),
        "title" : "Pulp Fiction",
        "writer" : "Quentin Tarantino",
        "year" : 1994,
        "actors" : [
                "John Travolta",
                "Uma Thurman"
        ]
}
{
        "_id" : ObjectId("5c43e82bcb79af652b10b76b"),
        "title" : "Inglorious Basterds",
        "writer" : "Quentin Tarantino",
        "year" : 2009,
        "actors" : [
                " Brad Pitt",
                "Diane Kruger",
                "Eli Roth"
        ]
}
```
#### 5.get all documents where actors include "Brad Pitt"
```sql
 db.movies.find({"actors":{$regex:'Brad Pitt.*'}}).pretty()
 ```
 result:
```sql
{
        "_id" : ObjectId("5c43e46ecb79af652b10b769"),
        "title" : "Fight Club",
        "writer" : "Chuck Palahniuk",
        "year" : 1999,
        "actors" : [
                "Brad Pitt",
                "Edward Norton"
        ]
}
{
        "_id" : ObjectId("5c43e82bcb79af652b10b76b"),
        "title" : "Inglorious Basterds",
        "writer" : "Quentin Tarantino",
        "year" : 2009,
        "actors" : [
                " Brad Pitt",
                "Diane Kruger",
                "Eli Roth"
        ]
}
```
#### 6.get all documents with franchise set to "The Hobbit"
```sql
db.movies.find({"franchise":{$regex:'The Hobbit.*'}}).pretty()
```
 result:
```sql
{
        "_id" : ObjectId("5c43e8eecb79af652b10b76c"),
        "title" : "The Hobbit: An Unexpected Journey",
        "writer" : "J.R.R. Tolkein",
        "year" : 2012,
        "franchise" : "The Hobbit"
}
{
        "_id" : ObjectId("5c43ea59cb79af652b10b76d"),
        "title" : "The Hobbit: The Desolation of Smaug",
        "writer" : "J.R.R. Tolkein",
        "year" : 2013,
        "franchise" : "The Hobbit"
}
{
        "_id" : ObjectId("5c43eaabcb79af652b10b76e"),
        "title" : "The Hobbit: The Battle of the Five Armies",
        "writer" : "J.R.R. Tolkein",
        "year" : 2012,
        "franchise" : "The Hobbit",
        "synopsis" : "Bilbo and Company are forced to engage in a war against an array of combatants and keep the Lonely Mountain from falling into the hands of a rising darkness."
}
```
#### 7.get all movies released in the 90s
```sql
db.movies.find({$and:[{"year":{$gte:1900}},{"year":{$lte:1999}} ]}).pretty()
```
result
```sql
{
        "_id" : ObjectId("5c43e46ecb79af652b10b769"),
        "title" : "Fight Club",
        "writer" : "Chuck Palahniuk",
        "year" : 1999,
        "actors" : [
                "Brad Pitt",
                "Edward Norton"
        ]
}
{
        "_id" : ObjectId("5c43e77ecb79af652b10b76a"),
        "title" : "Pulp Fiction",
        "writer" : "Quentin Tarantino",
        "year" : 1994,
        "actors" : [
                "John Travolta",
                "Uma Thurman"
        ]
}
```
#### 8.get all movies released before the year 2000 or after 2010
```sql
db.movies.find({$or:[{"year":{$gt:2010}},{"year":{$lt:2000}} ]}).pretty()
```
result
```sql
{
        "_id" : ObjectId("5c43e46ecb79af652b10b769"),
        "title" : "Fight Club",
        "writer" : "Chuck Palahniuk",
        "year" : 1999,
        "actors" : [
                "Brad Pitt",
                "Edward Norton"
        ]
}
{
        "_id" : ObjectId("5c43e77ecb79af652b10b76a"),
        "title" : "Pulp Fiction",
        "writer" : "Quentin Tarantino",
        "year" : 1994,
        "actors" : [
                "John Travolta",
                "Uma Thurman"
        ]
}
{
        "_id" : ObjectId("5c43e82bcb79af652b10b76b"),
        "title" : "The Hobbit: An Unexpected Journey",
        "writer" : "J.R.R. Tolkein",
        "year" : 2012,
        "franchise" : "The Hobbit"
}
{
        "_id" : ObjectId("5c43e8eecb79af652b10b76c"),
        "title" : "The Hobbit: The Desolation of Smaug",
        "writer" : "J.R.R. Tolkein",
        "year" : 2013,
        "franchise" : "The Hobbit"
}
{
        "_id" : ObjectId("5c43ea59cb79af652b10b76d"),
        "title" : "The Hobbit: The Battle of the Five Armies",
        "writer" : "J.R.R. Tolkein",
        "year" : 2012,
        "franchise" : "The Hobbit",
        "synopsis" : "Bilbo and Company are forced to engage in a war against an array of combatants and keep the Lonely Mountain from falling into the hands of a rising darkness."

 ```
#### 9.add a synopsis to "The Hobbit: An Unexpected Journey"
```sql
 db.movies.update({ "_id" : ObjectId("5c43e82bcb79af652b10b76b")},{"title":"The Hobbit: An Unexpected Journey","writer":"J.R.R. Tolkein","year":2012,"franchise":"The Hobbit","synopsis":"A reluctant hobbit, Bilbo Baggins, sets out to the Lonely Mountain with a spirited group of dwarves to reclaim their mountain home - and the gold within it - from the dragon Smaug."})
```
result
```sql
{
        "_id" : ObjectId("5c43e82bcb79af652b10b76b"),
        "title" : "The Hobbit: An Unexpected Journey",
        "writer" : "J.R.R. Tolkein",
        "year" : 2012,
        "franchise" : "The Hobbit",
        "synopsis" : "A reluctant hobbit, Bilbo Baggins, sets out to the Lonely Mountain with a spirited group of dwarves to reclaim their mountain home - and the gold within it - from the dragon Smaug."
}
```
#### 10.add a synopsis to "The Hobbit: The Desolation of Smaug"   
```sql
  db.movies.update({ "_id" : ObjectId("5c43e8eecb79af652b10b76c")},{"title":"The Hobbit: The Desolation of Smaug","writer":"J.R.R. Tolkein","year":2013,"franchise":"The Hobbit","synopsis":"The dwarves, along with Bilbo Baggins and Gandalf the Grey, continue their quest to reclaim Erebor, their homeland, from Smaug. Bilbo Baggins is in possession of a mysterious and magical ring."})
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
```
result
```sql
{
        "_id" : ObjectId("5c43e8eecb79af652b10b76c"),
        "title" : "The Hobbit: The Desolation of Smaug",
        "writer" : "J.R.R. Tolkein",
        "year" : 2013,
        "franchise" : "The Hobbit",
        "synopsis" : "The dwarves, along with Bilbo Baggins and Gandalf the Grey, continue their quest to reclaim Erebor, their homeland, from Smaug. Bilbo Baggins is in possession of a mysterious and magical ring."
}
```
#### 11.add an actor named "Samuel L. Jackson" to the movie "Pulp Fiction"
```sql
  db.movies.update({ "_id" : ObjectId("5c43e77ecb79af652b10b76a")},{"title":"Pulp Fiction","writer":"Quentin Tarantino","year":1994,"actors": ["John Travolta","Uma Thurman","Samuel L. Jackson"]})
  ```
  result
  ```sql
  {
        "_id" : ObjectId("5c43e77ecb79af652b10b76a"),
        "title" : "Pulp Fiction",
        "writer" : "Quentin Tarantino",
        "year" : 1994,
        "actors" : [
                "John Travolta",
                "Uma Thurman",
                "Samuel L. Jackson"
        ]
}
```
#### 12.find all movies that have a synopsis that contains the word "Bilbo"
```sql
> db.movies.find({"synopsis":{$regex:'Bilbo.*'}}).pretty()
```
result
```sql
{
        "_id" : ObjectId("5c43e82bcb79af652b10b76b"),
        "title" : "The Hobbit: An Unexpected Journey",
        "writer" : "J.R.R. Tolkein",
        "year" : 2012,
        "franchise" : "The Hobbit",
        "synopsis" : "A reluctant hobbit, Bilbo Baggins, sets out to the Lonely Mountain with a spirited group of dwarves to reclaim their mountain home - and the gold within it - from the dragon Smaug."
}
{
        "_id" : ObjectId("5c43e8eecb79af652b10b76c"),
        "title" : "The Hobbit: The Desolation of Smaug",
        "writer" : "J.R.R. Tolkein",
        "year" : 2013,
        "franchise" : "The Hobbit",
        "synopsis" : "The dwarves, along with Bilbo Baggins and Gandalf the Grey, continue their quest to reclaim Erebor, their homeland, from Smaug. Bilbo Baggins is in possession of a mysterious and magical ring."
}
{
        "_id" : ObjectId("5c43ea59cb79af652b10b76d"),
        "title" : "The Hobbit: The Battle of the Five Armies",
        "writer" : "J.R.R. Tolkein",
        "year" : 2012,
        "franchise" : "The Hobbit",
        "synopsis" : "Bilbo and Company are forced to engage in a war against an array of combatants and keep the Lonely Mountain from falling into the hands of a rising darkness."
}
```
#### 13.find all movies that have a synopsis that contains the word "Gandalf"
```sql
 db.movies.find({"synopsis":{$regex:'Gandalf.*'}}).pretty()
```
result
```sql
{
        "_id" : ObjectId("5c43e8eecb79af652b10b76c"),
        "title" : "The Hobbit: The Desolation of Smaug",
        "writer" : "J.R.R. Tolkein",
        "year" : 2013,
        "franchise" : "The Hobbit",
        "synopsis" : "The dwarves, along with Bilbo Baggins and Gandalf the Grey, continue their quest to reclaim Erebor, their homeland, from Smaug. Bilbo Baggins is in possession of a mysterious and magical ring."
}
```
#### 14.find all movies that have a synopsis that contains the word "Bilbo" and not the word "Gandalf"
```sql
db.movies.find({synopsis:{'$regex' : '^((?!Gandalf).)*$', '$options' : 'i',},synopsis:{$regex:'hobbit.*'}}).pretty()
```
result
```sql
{
        "_id" : ObjectId("5c43e82bcb79af652b10b76b"),
        "title" : "The Hobbit: An Unexpected Journey",
        "writer" : "J.R.R. Tolkein",
        "year" : 2012,
        "franchise" : "The Hobbit",
        "synopsis" : "A reluctant hobbit, Bilbo Baggins, sets out to the Lonely Mountain with a spirited group of dwarves to reclaim their mountain home - and the gold within it - from the dragon Smaug."
}
```
#### 15.find all movies that have a synopsis that contains the word "dwarves" or "hobbit"
```sql
db.movies.find({$or:[{"synopsis":{$regex:'dwarves.*'}},{"synopsis":{$regex:'hobbit.*'}} ]}).pretty()
```
result
```sql
{
        "_id" : ObjectId("5c43e82bcb79af652b10b76b"),
        "title" : "The Hobbit: An Unexpected Journey",
        "writer" : "J.R.R. Tolkein",
        "year" : 2012,
        "franchise" : "The Hobbit",
        "synopsis" : "A reluctant hobbit, Bilbo Baggins, sets out to the Lonely Mountain with a spirited group of dwarves to reclaim their mountain home - and the gold within it - from the dragon Smaug."
}
{
        "_id" : ObjectId("5c43e8eecb79af652b10b76c"),
        "title" : "The Hobbit: The Desolation of Smaug",
        "writer" : "J.R.R. Tolkein",
        "year" : 2013,
        "franchise" : "The Hobbit",
        "synopsis" : "The dwarves, along with Bilbo Baggins and Gandalf the Grey, continue their quest to reclaim Erebor, their homeland, from Smaug. Bilbo Baggins is in possession of a mysterious and magical ring."
}
```
#### 16.find all movies that have a synopsis that contains the word "gold" and "dragon"
```sql
db.movies.find({$and:[{"synopsis":{$regex:'gold.*'}},{"synopsis":{$regex:'dragon.*'}} ]}).pretty()
```
result
```sql
{
        "_id" : ObjectId("5c43e82bcb79af652b10b76b"),
        "title" : "The Hobbit: An Unexpected Journey",
        "writer" : "J.R.R. Tolkein",
        "year" : 2012,
        "franchise" : "The Hobbit",
        "synopsis" : "A reluctant hobbit, Bilbo Baggins, sets out to the Lonely Mountain with a spirited group of dwarves to reclaim their mountain home - and the gold within it - from the dragon Smaug."
}
```
#### 17.delete the movie "Pee Wee Herman's Big Adventure"
```sql
db.movies.remove({"_id" : ObjectId("5c43eb0dcb79af652b10b76f")})
```
result
```sql
WriteResult({ "nRemoved" : 1 })
```
#### 18.delete the movie "Avatar"
```sql
db.movies.remove({"_id" : ObjectId("5c43eb3fcb79af652b10b770")})
```
result
```sql
WriteResult({ "nRemoved" : 1 })
```


```sql
db.movies.find().pretty()
{
        "_id" : ObjectId("5c43e46ecb79af652b10b769"),
        "title" : "Fight Club",
        "writer" : "Chuck Palahniuk",
        "year" : 1999,
        "actors" : [
                "Brad Pitt",
                "Edward Norton"
        ]
}
{
        "_id" : ObjectId("5c43e77ecb79af652b10b76a"),
        "title" : "Pulp Fiction",
        "writer" : "Quentin Tarantino",
        "year" : 1994,
        "actors" : [
                "John Travolta",
                "Uma Thurman",
                "Samuel L. Jackson"
        ]
}
{
        "_id" : ObjectId("5c43e82bcb79af652b10b76b"),
        "title" : "The Hobbit: An Unexpected Journey",
        "writer" : "J.R.R. Tolkein",
        "year" : 2012,
        "franchise" : "The Hobbit",
        "synopsis" : "A reluctant hobbit, Bilbo Baggins, sets out to the Lonely Mountain with a spirited group of dwarves to reclaim their mountain home - and the gold within it - from the dragon Smaug."
}
{
        "_id" : ObjectId("5c43e8eecb79af652b10b76c"),
        "title" : "The Hobbit: The Desolation of Smaug",
        "writer" : "J.R.R. Tolkein",
        "year" : 2013,
        "franchise" : "The Hobbit",
        "synopsis" : "The dwarves, along with Bilbo Baggins and Gandalf the Grey, continue their quest to reclaim Erebor, their homeland, from Smaug. Bilbo Baggins is in possession of a mysterious and magical ring."
}
{
        "_id" : ObjectId("5c43ea59cb79af652b10b76d"),
        "title" : "The Hobbit: The Battle of the Five Armies",
        "writer" : "J.R.R. Tolkein",
        "year" : 2012,
        "franchise" : "The Hobbit",
        "synopsis" : "Bilbo and Company are forced to engage in a war against an array of combatants and keep the Lonely Mountain from falling into the hands of a rising darkness."
}
```







  




 






