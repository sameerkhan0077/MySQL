### 1. Name of all students jinhone abi tak koi fees deposit ni ki

```sql
SELECT * FROM students s left join fees f ON  s.studentid =f.fstudentid where fstudentid is null;
```
