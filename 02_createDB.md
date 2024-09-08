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
- No Fixed Schema: Collections do not enforce a fixed schema. Documents within the same collection can have different sets of fields, and the data types for the same field can vary across documents.
- Dynamic Schema: You can add or remove fields from documents without having to update a central schema definition. This allows for more flexibility and faster iteration during development.
- Nested Data Structures: MongoDB supports nested documents and arrays, allowing for more complex data representations within a single document.

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

