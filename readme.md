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
 # 46-2 limit and offset
 - limit
 
 ```
select * from students limit 3
 ```
 ```
 select * from students where age in (20,21,23) limit 5
 ```
 - offset
 ```
 select * from students limit 5 offset 2 * 0
 ```
 ```
 select * from students limit 5 offset 2 * 1
 ```
 ```
 select * from students limit 5 offset 2 * 2
 ```
# 46-3 updating data
- If we want update  whole table we can update like this..but its not a right way to update we need add a condition for a specific row or multiple row 
 ``` 
 update  students set email = 'defualt@gmail.com'
 ```
 ``` 
update students set first_name = 'Ronjina',age=26
where student_id = 2
 ```
 ``` 
update students set grade = 'B' where student_id in (1,2)
 ```
 # 46-4 Delete Data
 - If we delete data like this  entire table will be delete so need add a specific condition like which data we can be delete 
 ```
 delete from  students
 ```
 
 ```
delete from students where age > 20 and grade = 'A'

 ```
 # 46-5 group by 
 - count avarage age group by country
 ```
 select country, avg(age) from students group by country
 ```
 - count students by country
 ```
  select country, count(*) from students group by country
  ```
   - count students by grade 
  ```
  select grade, count(*) from students group by grade
  ```
  ![alt text](group%20by.png)
# 46-6 group by having 
  - courses with more than 4 students 
 ``` 
select course,count(*) from students group by course having count(*) >4
```
  - country where avarage student age is greater than 21
```
select country, avg(age) from students group by country having avg(age) > 21
```   
# practice task 
## Simple Queries
- 1 . select all users
```
select * from users
```
- 2 . Show only first name and email
```
select first_name,email from users
```
- 3.Find users older than 25
```
select * from users where age > 25
```
- 4.Count how many users are from each country
```
select country, count(*) from users group by country
```
- 5 . Find the youngest user’s age
```
select  min(age) from users
```
- 6 Find the oldest user’s age
```
select max(age) from users
```
- 7.Find the average age of all users
```
select avg(age) from users
```
- 8 List users ordered by age (youngest first)
```
select age from users order by age asc
```

## Add Some NULL Data for COALESCE Practice
- Let’s say some users don’t have an email yet:
```
INSERT INTO users (first_name, last_name, age, country, email) VALUES
('Imran', 'Haque', 26, 'Bangladesh', NULL),
('Lina',  'Begum', 23, 'India', NULL);
```
# Queries with COALESCE
- Show email, but if NULL → display "Not Provided"
```
select coalesce(email,'not provided')  as email from 
users 
```
- Count users by country, replacing NULL country with "Unknown"
```
select coalesce(country,'unknown'),count(*) from users group by country 
```
# Queries with LIMIT & OFFSET
- 1 Get the first 5 users
```
select * from users limit 5

```
- 2 Get the first 5 users
```
select * from users limit 5 offset 5*1
```
  - 3.Get the 3 youngest users
  ```
select * from users order by age asc limit 3
```