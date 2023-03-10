# SQL Asssignment
### <ins> Creating the database first:  </ins>
 > CREATE table EmployeeInfo( 
> EmpID serial primary key,   
> EmpFname varchar(20) not null,   
> EmpLname varchar(20) not null,   
> Department varchar(10),    
> Project varchar(10),   
> Address varchar(50),   
> DOB date,   
> Gender varchar(2)  	 
> ); 

> CREATE table EmployeePosition(   
> EmpID int,   
> EmpPosition varchar(20),   
> DateofJoining date,   
> Salary int,   
> CONSTRAINT fk_employeeinfo   
> FOREIGN KEY(EmpID)    
> REFERENCES employeeinfo(EmpID)   
> );  

### <ins>  Inserting the data in tables : </ins>

> INSERT INTO EmployeeInfo(EmpFname,EmpLname,Department,Project,Address,DOB,Gender)   
> VALUES('Sanjay','Mehra','HR','P1','Hyderabad(HYD)','21/12/1976','M'),   
> ('Ananya','Mishra','Admin','P2','Delhi(DEL)','02/05/1968','F'),   
> ('Rohan','Diwan','Account','P3','Mumbai(BOM)','01/01/1980','M'),   
> ('Soniya','Kulkarni','HR','P1','Hyderabad(HYD)','02/05/1992','F'),   
> ('Ankit','Kapoor','Admin','P2','Delhi(DEL)','03/07/1994','M');   

> INSERT INTO EmployeePosition(EmpPosition,DateofJoining,Salary)   
> VALUES('Manager','01/05/2022',500000),   
> ('Executive','02/05/2022',75000),   
> ('Manager','01/05/2022',90000),   
> ('Lead','02/05/2022',85000),   
> ('Executive','01/05/2022',300000);  

#### <ins> Question 1 </ins>

> Write a query to fetch the number of employees working in the department ‘Admin’: 

> <ins>Query:</ins> 
>
> **SELECT COUNT(*)  
> FROM employeeinfo 
> WHERE department='Admin'** 

* Here COUNT() function is used in SELECT function to return the number of employees working in Admin department. 
* The COUNT() function is an aggregate function that allows you to get the number of rows that match a specific condition of a query. 

#### <ins> Question 2</ins>
> Write a query to retrieve the first four characters of  EmpLname from the EmployeeInfo table. 

> <ins>Query:</ins> 
> 
> **SELECT LEFT(EmpLname,4) 
> FROM employeeinfo;**

* The PostgreSQL LEFT() function returns the first n characters in the string.

#### <ins> Question 3</ins>
> Write a query to find all the employees whose salary is between 50000 to 100000.  

> <ins>Query:</ins>  
>
> **SELECT *  
> FROM employeeposition 
> WHERE salary>=50000 AND salary<=100000;** 

#### <ins> Question 4</ins>
> Write a query to find the names of employees that begin with ‘S’. 

> <ins>Query:</ins>   
>
> **SELECT *  
> FROM employeeinfo 
> WHERE empfname LIKE 'S%' ;** 

* Apart from this if we want to make the search case insensitive, we can use the ILIKE as well. 

#### <ins> Question 5 </ins>
> Write a query to fetch top N records order by salary. (ex. top 5 records).   
  
> <ins>Query:</ins>   
> **SELECT *  
> FROM employeeposition 
> ORDER BY salary DESC  
> LIMIT 3;**  
* LIMIT restricts the number of outputs a query returns.   
* LIMIT is not used as an SQL standard  practice, instead FETCH is used.  

#### <ins> Question 6</ins>
> Write a query to fetch details of all employees excluding the employees with first names, “Sanjay” and “Sonia” from the EmployeeInfo table.     

> <ins>Query: </ins>   
> **SELECT *  
> FROM employeeinfo 
> WHERE empfname NOT IN('Sanjay','Soniya');**

#### <ins> Question 7</ins>
> Write a query to fetch the department-wise count of employees sorted by department’s count in ascending order.   

> <ins>Query:</ins>   
> 
> **SELECT count(*)as total,department  
> FROM employeeinfo 
> GROUP BY department 
> ORDER BY total;** 

#### <ins> Question 8</ins>
> Create indexing for any particular field and show the difference in data fetching before and after indexing.   

> <ins>Query:</ins>   
> 
> **CREATE INDEX idx_empid ON employeeinfo(empid);**
* To find the difference between an indexed column and non-indexed column we make the use of EXPLAIN clause. 

> EXPLAIN SELECT *  
> FROM employeeinfo 
> WHERE empid=3; 

* On examining the results closely, we find that the time cost reduces when we apply index on a particular column. 

