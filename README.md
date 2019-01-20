# mongodb project
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
db.movies.insert({"title":"Fight Club","writer":"Chuck Palahniuk","year":"1999","actors": ["Brad Pitt","Edward Norton"]})
db.movies.insert({"title":"Pulp Fiction","writer":"Quentin Tarantino","year":"1994","actors": ["John Travolta","Uma Thurman"]})
db.movies.insert({"title":"The Hobbit: An Unexpected Journey","writer":"J.R.R. Tolkein","year":"2012","franchise":"The Hobbit"})
```


