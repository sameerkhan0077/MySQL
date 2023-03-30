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
### 16.What is the average marks obtained by the student with studentid = 9 for the subject of science?
```
select * from student where course ="node.js" and studentid =9;

select avg(obtainedmarks) from result where studentid = 9;

````
### 17.What is the name of the student who paid the highest amount of fees for the month of February? 
```
select studentid,sum(amount) as highestfee from fees group by studentid order by highestfee desc limit 1;

select * from student where studentid = 1;

```

### 18.What is the name of the student who obtained the highest marks in the subject of English?
```
select studentid, sum(obtainedmarks) as highestmarks from result where subject = 'english'  group by  studentid order by highestmarks desc limit 1;

SELECT * FROM result where studentid = 9;

```
### 19.What is the name of the student who paid the highest amount of fees for the subject of computer science?
```
select studentid, sum(amount) as highfee from fees where subject = 'computer science' group by studentId ORDER BY highfee desc limit 1;

select * from student where in (1,2);

```
### 20.What is the name of the student who obtained the highest marks in the subject of mathematics for the test date of '2022-02-15'?

```
select studentid,sum(obtainedmarks) as highestmarks from result where testdate ='2022-02-15' and subject = "mathematics" group by studentid order by highestmarks desc limit 1;
select * from student where studentid = 9;
```

###  21.What is the total amount of fees paid by all students whose fathers' names start with the letter 'S'?
```
select * from student where fathers like  "%s%";

select sum(amount) from fees where studentid in (1,2,3,4,7);

```
### 22. What is the average marks obtained by all students for the subject of science?
```
select studentid from result where subject ="sciences";

select avg(obtainedmarks) from result where studentid in (1,2,4,5,6);

```

### 23.What is the name of the student who paid the highest amount of fees for the year 2022?
```
select studentid,sum(amount) as totalfee from fees where month ='january' group by studentid order by totalfee desc limit 1 ;

select * from student where studentid=9;
 
 ```
 ### 24.What is the name of the student who obtained the highest marks in the subject of English for the test date of '2022-03-15'?
 ```
select studentid,sum(obtainedmarks) as highmakrs from fees where date = '2022-03-15' group by amount ORDER BY highmakrs desc limit 1;

select * from student where studentId = 10;

```
  
### 25.What is the name of the student who paid the second highest amount of fees for the subject of computer science?

```
select studentid, sum(amount) as highmaks FROM fees where subject = 'science' group BY studentid ORDER BY highmaks desc limit 2;

select * from student where studentid = 8;

```
### 26.What is the name of the student who obtained the highest marks in the subject of mathematics and science combined?
```
select studentId,SUM(obtainedMarks) as highm FROM result WHERE subject = 'mathematics' and subject = 'science.js' group BY studentid ORDER BY highm desc LIMIT 1;

select * FROM student WHERE studentid = 2;
```

### 27.What is the name of the student who paid the highest amount of fees for the month of March and the subject of English combined?

```
select studentid,sum(amount) as highfees FROM fees where subject = 'English' and month = 'march' GROUP BY studentId ORDER BY highfees desc LIMIT 1;

select * from student where studentid = 5;

```
### 28.What is the name of the student who obtained the highest marks for the test date of '2022-04-15' in any subject?

```
select studentId, obtainedMarks as highmarks from result where date = '2022-04-15' group BY studentId ORDER by highmarks desc LIMIT 1;

select * from student where studentid = 6;
```











