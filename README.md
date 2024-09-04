# MongoDB Notes
# Installation
1. choco install mongodb
2. mongod to verify installation
3. To start the MongoDB server : net start MongoDB
4. Connect to MongoDBOpen another Command Prompt.Type mongo and press Enter. This will start the MongoDB shell and connect to the MongoDB server.
Note: You can use `chocolatey` package manager or download it from [MongoDb download](https://www.mongodb.com/try/download/community) from the official website.

# Introduction to Mongodb
MongoDB is a popular open-source NoSQL database that uses a document-oriented data model.
Unlike traditional relational databases that store data in tables with rows and columns, MongoDB stores data in flexible, JSON-like documents. 
This allows for more dynamic and scalable data storage, making it well-suited for applications with evolving data requirements.

### Key Features
Document-Oriented Storage: Data is stored in BSON (Binary JSON) format, which allows for nested data structures.
Schema Flexibility: Documents in a collection do not need to have the same set of fields, and data types for the same field can differ across documents.
Scalability: Supports horizontal scaling through sharding, which distributes data across multiple servers.
Indexing: Supports various types of indexes to improve query performance.
Aggregation Framework: Provides powerful tools for data aggregation and transformation.
Replication: Supports replica sets for high availability and data redundancy.

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

```javascript
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




