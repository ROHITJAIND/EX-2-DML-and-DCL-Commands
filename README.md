# EX-02 Data Manipulation Language (DML) Commands and built in functions in SQL
### AIM:
To create a manager database and execute DML queries using SQL.&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;  **DATE :** 22.08.2023
### DML(Data Manipulation Language)
<div align="justify">
The SQL commands that deal with the manipulation of data present in the database belong to DML or Data Manipulation Language and this includes most of the SQL statements. It is the component of the SQL statement that controls access to data and to the database. Basically, DCL statements are grouped with DML statements.
</div>

### List of DML commands: 
<div align="justify">
INSERT: It is used to insert data into a table.<br>
UPDATE: It is used to update existing data within a table.<br>
DELETE: It is used to delete records from a database table.<br>
</div>

#### Create the table as given below:
```sql
create table manager(enumber number(6),ename char(15),salary number(5),
                      commission number(4),annualsalary number(7),Hiredate date,
                      designation char(10),deptno number(2),reporting char(10));
```
#### insert the following values into the table
```sql
insert into manager values(7369,'Dharsan',2500,500,30000,'30-June-81','clerk',10,'John');
insert into manager values(7839,'Subu',3000,400,36000,'1-Jul-82','manager',null,'James');
insert into manager values(7934,'Aadhi',3500,300,42000,'1-May-82','manager',30,NULL);
insert into manager values(7788,'Vikash',4000,0,48000,'12-Aug-82','clerk',50,'Bond');
```

#### Q1) Update all the records of manager table by increasing 10% of their salary as bonus.
##### QUERY:
```SQL
update manager set salary=salary+(salary*0.10);
```
##### OUTPUT:
![Screenshot 2023-09-29 095934](https://github.com/ROHITJAIND/EX-2-DML-and-DCL-Commands/assets/118707073/ac349853-810d-4b8d-921c-5b55bced423d)

#### Q2) Delete the records from manager table where the salary less than 2750.
##### QUERY:
```SQL
delete from manager where salary<2750;
```
##### OUTPUT:
![Screenshot 2023-09-29 095934](https://github.com/ROHITJAIND/EX-2-DML-and-DCL-Commands/assets/118707073/ac349853-810d-4b8d-921c-5b55bced423d)

#### Q3) Display each name of the employee as “Name” and annual salary as “Annual Salary” (Note: Salary in emp table is the monthly salary)
<table>
<tr>
<td>

##### QUERY:
```SQL
select ename as "Name",salary*12 as "Annual salary" from manager;
```
</td>
<td>

  
##### OUTPUT:
<img src="https://github.com/ROHITJAIND/EX-2-DML-and-DCL-Commands/assets/118707073/5b6e495d-cd34-4874-91a3-b600f0e9927c">
</td>
</tr>
</table>


#### Q4)	List the names of Clerks from emp table.

<table>
<tr>
<td>

##### QUERY:
```SQL
select ename from manager where designation='clerk';
```      
</td>
<td>

##### OUTPUT:
![Screenshot 2023-09-29 143006](https://github.com/ROHITJAIND/EX-2-DML-and-DCL-Commands/assets/118707073/5070a252-e3ff-472c-9199-da5122711f0a)

</td>
</tr>
</table>

#### Q5)	List the names of employee who are not Managers.

<table>
<tr>
<td>

##### QUERY:
```SQL
select ename from manager where designation <> 'manager';
```
</td>
<td>
  
##### OUTPUT:
![Screenshot 2023-09-29 143006](https://github.com/ROHITJAIND/EX-2-DML-and-DCL-Commands/assets/118707073/863de69e-6b90-480d-9ca9-cdd271a25317)
</td>
</tr>
</table>

#### Q6)	List the names of employees not eligible for commission.

<table>
<tr>
<td>

##### QUERY:
```SQL
select ename from manager where commission=0;
```      
</td>
<td>
  
##### OUTPUT:
<img src="https://github.com/ROHITJAIND/EX-2-DML-and-DCL-Commands/assets/118707073/623b874c-2071-4209-a7e0-117c1beb8c72">
</td>
</tr>
</table>


#### Q7)	List employees whose name either start or end with ‘s’.

<table>
<tr>
<td>
  
##### QUERY:
```SQL
select ename from manager where ename like '%S' or ename like 'S%';
```      
</td>
<td>
  
##### OUTPUT:
<img src="https://github.com/ROHITJAIND/EX-2-DML-and-DCL-Commands/assets/118707073/078a17cd-e22c-4350-9742-f8a7647dc178">
</td>
</tr>
</table>

#### Q8) Sort emp table in ascending order by hire-date and list ename, job, deptno and hire-date.

<table>
<tr>
<td>

##### QUERY:
```SQL
select ename,designation as "job",deptno,hiredate
from manager order by hiredate asc;
```
      
</td>
<td>

 
##### OUTPUT:
![image](https://github.com/ROHITJAIND/EX-2-DML-and-DCL-Commands/assets/118707073/14986921-48ae-4049-92a0-7dd1c7d89fe6) 
</td>
</tr>
</table>


#### Q9) List the Details of Employees who have joined before 30 Sept 81.
##### QUERY:
```SQL
select * from manager where hiredate<to_date('1981-09-30','YYYY-MM-DD');
```
##### OUTPUT:
![271218808-e43e7182-4761-4e64-b432-0ae4ed69e8b4](https://github.com/ROHITJAIND/EX-2-DML-and-DCL-Commands/assets/118707073/eff2e40c-7097-4719-be3e-9c0876735870)

#### Q10)	List ename, deptno and sal after sorting emp table in ascending order by deptno and then descending order by sal.

<table>
<tr>
<td>

      
##### QUERY:
```SQL
select ename,deptno,salary from manager
  order by deptno asc,salary desc;
```
</td>
<td>
  
##### OUTPUT:
<img src="https://github.com/ROHITJAIND/EX-2-DML-and-DCL-Commands/assets/118707073/1eca19e0-48ee-428b-b0bf-12ee0cf74591">
</td>
</tr>
</table>

#### Q11) List the names of employees not belonging to dept no 30,40 & 10

<table>
<tr>
<td>

##### QUERY:
```SQL
select ename from manager where deptno not in (30,40,10);
```

</td>
<td>
 
##### OUTPUT:
<img src="https://github.com/ROHITJAIND/EX-2-DML-and-DCL-Commands/assets/118707073/7e00adfe-60cc-49a0-9fdd-b48f6e46fd12"> 
</td>
</tr>
</table>


#### Q12) Find number of rows in the table EMP

<table>
<tr>
<td>

##### QUERY:
```SQL
select count(*) from manager;
```      
</td>
<td>
  
##### OUTPUT:
<img src="https://github.com/ROHITJAIND/EX-2-DML-and-DCL-Commands/assets/118707073/0a17316a-35d0-48ae-9957-5c10307369b3">
</td>
</tr>
</table>



#### Q13) Find maximum, minimum and average salary in EMP table.

<table>
<tr>
<td>
  
##### QUERY:
```SQL
select max(salary) from manager;
select min(salary) from manager;
select avg(salary) from manager;
```
      
</td>
<td>
 
##### OUTPUT:
![Screenshot 2023-09-29 144349](https://github.com/ROHITJAIND/EX-2-DML-and-DCL-Commands/assets/118707073/0c027aff-f837-4cf1-8214-0e1091674f71) ![Screenshot 2023-09-29 144403](https://github.com/ROHITJAIND/EX-2-DML-and-DCL-Commands/assets/118707073/38b2cd4c-eabc-442b-8fd1-bcadb2612961) ![Screenshot 2023-09-29 144327](https://github.com/ROHITJAIND/EX-2-DML-and-DCL-Commands/assets/118707073/c3e23cad-1f65-4c2d-8746-db12f84b5ab3) 
</td>
</tr>
</table>

#### Q14) List the jobs and number of employees in each job. The result should be in the descending order of the number of employees.
<table>
<tr>
<td>

##### QUERY:
```SQL
SELECT designation AS job, COUNT(*) AS num_employees
  FROM manager GROUP BY designation ORDER BY num_employees DESC;
```      
</td>
<td>
 
##### OUTPUT:
<img src="https://github.com/ROHITJAIND/EX-2-DML-and-DCL-Commands/assets/118707073/faa78ae1-0a9c-4888-b5f5-72213d0833ab"> 
</td>
</tr>
</table>


### RESULT:
To create a manager database and execute DML queries using SQL is executed successfully.
