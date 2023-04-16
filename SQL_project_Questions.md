### 1. Name of all students jinhone abi tak koi fees deposit ni ki?

```sql
SELECT * FROM students s left join fees f ON  s.studentid =f.fstudentid where fstudentid is null;
```
### 2. Sbse jyada fees kis student ne di hai. naam btao?
```sql
SELECT s.name, SUM(amount) AS total FROM students s JOIN fees f ON s.studentid IN (f.fstudentid) GROUP BY s.name ORDER BY total DESC LIMIT 1;;

```
### 3. Sbse jyada fees me 2nd number pr jo student hai uska naam btao ?
```sql
SELECT s.name, SUM(amount) AS total FROM students s JOIN fees f ON s.studentid IN (f.fstudentid)  GROUP BY s.name ORDER BY total DESC LIMIT 2;
```
### 4. Coaching me total kitne employees hain unka naam and designation/role show krvao?
```sql
SELECT COUNT(*), employeeName, employeeWork FROM employee GROUP BY employeeName, employeeWork;
```
### 5. Kis employee ne kitni salary uthayi hai ab tak vo btao ya month wise
```sql
SELECT employeeName, SUM(amount) FROM employee JOIN salary ON employee.employeeId = salary.employeeId GROUP BY employeeName;
```
### 6.Vo sare students jo abi tak 1 b test me fail hue hai unka naam, subject, totalmarks, passingmarks, obtainedmarks btao   


### 7. Particular month ka kharcha btao. Kharche me tume salary and expenses dono add krne hai ?

```sql
select( select sum(amount) from salary where month(date)=3)+
(select sum(ExpensesAmount) from InstitueExpenses where month(ExpenseDate)=4)as total_amount;
```

### 8. Particular month me total income btao 
```sql
select sum(amount) from fees where month(depositDate)=4 ;
```

### 9. Total income aaj tak 
```sql
select sum(amount) as totle from fees;
```
### 10. Total kharche aaj tak 
```sql
select sum(ExpensesAmount) as totaleExpenses from  InstitueExpenses;
```
### 11.Kis course me kitne students hai vo btane hai coursename startdate time totalstudents
### 12. Vo course btana hai jisme sbse jyada income hui hai 
### 13. Vo course btana hai jisme sbse kam income hui hai 
### 14. Kaunsa course hai jisme sbse jyada students hai 
### 15. Kaunsa course hai jisme sbse kam students hain
### 16.Sbse jyada expense from expense table kis chiz ke liye hua hai 
```sql
select InstitueExpenses.expenseDetail, sum(ExpensesAmount) as max_Expenses from InstitueExpenses GROUP BY InstitueExpenses.expenseDetail ORDER BY max_Expenses DESC LIMIT 1;
```


### 17. Employee list print krvani hai unki total paid salary ke descending order me
Sajid Teacher 100000
Shahrukh Teacher 80000
Rehna Peon 20000
```sql
select e.EmployeeName ,e.EmployeeWork,sum(amount) as totaleAmount from
 employee e join salary s on e.EmployeeId = s.EmployeeId group by e.EmployeeName ,e.EmployeeWork order by totaleAmount desc;

 ```
### 18. Course table ko alter krna hai aur usme ek teacherid column add krna hai jo ki foreign key hogi 
``` sql
alter table Course
add column teacherid integer not null,
ADD FOREIGN KEY (teacherid) REFERENCES Employee(EmployeeId);
```

### 19.Kaunse course me kaunsa teacher pdhata hai uski detail print krvani hai CourseName CourseTime TeacherName


### 20. Kaunsa course hai jisme koi admission ni hua hai
```sql
select c.name from course c left  join studentCourse s on c.id =s.courseId  where s.courseId  is null  group by c.name ;
```
### 21.Student list print krvani hai unki total paid fees ke descending order me
```sql
select s.name ,sc.courseId,sum(amount)as totale from students s 
join studentCourse sc on s.studentid = sc.studentid 
join fees f on f.fstudentid = s.studentid
group by s.name ,sc.courseId order by totale desc;
```


### 22.Kisi b year ka total profit/loss btana hai
Total fees - (total salary + total expenses)
```sql

select (select  sum(amount) as profit_LOSS from fees )-(
(select sum(amount) as profit_LOSS from salary )+
(select sum(ExpensesAmount) as profit_LOSS from InstitueExpenses ));
```

### 23.Student count list print krvani hai unki total batch count ke descending order me
Nodejs 10:00PM 10/01/2023  10/07/2023 30
JS 9:00PM 10/01/2023  10/07/2023 20
HTML 10:00AM 10/01/2023  10/07/2023 40

### 24.Student list print krvani hai unki total student in pincode ke descending order me
302012 Jhotwara 20
303012 Merta 15
304013 Sikar 12

### 25. Ek view bnana hai. 
StudentName Mobie Email CourserName CourseStartDate CourseEndDate Time TotalFees AvgMarks Address(plotno, colony, city, state, pincode)

### 26. Ek view result pr bnana hai 
StudentName Mobile TotalMakrs TotalOBtainedMarks Avg Rank
Sajid 945655445 500 400 80 1
### 27. Vo student jinhone koi b fees jama ni krayi hai unko delete kr dena hai student table se Aur iske child records Address, Result tables me hai vo vha se b delete krna hai 

### 28.Expenses table se monthly expenses descending order me btane hai 

Year Month TotalExpenses
2023 Feb 25000
2022 Dec 12000

### 29.Kaunse teacher ke batch ke students ki performance sbse best hai 

### 30 .ek view bnana hai TeacherName BatchName BatchStartDate BatchEndDate Designation TotalFeesDepositByThisBatch  TotalSalary

