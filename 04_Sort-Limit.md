# Sort and Limit Data
 
1. limit
`db.people.find().limit(2)`

![image](https://github.com/user-attachments/assets/2a4e9342-a46f-41f3-b536-1154f570f51c)

Use : It is used in Pagination 
Pagination  is a technique used in database queries (and in web applications generally) to divide a large dataset into smaller, more manageable chunks or "pages." This allows users to retrieve and view a portion of the data at a time rather than loading the entire dataset in a single query.
- Achieving pagination using Mongodb find and limit

![image](https://github.com/user-attachments/assets/7b38ab04-9c96-4345-bb04-aec2dd868248)

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


