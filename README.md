# EX 2 Data Manipulation Language (DML) Commands and built in functions in SQL
## DATE: 11/8/2023
## AIM:
To create a manager database and execute DML queries using SQL.
## DML(Data Manipulation Language)
<div align="justify">
The SQL commands that deal with the manipulation of data present in the database belong to DML or Data Manipulation Language and this includes most of the SQL statements. It is the component of the SQL statement that controls access to data and to the database. Basically, DCL statements are grouped with DML statements.
</div>

## List of DML commands: 
<div align="justify">
INSERT: It is used to insert data into a table.<br>
UPDATE: It is used to update existing data within a table.<br>
DELETE: It is used to delete records from a database table.<br>
</div>

## Create the table as given below:
```sql
create table manager(enumber number(6),ename char(15),salary number(5),commission number(4),annualsalary number(7),Hiredate date,designation char(10),deptno number(2),reporting char(10));
```
## insert the following values into the table
```sql
insert into manager values(7369,'Dharsan',2500,500,30000,'30-June-81','clerk',10,'John');
insert into manager values(7839,'Subu',3000,400,36000,'1-Jul-82','manager',null,'James');
insert into manager values(7934,'Aadhi',3500,300,42000,'1-May-82','manager',30,NULL);
insert into manager values(7788,'Vikash',4000,0,48000,'12-Aug-82','clerk',50,'Bond');
```

### Q1) Update all the records of manager table by increasing 10% of their salary as bonus.
### QUERY:
`UPDATE manager SET salary = salary * 1.10;`
### OUTPUT:
![Screenshot 2023-10-04 141151](https://github.com/Priyadharshini-Er/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/119558093/ec50a0e6-6ad1-4551-bf02-eb10f6f5475d)

### Q2) Delete the records from manager table where the salary less than 2750.
### QUERY:
DELETE FROM manager WHERE salary < 2750;
### OUTPUT:
![Screenshot 2023-10-04 141203](https://github.com/Priyadharshini-Er/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/119558093/2e4287ae-414e-46c6-bd7f-0af748004537)

### Q3) Display each name of the employee as “Name” and annual salary as “Annual Salary” (Note: Salary in emp table is the monthly salary)
### QUERY:
SELECT ename AS "Name", (salary * 12) + NVL(commission, 0) AS "Annual Salary" FROM manager;
### OUTPUT:
![Screenshot 2023-10-04 141214](https://github.com/Priyadharshini-Er/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/119558093/1f059f33-95f0-46ff-8343-71a68c014a6a)

### Q4)	List the names of Clerks from emp table.
### QUERY:
SELECT ename FROM manager WHERE designation = 'clerk';
### OUTPUT:
![Screenshot 2023-10-04 141224](https://github.com/Priyadharshini-Er/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/119558093/6113a651-8391-48e4-91d5-3158b08fd12a)

### Q5)	List the names of employee who are not Managers.
### QUERY:
SELECT ename FROM manager WHERE designation != 'manager';
### OUTPUT:
![Screenshot 2023-10-04 141231](https://github.com/Priyadharshini-Er/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/119558093/40ba70cc-f8cb-4271-a575-c7e5aa9617fa)

### Q6)	List the names of employees not eligible for commission.
### QUERY:
SELECT ename FROM manager WHERE commission = 0;
### OUTPUT:
![Screenshot 2023-10-04 142831](https://github.com/Priyadharshini-Er/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/119558093/8f9d5831-3e39-438c-9e73-08062a962807)

### Q7)	List employees whose name either start or end with ‘s’.
### QUERY:
SELECT ename FROM manager WHERE ename LIKE 'S%' OR ename LIKE '%S';
### OUTPUT:
![Screenshot 2023-10-04 141241](https://github.com/Priyadharshini-Er/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/119558093/881a24ad-37ca-4d6c-afc1-7a140b64c5ef)

### Q8) Sort emp table in ascending order by hire-date and list ename, job, deptno and hire-date.
### QUERY:
SELECT ename, designation, deptno, Hiredate FROM manager ORDER BY hiredate ASC;
### OUTPUT:
![Screenshot 2023-10-04 141306](https://github.com/Priyadharshini-Er/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/119558093/d764b28e-2dd1-4eae-b95e-ca279ccf62dc)

### Q9) List the Details of Employees who have joined before 30 Sept 81.
### QUERY:
SELECT * FROM manager WHERE Hiredate < TO_DATE('30-SEP-81', 'DD-MON-YY');
### OUTPUT:
![Screenshot 2023-10-04 141317](https://github.com/Priyadharshini-Er/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/119558093/fc8f1d5b-f786-4bf5-b60f-471d33872afc)

### Q10)	List ename, deptno and sal after sorting emp table in ascending order by deptno and then descending order by sal.
### QUERY:
SELECT ename, deptno, salary FROM manager ORDER BY deptno ASC, salary DESC;
### OUTPUT:
![Screenshot 2023-10-04 141342](https://github.com/Priyadharshini-Er/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/119558093/abe84a26-9bce-4f86-9d5b-3049f1a039a8)

### Q11) List the names of employees not belonging to dept no 30,40 & 10
### QUERY:
SELECT ename FROM manager WHERE deptno NOT IN (10, 30, 40);
### OUTPUT:
![Screenshot 2023-10-04 141347](https://github.com/Priyadharshini-Er/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/119558093/86df6f23-cb53-4e3e-824e-f527ac5f5ee9)

### Q12) Find number of rows in the table EMP
### QUERY:
SELECT COUNT(*) AS "Number of Rows" FROM manager;
### OUTPUT:
![Screenshot 2023-10-04 141352](https://github.com/Priyadharshini-Er/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/119558093/f2b36f02-353d-40e9-bb68-a4385d83ddf6)


### Q13) Find maximum, minimum and average salary in EMP table.
### QUERY:
SELECT MAX(salary) AS "Maximum Salary", MIN(salary) AS "Minimum Salary", AVG(salary) AS "Average Salary" FROM manager;
### OUTPUT:
![Screenshot 2023-10-04 143301](https://github.com/Priyadharshini-Er/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/119558093/ed21ed72-afd4-432e-a850-73740c982a73)


### Q14) List the jobs and number of employees in each job. The result should be in the descending order of the number of employees.
### QUERY:
SELECT designation, COUNT(*) AS "Number of Employees" FROM manager GROUP BY designation ORDER BY COUNT(*) DESC;
### OUTPUT:
![Screenshot 2023-10-04 143358](https://github.com/Priyadharshini-Er/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/119558093/131ce569-8f53-4881-b9e2-31422dd46774)

## RESULT:
Manager database is created and DML queries are executed successsfully.
