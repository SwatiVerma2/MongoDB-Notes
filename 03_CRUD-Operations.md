# CRUD Operations


[Documentation](https://www.mongodb.com/docs/manual/)

## Insert

The MongoDB shell provides the following methods to insert documents into a collection:
To insert a single document, use `db.collection.insertOne()`.
To insert multiple documents, use `db.collection.insertMany()`.

### Examples:
```mongosh
db.inventory.insertOne(
  {
    title: "The Favourite",
    type: "movie"
  }
)
```
Output

![image](https://github.com/user-attachments/assets/b1819d7c-e7fd-46d4-8688-414ff4aaa331)


## Read

Use the `db.collection.find()` method in the MongoDB Shell to query documents in a collection.
`db.inventory.find()` - fetch all documents, Read All Documents in a Collection
This operation is equivalent to the following SQL statement `SELECT * FROM movies`

`db.collection.find({})` 

![image](https://github.com/user-attachments/assets/8df5bb72-ecc9-44c2-a8b6-1bf76019b07b)


### Specify Equality Condition
To select documents which match an equality condition, specify the condition as a `<field>:<value>` pair in the query filter document.

`db.inventory.find({type: “web series”})`

### Specify Conditions Using Query Operators

Use query operators in a query filter document to perform more complex comparisons and evaluations. Query operators in a query filter document have the following form:
`{ <field1>: { <operator1>: <value1> }, ... }`
`db.inventory.find({type: {$in: ["web series" , "Netflix Original"]}})`

### Examples:

Sample Data

```mongosh
Sample Data
{
  _id: 1,
  name: 'Alice',
  age: 28,
  city: 'New York',
  occupation: 'Engineer'
}
{
  _id: 2,
  name: 'Bob',
  age: 34,
  city: 'San Francisco',
  occupation: 'Designer'
}
{
  _id: 3,
  name: 'Charlie',
  age: 23,
  city: 'New York',
  occupation: 'Teacher'
}
{
  _id: 4,
  name: 'David',
  age: 29,
  city: 'New York',
  occupation: 'Engineer'
}

```

AND
```mongosh
db.people.find({
  occupation: "Engineer",
  city: "New York"
})
```
Without AND

```mongosh
db.people.find({
  $and: [
    { occupation: "Engineer" },
    { city: "New York" }
  ]
})
```
Output

![image](https://github.com/user-attachments/assets/ea131f26-d7ee-4473-aea3-63f02d2f845a)

Using $gt
```mongosh
db.people.find({
     occupation: "Engineer" ,
     age: {$gt: 23} 
})
```
![image](https://github.com/user-attachments/assets/73fab12c-ac81-42a6-9ecb-0ffc53a0278f)

OR
```mongosh
db.people.find({
  $or: [
    { occupation: "Engineer" },
    { city: "San Francisco" }
  ]
})
```
Output

![image](https://github.com/user-attachments/assets/c0a6f3db-4d09-4e3f-85ad-3f08c99857dc)

Eg 2 
```mongosh
db.people.find({
   $or: [ {occupation: "Engineer" } ,{age: {$gt: 23}} ]
})
```
Output

![image](https://github.com/user-attachments/assets/2fd51838-16df-4972-baad-49c3725fbe04)


The findOne method in MongoDB is used to retrieve a single document from a collection that matches a specified query. Unlike the find method, which returns a cursor pointing to all matching documents, findOne directly returns the first matching document it finds.
Syntax : `db.collection.findOne(query, projection)`

```mongosh
db.people.findOne({
   $or: [ {occupation: "Engineer" } ,{age: {$gt: 23}} ]
})
```
Output

![image](https://github.com/user-attachments/assets/832da74e-7139-4f99-872c-9c0e5623214d)


## Update
1. `updateOne()`
```mongosh
db.people.updateOne(
  { name: "Alice"},
  { $set: { age: 70} }
)
```

Output

![image](https://github.com/user-attachments/assets/79e412c9-7f71-4587-9d51-6cb94c0af128)

Updated Data

![image](https://github.com/user-attachments/assets/715173c8-9728-4072-af2b-a8f7dfe32c61)

2. `updateMany()`
```mongosh
db.people.updateMany(
  {occupation: "Engineer"},
  { $set: {city: "Punjab, India"},
   $currentDate: { lastModified: true }
  }  )
```
Output

![image](https://github.com/user-attachments/assets/dd9fae4a-ca63-4601-ae99-d2a408405be5)

Updated Data

![image](https://github.com/user-attachments/assets/38b31eab-8579-483f-8140-dd3aa5dd31db)


## Delete

1.deleteMany()
`db.Programmers.deleteMany({})`

![image](https://github.com/user-attachments/assets/78dd900a-a4ac-4baf-af1e-c3873670795e)

2. deleteOne()
`db.Programmers.deleteOne({})`

 ![image](https://github.com/user-attachments/assets/47e9ef99-f1db-4458-8315-c18705eb2b0f)
