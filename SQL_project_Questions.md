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
