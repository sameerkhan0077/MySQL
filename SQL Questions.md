### 1 .How many students are there in the student table?
```
select count(*) from student;
```
### 2 .What is the name of the student with studentid = 5?
```
select * from student where studentid = 5 ;
```
### 3. How many students are there from the city of Mumbai?
```
select count(city) from student where city = "mumbai";
```
### 4. What is the email address of the student whose name is 'John Doe'?
```
select * from student where name like "%john doe%" ;
```
### 5.What is the total amount of fees paid by the student with studentid = 10?
```
select sum(amount) as totaleFee from fees where studentid = 10;
```
### 6.What is the highest amount of fees paid by any student?
```
  select studentid, sum(amount) as total from fees group by studentid order by total desc limit 1;
  ```
### 7.What is the average amount of fees paid by all students?
```
   select avg(amount) as totalavg from fees  ;
```
### 8.What is the name of the student who paid the highest amount of fees?
```
select studentid,sum(amount) from fees group by studentid order by amount desc limit 1;
select * from student where studentid in (1);
```
### 9.What is the total marks obtained by the student with studentid = 7?
```
   select sum(obtainedmarks)  from result where studentid =7;
```
### 10.What is the highest marks obtained by any student?
```
select studentid,sum(obtainedmarks)as highestmarks  from result group by studentid order by highestmarks desc limit 1;
```
### 11.What is the average marks obtained by all students?
```
select avg(obtainedmarks) from result;
```
### 12.What is the name of the student who obtained the highest marks?
```
select studentid,sum(obtainedmarks) as highestmarks from result group by studentid order by highestmarks desc limit 1;
select * from student where studentid = 9 ;
```
### 13.What is the total amount of fees paid by all students from the city of Delhi?
```
select (studentid) from student where city = "delhi";
select sum(amount) from fees where studentid in(1,2,3,4);
```
### 14.What is the total amount of fees paid for the month of January?
```
select sum(amount) from fees where month ='january';
```
### 15.What is the total amount of fees paid by all students for the subject of mathematics?
```
select studentid from student where course="mathematics";
select sum(amount) from fees where studentid in (1,2);
```
  












