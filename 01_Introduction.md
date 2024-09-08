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

## Core concepts
1. Database: It is a container for collections, similar to how a database in a relational system contains tables. Each database has its own set of collections and is stored on disk as separate files. You can have multiple databases on a MongoDB server, each serving a different application or purpose.

2. Collection: A collection is a grouping of MongoDB documents, similar to a table in a relational database. However, unlike tables, collections do not enforce a schema, meaning the documents within a collection can have different structures. Collections are created dynamically when a document is inserted into them.

3. Document: A document is the basic unit of data in MongoDB, similar to a row in a relational database but more flexible. Documents are stored in BSON (Binary JSON) format, which allows them to hold complex data structures, including nested arrays and objects. Each document is a collection of key-value pairs, where the keys are strings, and the values can be various data types (e.g., string, number, array, object).

4. Fields: Fields are the key-value pairs within a document, similar to columns in a relational database table. Each field contains a specific piece of data. Unlike relational databases, fields in MongoDB documents are flexible, meaning different documents in the same collection can have different fields.

![image](https://github.com/user-attachments/assets/47fb5fb0-e27e-49d8-a84c-917cfdf871d4)

![image](https://github.com/user-attachments/assets/76b0f9c8-f8a1-426e-aa94-125e17c1bd2b)

![image](https://github.com/user-attachments/assets/89c245fd-65ae-4513-9f2f-9faba2616814)

![image](https://github.com/user-attachments/assets/6c939bab-39c7-40b2-afcf-878305730e65)

## Advantages of using MongoDB:

- 1. **Flexible Schema**: MongoDB uses a flexible schema model where documents in a collection can have different structures. This allows for easy adjustments to data models as requirements evolve.
- 2. **Scalability**: MongoDB supports horizontal scaling through sharding, which distributes data across multiple servers. This makes it easier to handle large volumes of data and high traffic loads.
- 3. **Performance**: MongoDB’s in-memory processing and indexing mechanisms allow for fast data retrieval and efficient querying.
- 4. **Document-Oriented**: Data is stored in a JSON-like format (BSON), making it easy to represent complex data structures and nested relationships directly within documents.
- 5. **High Availability**: MongoDB provides built-in replication and failover mechanisms through replica sets. This ensures high availability and data redundancy.
- 6. **Rich Query Language**: MongoDB supports a powerful query language that allows for complex queries, aggregations, and indexing.
- 7. **Easy Integration**: MongoDB integrates well with various programming languages and frameworks, making it easy to use in diverse tech stacks.
- 8. **Real-Time Data Processing**: MongoDB’s ability to handle real-time data feeds and its support for various data formats make it suitable for real-time analytics and applications.
- 9. **Built-In Tools**: MongoDB offers tools like MongoDB Atlas for cloud deployments, MongoDB Compass for GUI-based interactions, and a wide range of connectors for data integration.
- 10. **Community and Ecosystem**: MongoDB has a large community and extensive ecosystem of libraries, tools, and support resources, making it easier to find help and resources.
