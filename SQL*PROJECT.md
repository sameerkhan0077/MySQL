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
`Name` varchar(255) not null,
`FatherName` varchar(255) not null,
`MobileNumber` bigint not null,
`Email_Address` varchar(255) not null,
`Gander` varchar(155) not null,
`AdmissionDate` date not null
);

```
  #  create table Address
  ```sql
  create table `Address`(
`Id` integer unsigned primary key not null auto_increment,
`PlotNo` integer not null,
`Colont` varchar(255) not null,
`city` varchar(255) not null,
`state` varchar(255) not null,
`PinCode` integer  not null,
`studentid` int unsigned,
 CONSTRAINT FK_StudentId FOREIGN KEY (studentid)
	REFERENCES Student(studentid)
);
```

# create table fees
```sql
create table `fees`(
`Id` integer unsigned primary key not null auto_increment,
`amount`integer,
`month`  varchar (155),
`Fstudentid` int unsigned ,
 CONSTRAINT FK_FStudentId FOREIGN KEY (Fstudentid)
	REFERENCES students(studentId)

);
```
# create table TestTable

```sql
create table `TestTable`(
`Testid` integer unsigned primary key not null auto_increment,
`Testname` varchar (215),
`Passingmarks` integer not null,
`Totalmarks` integer not null,
`Testdate` date not null,
`TStudentId` integer unsigned,
 CONSTRAINT FK_TStudentId FOREIGN KEY (TStudentId)
	REFERENCES Students(Studentid)
);
```

# create  table result

```sql
    create table `result`(
`Resultid` integer unsigned  not null auto_increment ,
`TotalMarks` integer not null,
`ObtainedMarks` integer not null,
`Result` varchar(155) not null,
`TestId` integer,
`studentId` integer,
primary key(Resultid,TestId,studentId)
);
```
#  create table Course 

 ```sql
 create table `Course`(
`Id` integer unsigned primary key not null auto_increment,
`Name` varchar(255) not null,
`fee` integer  not null,
`StartDate` date not null,
`EndDate` date not null,
`Time` time not null,
`Cstudentid` int unsigned ,
 CONSTRAINT FK_cStudentId FOREIGN KEY (Cstudentid)
	REFERENCES students(studentId)
);
```

#  create table studentCourse

```sql
create table `studentCourse`(
`studentCourseId` integer unsigned  not null auto_increment,
`studentId` integer,
`courseId` integer,
primary key(studentCourseId,studentId,courseId)
);
```

#  create table Employee

```sql
create table `Employee`(
`EmployeeId` integer unsigned primary key  auto_increment ,
`EmployeeName` varchar(215) not null,
`EmployeeType` integer ,
`EmployeeTypeId` INTEGER unsigned,
CONSTRAINT FK_ETypeId foreign key(EmployeeTypeId) REFERENCES EmployeeType(EmployeeTId)
);
```

#  CREATE TABLE EmployeeType
```sql
CREATE TABLE `EmployeeType`(
EmployeeTId INTEGER UNSIGNED PRIMARY KEY AUTO_INCREMENT,
EmployeeType VARCHAR(155) NOT NULL
);

```




