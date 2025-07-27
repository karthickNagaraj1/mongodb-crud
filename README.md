MongoDB CRUD operations
use library
1. Create (Insert) Operations:
   
db.books.insert({title:"The Great Gatsby", author:"F. Scott Fitzgerald", published_year:1925})
db.books.insertOne({title:"Harry Potter and the Philosopher's Stone", author:"J.K. Rowling", published_year:1997})
db.books.insertMany([
  {title:"To Kill a Mockingbird", author:"Harper Lee", published_year:1960},
  {title:"Pride & Prejudice", author:"Jane Austen", published_year:1813},
  {title:"The Catcher in the Rye", author:"J. D. Salinger", published_year:1951},
  {title:"One Hundred Years of Solitude", author:"Gabriel García Márquez", published_year:1967}
])
Explanation:use library: Switches to or creates the library database.

insert, insertOne, and insertMany: Add books to the books collection.

2.Read (Query) Operations:

db.books.find()
{
  "_id": ObjectId("..."),
  "title": "The Great Gatsby",
  "author": "F. Scott Fitzgerald",
  "published_year": 1925
}
{
  "_id": ObjectId("..."),
  "title": "Harry Potter and the Philosopher's Stone",
  "author": "J.K. Rowling",
  "published_year": 1997
}
{
  "_id": ObjectId("..."),
  "title": "To Kill a Mockingbird",
  "author": "Harper Lee",
  "published_year": 1960
}
{
  "_id": ObjectId("..."),
  "title": "Pride & Prejudice",
  "author": "Jane Austen",
  "published_year": 1813
}
{
  "_id": ObjectId("..."),
  "title": "The Catcher in the Rye",
  "author": "J. D. Salinger",
  "published_year": 1951
}
{
  "_id": ObjectId("..."),
  "title": "One Hundred Years of Solitude",
  "author": "Gabriel García Márquez",
  "published_year": 1967
}
 Explanation:find(): Retrieves all documents in the books collection.

 3.Update Operations:

 db.books.update(
  { title: "Harry Potter and the Philosopher's Stone" },
  { $set: { published_year: 2001 } }
)

Explanation:This updates the published_year of "Harry Potter and the Philosopher's Stone" from 1997 to 2001.

update() is deprecated; recommended method is updateOne().

Adding a New Field (genre)

db.books.update(
  { title: "Harry Potter and the Philosopher's Stone" },
  { $set: { published_year: 2001, genre: "fantasy" } }
)

Explanation:This adds a new field genre with value "fantasy" and reconfirms the published_year as 2001.

4.Delete Operations:

db.books.remove({ title: "The Catcher in the Rye" })
Explanation:
This deletes the book titled "The Catcher in the Rye" from the collection.

remove() is deprecated. Use deleteOne() or deleteMany() instead.

db.books.remove({ published_year: { $lt: 1900 } })

Explanation:
Deletes books published before the year 1900.

In this case, “Pride & Prejudice” (1813) is removed.

db.books.find()
{
  "_id": ObjectId("..."),
  "title": "The Great Gatsby",
  "author": "F. Scott Fitzgerald",
  "published_year": 1925
}
{
  "_id": ObjectId("..."),
  "title": "Harry Potter and the Philosopher's Stone",
  "author": "J.K. Rowling",
  "published_year": 2001,
  "genre": "fantasy"
}
{
  "_id": ObjectId("..."),
  "title": "To Kill a Mockingbird",
  "author": "Harper Lee",
  "published_year": 1960
}
{
  "_id": ObjectId("..."),
  "title": "One Hundred Years of Solitude",
  "author": "Gabriel García Márquez",
  "published_year": 1967
}
Remaining Books (4 total):

The Great Gatsby

Harry Potter and the Philosopher’s Stone

To Kill a Mockingbird

One Hundred Years of Solitude
