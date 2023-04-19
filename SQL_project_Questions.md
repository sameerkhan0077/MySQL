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
```sql
SELECT s.name, t.Testname, r.TotalMarks, t.Passingmarks, r.ObtainedMarks, 
r.Result FROM students s
JOIN result r ON s.studentId = r.studentId  
JOIN testtable t ON s.studentId = t.Testid  AND t.Passingmarks > r.ObtainedMarks;
```


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
```sql

### 12. Vo course btana hai jisme sbse jyada income hui hai 
### 13. Vo course btana hai jisme sbse kam income hui hai 
### 14. Kaunsa course hai jisme sbse jyada students hai 
### 15. Kaunsa course hai jisme sbse kam students hain

#   # Test 2

### 1.Kaunsa course hai jisme koi admission ni hua hai
```sql
select c.name from course c left  join studentCourse s on c.id =s.courseId  where s.courseId  is null  group by c.name ;
```

### 2. Sbse jyada expense from expense table kis chiz ke liye hua hai 
```sql
select InstitueExpenses.expenseDetail, sum(ExpensesAmount) as max_Expenses from InstitueExpenses GROUP BY InstitueExpenses.expenseDetail ORDER BY max_Expenses DESC LIMIT 1;
```


### 3. Employee list print krvani hai unki total paid salary ke descending order me
```sql
select e.EmployeeName ,e.EmployeeWork,sum(amount) as totaleAmount from
 employee e join salary s on e.EmployeeId = s.EmployeeId group by e.EmployeeName ,e.EmployeeWork order by totaleAmount desc;

 ```
### 4. Course table ko alter krna hai aur usme ek teacherid column add krna hai jo ki foreign key hogi 
``` sql
ALTER TABLE Course
ADD EmployeeId integer not null ,add
FOREIGN KEY(EmployeeId) REFERENCES Employee(Employeeid);
```

### 5. Kaunse course me kaunsa teacher pdhata hai uski detail print krvani hai 


 ### 6. Student list print krvani hai unki total paid fees ke descending order me

```sql
select s.name ,sc.courseId,sum(amount)as totale from students s 
join studentCourse sc on s.studentid = sc.studentid 
join fees f on f.fstudentid = s.studentid
group by s.name ,sc.courseId order by totale desc;
```


### 7. Kisi b year ka total profit/loss btana hai
```sql

select (select sum(amount) from fees WHERE YEAR(months) )-(
(select sum(amount) from salary WHERE YEAR(months) )+
(select sum(ExpensesAmount) from institueexpenses WHERE YEAR(months))) as total_amount ;
```

### 8. Student count list print krvani hai unki total batch count ke descending order me

```sql
SELECT Course.name, Course.time,Course.StartDate,Course.EndDate,COUNT(students.studentId) AS total_student FROM students 
JOIN studentCourse ON students.studentId = studentCourse.studentId 
JOIN Course ON Course.Id = studentCourse.courseId GROUP BY course.name,Course.time,Course.StartDate,Course.EndDate ORDER BY total_student DESC ;
```

### 9. Student list print krvani hai unki total student in pincode ke descending order me?
```sql
select Address.pincode, Address.colont,count(students.studentid) as totale from Address 
join students on Address.studentid =students.studentid  GROUP BY  Address.pincode, Address.colont order by totale desc;
```

### 10. Ek view bnana hai.
-StudentName Mobie Email CourserName CourseStartDate CourseEndDate Time TotalFees AvgMarks Address(plotno, colony, city, state, pincode)


```sql
CREATE VIEW StudentRecord AS
select s.name,s.Mobile_Number,s.Email_Address,ad.plotNo, ad.Colont, ad.city, ad.state, ad.pincode,
c.Name as namec, c.StartDate, c.endDate, c.Time, SUM(f.amount) AS totalFee, AVG(r.obtainedMarks) AS AvgMarks from students s 
LEFT join studentcourse sc  on  s.studentId  =sc.studentId 
LEFT join course c on c.id  = sc.courseId 
LEFT join address ad on ad.studentid = s.studentid
LEFT join fees f on  f.Fstudentid = s.studentId 
LEFT join result r on  r.studentId =s.studentId
GROUP BY  s.name, s.Mobile_Number, s.Email_Address, c.name, c.StartDate, c.endDate, c.time, ad.plotNo, ad.Colont, ad.city, ad.state, ad.pincode,
f.amount ;
```
### 11. Ek view result pr bnana hai 
- StudentName Mobile TotalMakrs TotalOBtainedMarks Avg Rank
- Sajid 945655445 500 400 80 1
```sql
CREATE VIEW student_result_Record AS
SELECT s.name,s.Mobile_Number,r.TotalMarks,avg(r.ObtainedMarks) as avgmark from students s
 left join result r on s.studentid = r.studentid group by s.name,s.Mobile_Number,r.TotalMarks, r.ObtainedMarks  ORDER BY avgmark DESC;
```
### 12. Vo student jinhone koi b fees jama ni krayi hai unko delete kr dena hai student table se Aur iske child records Address, Result tables me hai vo vha se b delete krna hai 
```sql
SELECT * FROM students s WHERE s.studentId NOT IN (SELECT fstudentId FROM Fees);
DELETE FROM result WHERE studentId in (6,9,10 );
DELETE FROM result WHERE studentId in (6,9,10 );
```
### 13. Expenses table se monthly expenses descending order me btane hai 
- Year Month TotalExpenses
- 2023 Feb 25000
- 2022 Dec 12000
```SQL
SELECT YEAR(institueexpenses.ExpenseDate) AS Year, MONTH(institueexpenses.ExpenseDate) AS month, SUM(ExpensesAmount) AS total_expense from institueexpenses GROUP BY Year,Month;
```
### 14. Kaunse teacher ke batch ke students ki performance sbse best hai 

### 15. ek view bnana hai
- TeacherName 
- BatchName
- BatchStartDate 
- BatchEndDate 
- Designation 
- TotalFeesDepositByThisBatch  
- TotalSalary
```SQL
CREATE VIEW teacherRecord AS
SELECT e.employeeName, c.courseName, c.startDate, c.endDate, e.employeeWork, 
SUM(f.amount) AS This_Batch, SUM(sa.amount) AS total_salary 
FROM employee e JOIN course c ON c.teacherId = e.employeeId
JOIN studentCourse sc ON sc.courseId = c.courseId
JOIN student s ON s.studentId = sc.studentId  
JOIN Fee f on f.studentId = s.studentId
JOIN salary sa ON sa.employeeId = e.employeeId
GROUP BY e.employeeName, c.courseName, c.startDate, c.endDate, e.employeeWork;
```
