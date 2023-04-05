 ###          SQL QUERIES  ###
 1.What is the query to get all the details of a student along with the fees and result data for the student?
 ```
 select * from student s inner join fees f on s.sudentid = f.sudentid inner join result r on r.sudentid = s.sudentid;
 ```
2. How can we retrieve the data of a student who has paid fees for the month of January?

```
select * from student s inner join fees f on s.sudentid = f.sudentid where month='january';

```
3.What is the query to get the list of all students who have not yet paid their fees?

```
select * from student s inner join fees f on s.sudentid = f.sudentid where amount is null
```
4. How can we fetch the list of students who scored more than 80 marks in any subject in the result table?
```
select * from student s  join result r on s.sudentid = r.sudentid where obtainedmarks >80;
```
5.What is the query to get the details of students along with the total amount of fees they have paid so far?
```
select sum(amount) from student s inner join fees f on s.studentid = f.studentid ;

```
6.  How can we fetch the list of all students along with their fees data and result data, even if they do not have any data in the fees or result table?
```
select * from student s join fees f  on s.studentid = f.studentid join result r on r.studentid = s.studentid;


```
7.  What is the query to get the name, email address, and mobile number of all the students who belong to the city of "Delhi"?
```
select s.name , s.email_id, s.mobile ,s.studentid from student s where s.city = 'Delhi';

```

8.  How can we retrieve the details of students who belong to the city of "Mumbai" and have paid their fees for the month of February?
```
select * from student s join fees f on s.studentid =f.studentid where s.city = 'sikar' and f.month ="january";

```


9.  What is the query to get the name, email address, and total amount of fees paid by all the students who have paid their fees?
```
select s.name,s.email_id,sum(f.amount) from student s join fees f on s.studentid = f.studentid where f.amount is not null group by s.name ,s.email_id;

```
10.  How can we fetch the details of all students who have taken any test before a specific date?
```
select * from  student s join result r on s.studentid = r.studentid where r.testdate >=10-03-2023;
```


11.  What is the query to get the name, email address, and subject name of all the students who have scored more than 90 marks in any subject?

12.  How can we retrieve the details of students who belong to the city of "Bangalore" and have scored less than 50 marks in any subject?

13.  What is the query to get the details of all students along with their fees and result data, sorted by their name in ascending order?

14.  How can we fetch the name, email address, and total amount of fees paid by all the students who have not paid their fees yet?

15.  What is the query to get the details of all students who have paid their fees for the month of March and have scored more than 70 marks in any subject?

16.  How can we retrieve the details of students who have not taken any test yet?

17.  What is the query to get the name, email address, and subject name of all the students who have scored less than 40 marks in any subject?

18.  How can we fetch the details of students who belong to the city of "Pune" and have paid their fees for the month of January?

19.  What is the query to get the name, email address, and mobile number of all the students who have not taken any test yet?

20.  How can we retrieve the details of students who have scored more than 60 marks in all the subjects they have taken tests for?
  
