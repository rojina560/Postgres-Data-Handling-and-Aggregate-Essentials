# Postgres data handling and aggregation essentials
In this module, you’ll learn essential data manipulation concepts in PostgreSQL. From handling NULL values with COALESCE to implementing LIMIT and OFFSET for pagination, updating and deleting records, everything is covered. You’ll also explore how to group data with GROUP BY and refine results using HAVING for deeper analysis.

## 46-1 Handling NULL with COALESCE
- null
```
 select * from students where email is  null 
 ```
- not null
```
 select * from students where email is not null 
 ```
- coalesce
```
select first_name,age,coalesce(email,'Not Provided')  as email from students
 ```