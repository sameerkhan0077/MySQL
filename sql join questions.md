 ###          SQL QUERIES  ###
 1.What is the query to get all the details of a student along with the fees and result data for the student?
 ```
 select * from student s inner join fees f on s.sudentid = f.sudentid inner join result r on r.sudentid = s.sudentid;
 ```

