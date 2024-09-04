# MongoDB Installation
1. Use `choco install mongodb`
2. To verify installation run this `mongod` in cmd
3. Download MongoDB Shell `mongosh` from [Mongosh](https://www.mongodb.com/try/download/shell).
4. Launch MongoDb-Compass and connect to MongoDB.
- Note: You can use `chocolatey` package manager or download it from the official website. [MongoDb download](https://www.mongodb.com/try/download/community) 

# Introduction to Mongodb
MongoDB is a popular open-source NoSQL database that uses a document-oriented data model.
Unlike traditional relational databases that store data in tables with rows and columns, MongoDB stores data in flexible, JSON-like documents. 
This allows for more dynamic and scalable data storage, making it well-suited for applications with evolving data requirements.

### Key Features
- Document-Oriented Storage: Data is stored in BSON (Binary JSON) format, which allows for nested data structures.
- Schema Flexibility: Documents in a collection do not need to have the same set of fields, and data types for the same field can differ across documents.
- Scalability: Supports horizontal scaling through sharding, which distributes data across multiple servers.
- Indexing: Supports various types of indexes to improve query performance.
- Aggregation Framework: Provides powerful tools for data aggregation and transformation.
- Replication: Supports replica sets for high availability and data redundancy.

### Core concepts
1. Database: It is a container for collections, similar to how a database in a relational system contains tables. Each database has its own set of collections and is stored on disk as separate files. You can have multiple databases on a MongoDB server, each serving a different application or purpose.

2. Collection: A collection is a grouping of MongoDB documents, similar to a table in a relational database. However, unlike tables, collections do not enforce a schema, meaning the documents within a collection can have different structures. Collections are created dynamically when a document is inserted into them.

3. Document: A document is the basic unit of data in MongoDB, similar to a row in a relational database but more flexible. Documents are stored in BSON (Binary JSON) format, which allows them to hold complex data structures, including nested arrays and objects. Each document is a collection of key-value pairs, where the keys are strings, and the values can be various data types (e.g., string, number, array, object).

4. Fields: Fields are the key-value pairs within a document, similar to columns in a relational database table. Each field contains a specific piece of data. Unlike relational databases, fields in MongoDB documents are flexible, meaning different documents in the same collection can have different fields.

![image](https://github.com/user-attachments/assets/47fb5fb0-e27e-49d8-a84c-917cfdf871d4)

![image](https://github.com/user-attachments/assets/76b0f9c8-f8a1-426e-aa94-125e17c1bd2b)

![image](https://github.com/user-attachments/assets/89c245fd-65ae-4513-9f2f-9faba2616814)

![image](https://github.com/user-attachments/assets/6c939bab-39c7-40b2-afcf-878305730e65)

# Creating a database, collection and adding data to it using MongoDB-Compass

![image](https://github.com/user-attachments/assets/28eb1f3c-d50a-4506-b958-3549fd4378ee)  

- 1st + → creating a connection
- 2nd + → creating database
- 3rd → creating a collection

Add data > insert document 

![image](https://github.com/user-attachments/assets/c12de609-fe4a-4b59-ac32-da258b39ed3f)

Data added

![image](https://github.com/user-attachments/assets/6478ed38-2ea4-4118-a03e-215c78fbb67e)

There is no need for schema here.
"schema" refers to the structure of the data, including the fields and their data types. Unlike traditional relational databases like MySQL , which enforce a strict schema at the database level, MongoDB is schema-less or schema-flexible. 
This means:
No Fixed Schema: Collections do not enforce a fixed schema. Documents within the same collection can have different sets of fields, and the data types for the same field can vary across documents.
Dynamic Schema: You can add or remove fields from documents without having to update a central schema definition. This allows for more flexibility and faster iteration during development.
Nested Data Structures: MongoDB supports nested documents and arrays, allowing for more complex data representations within a single document.

```mongosh
_id: ObjectId('66d6c04165421871b216b8cf')
name : "Swati"
role : "Devops"

_id: ObjectId('66d6c10365421871b216b8d0')
name : "Niall"
location: "San Fransisco"
```
### Basic Commands
`show dbs`

![image](https://github.com/user-attachments/assets/20f23f2f-c97e-4be0-ab9a-4361be1444dd)

`use <database-name>`

![image](https://github.com/user-attachments/assets/6ea04f29-e409-4954-89b0-36a620029f75)


# CRUD Operations

[Documentation](https://www.mongodb.com/docs/manual/)

### Insert

The MongoDB shell provides the following methods to insert documents into a collection:
To insert a single document, use `db.collection.insertOne()`.
To insert multiple documents, use `db.collection.insertMany()`.

Examples:
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


### Read

Use the `db.collection.find()` method in the MongoDB Shell to query documents in a collection.
`db.inventory.find()` - fetch all documents, Read All Documents in a Collection
This operation is equivalent to the following SQL statement `SELECT * FROM movies`

`db.collection.find({})` 

![image](https://github.com/user-attachments/assets/8df5bb72-ecc9-44c2-a8b6-1bf76019b07b)


#### Specify Equality Condition
To select documents which match an equality condition, specify the condition as a `<field>:<value>` pair in the query filter document.

`db.inventory.find({type: “web series”})`

#### Specify Conditions Using Query Operators

Use query operators in a query filter document to perform more complex comparisons and evaluations. Query operators in a query filter document have the following form:
`{ <field1>: { <operator1>: <value1> }, ... }`
`db.inventory.find({type: {$in: ["web series" , "Netflix Original"]}})`

#### Examples:

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

### Update
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

### Delete

1.deleteMany()
`db.Programmers.deleteMany({})`

![image](https://github.com/user-attachments/assets/78dd900a-a4ac-4baf-af1e-c3873670795e)

2. deleteOne()
`db.Programmers.deleteOne({})`

 ![image](https://github.com/user-attachments/assets/47e9ef99-f1db-4458-8315-c18705eb2b0f)

# Sort and Limit Data

1. limit
`db.people.find().limit(2)`

![image](https://github.com/user-attachments/assets/2a4e9342-a46f-41f3-b536-1154f570f51c)



Use : It is used in Pagination 
Pagination  is a technique used in database queries (and in web applications generally) to divide a large dataset into smaller, more manageable chunks or "pages." This allows users to retrieve and view a portion of the data at a time rather than loading the entire dataset in a single query.
- Achieving pagination using Mongodb find and limit

- ![image](https://github.com/user-attachments/assets/7b38ab04-9c96-4345-bb04-aec2dd868248)

2. Skip : skips the specified number of documents
`db.people.find().skip(1)`

![image](https://github.com/user-attachments/assets/a3ad9f70-4d16-42ef-90e1-a145f0d60446)

3.sort
`db.people.find().sort({age:1})`
1 → ascending order

![image](https://github.com/user-attachments/assets/1d2dab9a-2968-4797-b1b0-a80cf4f15ff3)


`db.people.find().sort({age: -1})`
-1 → descending order

![image](https://github.com/user-attachments/assets/d41ffcba-82bd-4adc-8881-94915d2c98ee)




# Operators
[Documentation](https://www.mongodb.com/docs/manual/reference/operator/)

`db.swati.find({ age: {$in:  [29, 36, 70]  } }) `

![image](https://github.com/user-attachments/assets/5e0bb714-243c-4943-abae-39b6ad26b516)

`db.swati.find({ age: {$eq: 29 } })`

![image](https://github.com/user-attachments/assets/fdbe3dcc-f7df-4d0a-a512-3e17c84e5cd8)


# Aggregation Pipeline
An aggregation pipeline consists of one or more stages that process documents:
Each stage performs an operation on the input documents. For example, a stage can filter documents, group documents, and calculate values.
The documents that are output from a stage are passed to the next stage.
An aggregation pipeline can return results for groups of documents. For example, return the total, average, maximum, and minimum values.
You can update documents with an aggregation pipeline if you use the stages shown in Updates with Aggregation Pipeline.

[Documentation](https://www.mongodb.com/docs/manual/core/aggregation-pipeline/)

#### Data used
```mongosh
db.orders.insertMany( [
   { _id: 0, name: "Pepperoni", size: "small", price: 19,
     quantity: 10, date: ISODate( "2021-03-13T08:14:30Z" ) },
   { _id: 1, name: "Pepperoni", size: "medium", price: 20,
     quantity: 20, date : ISODate( "2021-03-13T09:13:24Z" ) },
   { _id: 2, name: "Pepperoni", size: "large", price: 21,
     quantity: 30, date : ISODate( "2021-03-17T09:22:12Z" ) },
   { _id: 3, name: "Cheese", size: "small", price: 12,
     quantity: 15, date : ISODate( "2021-03-13T11:21:39.736Z" ) },
   { _id: 4, name: "Cheese", size: "medium", price: 13,
     quantity:50, date : ISODate( "2022-01-12T21:23:13.331Z" ) },
   { _id: 5, name: "Cheese", size: "large", price: 14,
     quantity: 10, date : ISODate( "2022-01-12T05:08:13Z" ) },
   { _id: 6, name: "Vegan", size: "small", price: 17,
     quantity: 10, date : ISODate( "2021-01-13T05:08:13Z" ) },
   { _id: 7, name: "Vegan", size: "medium", price: 18,
     quantity: 10, date : ISODate( "2021-01-13T05:10:13Z" ) }
] )
```
#### Query

Calculate Total Order Quantity
The following aggregation pipeline example contains two stages and returns the total order quantity of medium size pizzas grouped by pizza name:
```mongosh
db.orders.aggregate( [

   // Stage 1: Filter pizza order documents by pizza size
   {
      $match: { size: "medium" }
   },

   // Stage 2: Group remaining documents by pizza name and calculate total quantity
   {
      $group: { _id: "$name", totalQuantity: { $sum: "$quantity" } }
   }

] )
```

- The $match stage:
  Filters the pizza order documents to pizzas with a size of medium.
  Passes the remaining documents to the $group stage.
- The $group stage:
  Groups the remaining documents by pizza name.
  Uses $sum to calculate the total order quantity for each pizza name. The total is stored in the totalQuantity field returned by the aggregation pipeline.

#### Output

![image](https://github.com/user-attachments/assets/43fa8d7b-ffa4-434c-8f1b-122c132d107a)

# Mongodb - Atlas 
MongoDB Atlas is a cloud-based, fully-managed database service provided by MongoDB. It offers a way to deploy, manage, and scale MongoDB databases without having to handle the operational aspects such as provisioning, patching, and backups. 

Key features of MongoDB Atlas:

- Managed Service: MongoDB Atlas handles the operational aspects of running MongoDB databases, including automated backups, monitoring, and security.
- Scalability: It provides auto-scaling capabilities, allowing you to adjust resources based on your application's needs. You can scale vertically by increasing instance size or horizontally by adding more nodes.
- Global Deployment: Atlas allows you to deploy databases across multiple cloud providers (AWS, Azure, and Google Cloud) and regions, which can improve performance and redundancy.
- Security: It includes built-in security features like encryption at rest and in transit, fine-grained access controls, and network isolation.
- Monitoring and Analytics: Provides real-time monitoring, alerts, and performance analytics, helping you keep track of database health and performance.
- Easy Integration: Atlas integrates with various tools and services, including MongoDB’s own tools, third-party monitoring solutions, and application frameworks.
- Automated Updates: Atlas manages updates and patches to ensure you are always running the latest, stable version of MongoDB.

