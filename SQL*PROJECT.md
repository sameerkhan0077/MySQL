  # Create database
  
  ```sql
CREATE DATABASE InstitueManagement;
```
  # Use DataBase
  
  ```sql
  use InstitueManagement
  ```
  
  #  create table Students
  
  ```sql
  create table `students`(
`StudentId ` integer unsigned primary key not null auto_increment,
`Name` varchar(25) not null,
`FatherName` varchar(25) not null,
`Mobile_Number` integer not null,
`Email_Address` varchar(25) unique  not null,
`AdmissionDate` date not null
);

```
  #  create table Address
  ```sql
  create table `Address`(
`Id` integer unsigned primary key not null auto_increment,
`PlotNo` integer not null,
`Colont` varchar(25) not null,
`city` varchar(25) not null,
`state` varchar(25) not null,
`PinCode` integer  not null,
`studentid` int unsigned,
 CONSTRAINT FK_StudentId FOREIGN KEY (studentid)
	REFERENCES Student(studentid)
);
```

# create table fees
```sql
create table `fees`(
`Id` integer primary key not null auto_increment,
`amount`integer,
`depositDate` date not null ,
`Fstudentid` int unsigned ,
 CONSTRAINT FK_FStudentId FOREIGN KEY (Fstudentid)
	REFERENCES students(studentId)

);
```
# create table TestTable

```sql
create table `TestTable`(
`Testid` integer primary key auto_increment,
`Testname` varchar (25) not null,
`Passingmarks` integer not null,
`Totalmarks` integer not null,
`Testdate` date not null,
);
```

# create  table result

```sql
    create table `result`(
`Resultid` integer  not null auto_increment primary key ,
`TotalMarks` integer not null,
`ObtainedMarks` integer not null,
`Result` enum('pass' , 'fail',
`TestId` integer,
`studentId` integer,
primary key(TestId,studentId)
);
```
#  create table Course 

 ```sql
 create table `Course`(
`Id` integer unsigned primary key not null auto_increment,
`Name` varchar(25) not null,
`fee` integer  not null,
`StartDate` date not null,
`EndDate` date not null,
`Time` time not null,
);
```

#  create table studentCourse

```sql
create table `studentCourse`(
`studentCourseId` integer unsigned not null auto_increment,
`studentId` integer,
`courseId` integer,
primary key(studentCourseId,studentId,courseId)
);
```

#  create table Employee

```sql
create table `Employee`(
`EmployeeId` integer unsigned primary key  auto_increment ,
`EmployeeName` varchar(25) not null,
`EmployeeType` integer ,
`EmployeeTypeId` INTEGER unsigned,
`Employee_Email` varchar(40) unique not null,
CONSTRAINT FK_ETypeId foreign key(EmployeeTypeId) REFERENCES EmployeeType(EmployeeTId)
);
```

#  create table EmployeeType
```sql
create table `EmployeeType`(
`EmployeeTId` INTEGER UNSIGNED PRIMARY KEY AUTO_INCREMENT,
`EmployeeType` VARCHAR(20)
);

```

#  create table Salary
```sql
   create table `Salary`(
`salaryId` INTEGER UNSIGNED PRIMARY KEY AUTO_INCREMENT,
`amount` bigint not null,
`date` date not null,
`EmployeeId` integer unsigned,
CONSTRAINT fk_salaryEmploye
foreign key(EmployeeId) REFERENCES Employee(EmployeeId)
);
```

# create table InstitueExpenses
```sql
 create table`InstitueExpenses`(
`I_ExpensesId` integer unsigned  not null primary key auto_increment,
`expenseDetail` varchar (50) not null,
`ExpensesAmount` integer  not null,
`ExpenseDate` date 
);

```







