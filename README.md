# SQL_DB_Assignment

# Creating Table EmployeeInfo :

CREATE TABLE EmployeeInfo ( <br>
  EmpID Serial NOT NULL PRIMARY KEY, <br>
  EmpFname varchar(20) NOT NULL, <br>
  EmpLname varchar(20) NOT NULL, <br>
  Department varchar(20) NOT NULL, <br>
  Project varchar(20) NOT NULL, <br>
  Address varchar(100) NOT NULL, <br>
  DOB date NOT NULL, <br>
  Gender Char(1) <br>
);

<h3> Output of Table EmployeeInfo:</h3>

https://simformsolutionspvtltd-my.sharepoint.com/:i:/r/personal/dhruvi_p_simformsolutions_com/Documents/DB_Practical/2023-03-16.png?csf=1&web=1&e=sevseF

## Adding Data in the Values:

INSERT INTO <br>
EmployeeInfo(EmpFname,EmpLname,Department,Project,Address,DOB,Gender) <br>
VALUES <br>
  ('Sanjay','Mehra','HR','P1','Hyderabad(HYD)','01/12/1976','M'), <br>
  ('Ananya','Mishra','Admin','P2','Delhi(DEL)','02/05/1968','F'), <br>
  ('Rohan','Diwan','Account','P3','Mumbai(BOM)','01/01/1980','M'), <br>
  ('Sonia','Kulkarni','HR','P1','Hyderabad(HYD)','02/05/1992','F'), <br>
  ('Ankit','Kapoor','Admin','P2','Delhi(DEL)','03/07/1994','M'); 

<h3> Output of Table EmployeeInfo: </h3>

https://simformsolutionspvtltd-my.sharepoint.com/:i:/r/personal/dhruvi_p_simformsolutions_com/Documents/DB_Practical/2023-03-16%20(1).png?csf=1&web=1&e=wrxnGS

# Creating Table EmployeePosition :

CREATE TABLE EmployeePosition ( <br>
  EmpID serial NOT NULL, <br>
	EmpPosition varchar(20) NOT NULL, <br>
  DateofJoining date NOT NULL, <br>
	Salary integer NOT NULL, <br>
	CONSTRAINT fk_EmployeeInfo <br>
	FOREIGN KEY(EmpID) <br>
	REFERENCES EmployeeInfo(EmpID) <br>
);

<h3> Output of Table EmployeePosition: </h3>

https://simformsolutionspvtltd-my.sharepoint.com/:i:/r/personal/dhruvi_p_simformsolutions_com/Documents/DB_Practical/2023-03-16%20(2).png?csf=1&web=1&e=bit96O

## Adding Data in the Values:

INSERT INTO <br>
EmployeePosition(EmpPosition,DateofJoining,Salary) <br>
VALUES <br>
	('Manager','01/05/2022','500000'), <br>
	('Executive','02/05/2022','75000'), <br>
	('Manager','01/05/2022','90000'), <br>
	('Lead','02/05/2022','85000'), <br>
	('Executive','01/05/2022','300000');
  
 <h3> Output of Table EmployeePosition:  </h3>
  
https://simformsolutionspvtltd-my.sharepoint.com/:i:/r/personal/dhruvi_p_simformsolutions_com/Documents/DB_Practical/2023-03-16%20(3).png?csf=1&web=1&e=EoLopU

# Question 1

# Write a query to fetch the number of employees working in the department ‘Admin’.

SELECT COUNT(*) FROM EmployeeInfo <br>
where Department = 'Admin';

* The COUNT() function is an aggregate function that allows you to get the number of rows that match a specific condition of a query.
* The COUNT() function returns the number of records returned by a select query.
* Here, COUNT() is used in select to count the numbers of employees working in Admin department.

 <h3> Output of the Query: </h3>

https://simformsolutionspvtltd-my.sharepoint.com/:i:/r/personal/dhruvi_p_simformsolutions_com/Documents/DB_Practical/2023-03-16%20(4).png?csf=1&web=1&e=xrAV79

# Question 2

# Write a query to retrieve the first four characters of  EmpLname from the EmployeeInfo table.

SELECT SUBSTR(EmpLname,1,4) AS FirstFourCharacter <br>
FROM EmployeeInfo;

* The SUBSTR() function extracts a substring from a string (starting at any position).
* The PostgreSQL substr() function is used to extract a specific number of characters from a particular position of a string. 
* substr(<string>,<position_from > [,<number_of_characters>])

<h3> Output of the Query: </h3>

https://simformsolutionspvtltd-my.sharepoint.com/:i:/r/personal/dhruvi_p_simformsolutions_com/Documents/DB_Practical/2023-03-16%20(5).png?csf=1&web=1&e=gTaI6x

# Question 3

# Write q query to find all the employees whose salary is between 50000 to 100000.

SELECT <br>
Emp_Info.EmpID,Emp_Info.EmpFname,Emp_Info.EmpLname,Emp_Pos.Salary <br>
FROM EmployeeInfo Emp_Info <br>
FULL OUTER JOIN EmployeePosition Emp_Pos <br>
ON Emp_Info.EmpID = Emp_Pos.EmpID <br>
WHERE Emp_Pos.Salary BETWEEN 50000 AND 100000;

* The PostgreSQL FULL OUTER JOIN or FULL JOIN creates the result-set by combining the result of both LEFT JOIN and RIGHT JOIN.

<h3> Output of the Query: </h3>

https://simformsolutionspvtltd-my.sharepoint.com/:i:/r/personal/dhruvi_p_simformsolutions_com/Documents/DB_Practical/2023-03-16%20(6).png?csf=1&web=1&e=Lh3qmv

# Question 4

# Write a query to find the names of employees that begin with ‘S’.

SELECT EmpFname,EmpLname <br>
FROM EmployeeInfo <br>
WHERE EmpFname LIKE 'S%';

* The PostgreSQL LIKE operator is used to match text values against a pattern using wildcards.
* We can have also name where the s in middle by like '%S%'.

<h3> Output of the Query: </h3>

https://simformsolutionspvtltd-my.sharepoint.com/:i:/r/personal/dhruvi_p_simformsolutions_com/Documents/DB_Practical/2023-03-16%20(7).png?csf=1&web=1&e=EYaoQw

# Question 5

# Write a query to fetch top N records order by salary. (ex. top 5 records)

SELECT  <br>
Emp_Info.EmpId,Emp_Info.EmpFname,Emp_Info.EmpLname,Emp_Info.Department,Emp_Pos.EmpPosition,Emp_Pos.Salary <br>
FROM EmployeeInfo Emp_Info FULL OUTER JOIN EmployeePosition Emp_Pos <br>
ON Emp_Info.EmpID = Emp_Pos.EmpID <br>
ORDER BY Emp_Pos.Salary;

* The ORDER BY clause allows you to sort rows returned by a SELECT clause in ascending or descending order based on a sort expression.

<h3> Output of the Query: </h3>

https://simformsolutionspvtltd-my.sharepoint.com/:i:/r/personal/dhruvi_p_simformsolutions_com/Documents/DB_Practical/2023-03-16%20(8).png?csf=1&web=1&e=YTMBL4

# Question 6

# Write a query to fetch details of all employees excluding the employees with first names, “Sanjay” and “Sonia” from the EmployeeInfo table.

SELECT * FROM EmployeeInfo <br>
WHERE EmpFname NOT IN ('Sanjay','Sonia');

* The NOT IN operator filters the query results and returns all the values of a result set except the specified values.

<h3> Output of the Query: </h3>

https://simformsolutionspvtltd-my.sharepoint.com/:i:/r/personal/dhruvi_p_simformsolutions_com/Documents/DB_Practical/2023-03-16%20(9).png?csf=1&web=1&e=ByAywf

# Question 7

# Write a query to fetch the department-wise count of employees sorted by department’s count in ascending order.

SELECT COUNT(*) AS EmployeeCount,Department <br>
FROM EmployeeInfo <br>
GROUP BY Department <br>
ORDER BY EmployeeCount;

* Here, i have used count() ,and 2 clause group by and order by. Count() is used for counting the employee by department and group it bby using clause (group by).
* Order by is used for ascending the group of employees.

<h3> Output of the Query: </h3>

https://simformsolutionspvtltd-my.sharepoint.com/:i:/r/personal/dhruvi_p_simformsolutions_com/Documents/DB_Practical/2023-03-16%20(10).png?csf=1&web=1&e=sZzJJT

# Question 8

# Create indexing for any particular field and show the difference in data fetching before and after indexing.

CREATE INDEX salary_index  <br>
ON EmployeePosition(Salary);

<h3> Output of the Query: </h3>

https://simformsolutionspvtltd-my.sharepoint.com/:i:/r/personal/dhruvi_p_simformsolutions_com/Documents/DB_Practical/2023-03-16%20(18).png?csf=1&web=1&e=Jp51eO

*  By examining the results closely ,we find that the total time cost reduces when we apply index on a particular column.

<h3> Before Index: </h3>

https://simformsolutionspvtltd-my.sharepoint.com/:i:/r/personal/dhruvi_p_simformsolutions_com/Documents/DB_Practical/2023-03-16%20(17).png?csf=1&web=1&e=gzQEJ4

<h3> After Index: </h3>

https://simformsolutionspvtltd-my.sharepoint.com/:i:/r/personal/dhruvi_p_simformsolutions_com/Documents/DB_Practical/2023-03-16%20(19).png?csf=1&web=1&e=JTY3IQ

* Here we can see that after Index apply on salary we reduces the total time cost from 20.38 msecs to 1.06 msecs.
* We can see clear large difference in the huge amount of data.
