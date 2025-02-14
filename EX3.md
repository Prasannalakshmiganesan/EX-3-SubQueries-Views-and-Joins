# EX 3 SubQueries, Views and Joins 

## Date:

## Create employee Table
```sql
CREATE TABLE EMP (EMPNO NUMBER(4) PRIMARY KEY,ENAME VARCHAR2(10),JOB VARCHAR2(9),MGR NUMBER(4),HIREDATE DATE,SAL NUMBER(7,2),COMM NUMBER(7,2),DEPTNO NUMBER(2));
```
## Insert the values
```sql
INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7369, 'SMITH', 'CLERK', 7902, '17-DEC-80', 800, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7499, 'ALLEN', 'SALESMAN', 7698, '20-FEB-81', 1600, 300, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7521, 'WARD', 'SALESMAN', 7698, '22-FEB-81', 1250, 500, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7566, 'JONES', 'MANAGER', 7839, '02-APR-81', 2975, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7654, 'MARTIN', 'SALESMAN', 7698, '28-SEP-81', 1250, 1400, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7698, 'BLAKE', 'MANAGER', 7839, '01-MAY-81', 2850, NULL, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7782, 'CLARK', 'MANAGER', 7839, '09-JUN-81', 2450, NULL, 10);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7788, 'SCOTT', 'ANALYST', 7566, '19-APR-87', 3000, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7839, 'KING', 'PRESIDENT', NULL, '17-NOV-81', 5000, NULL, 10);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7844, 'TURNER', 'SALESMAN', 7698, '08-SEP-81', 1500, 0, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7876, 'ADAMS', 'CLERK', 7788, '23-MAY-87', 1100, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7900, 'JAMES', 'CLERK', 7698, '03-DEC-81', 950, NULL, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7902, 'FORD', 'ANALYST', 7566, TO_DATE('03-DEC-81', 'DD-MON-RR'), 3000, 20, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7934, 'MILLER', 'CLERK', 7782, TO_DATE('23-JAN-82', 'DD-MON-RR'), 1300, 10, 10);
```

## Create department table
```sql
CREATE TABLE DEPT (DEPTNO NUMBER(2) PRIMARY KEY,DNAME VARCHAR2(14),LOC VARCHAR2(13));
```
## Insert the values in the department table
```sql
INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (10, 'ACCOUNTING', 'NEW YORK');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (20, 'RESEARCH', 'DALLAS');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (30, 'SALES', 'CHICAGO');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (40, 'OPERATIONS', 'BOSTON');
```

### Q1) List the name of the employees whose salary is greater than that of employee with empno 7566.


### QUERY:
 SELECT ename FROM empl WHERE sal > (SELECT sal FROM empl WHERE empno = 7566);

### OUTPUT:
![image](https://github.com/Prasannalakshmiganesan/EX-3-SubQueries-Views-and-Joins/assets/118610231/17ed4e96-cea7-4d49-9081-8d1921b459d5)


### Q2) List the ename,job,sal of the employee who get minimum salary in the company.

### QUERY:
SELECT ename, job, sal FROM empl WHERE sal = (SELECT MIN(sal) FROM empl);

### OUTPUT:
![image](https://github.com/Prasannalakshmiganesan/EX-3-SubQueries-Views-and-Joins/assets/118610231/db8f88f6-76be-4d1e-b9be-c5a5726ae446)


### Q3) List ename, job of the employees who work in deptno 10 and his/her job is any one of the job in the department ‘SALES’.

### QUERY:
SELECT ename, job FROM empl WHERE deptno = 10 AND job IN (SELECT job FROM empl WHERE job = 'sales');

### OUTPUT:
![image](https://github.com/Prasannalakshmiganesan/EX-3-SubQueries-Views-and-Joins/assets/118610231/e7d403bd-6fbb-4e31-b418-569e5268794f)


### Q4) Create a view empv5 (for the table emp) that contains empno, ename, job of the employees who work in dept 10.

### QUERY:
 CREATE VIEW emv5 AS SELECT empno, ename, job from empl WHERE deptno = 10;

### OUTPUT:
![image](https://github.com/Prasannalakshmiganesan/EX-3-SubQueries-Views-and-Joins/assets/118610231/3f065de6-3dc6-4a94-843c-375e36d2a3e4)


### Q5) Create a view with column aliases empv30 that contains empno, ename, sal of the employees who work in dept 30. Also display the contents of the view.

### QUERY:
CREATE VIEW emv30 AS SELECT empno AS "Employee Number", ename AS "Employee Name", sal AS "Salary" from empl WHERE deptno = 30;

### OUTPUT:
![image](https://github.com/Prasannalakshmiganesan/EX-3-SubQueries-Views-and-Joins/assets/118610231/cdb572b6-5a86-4cf1-8ee7-9e4609ce27d4)


### Q6) Update the view empv5 by increasing 10% salary of the employees who work as ‘CLERK’. Also confirm the modifications in emp table

### QUERY:
![270767939-d83bbdcd-83a3-427e-bd2b-e799958b055d](https://github.com/Prasannalakshmiganesan/EX-3-SubQueries-Views-and-Joins/assets/118610231/532e1c2f-2291-4305-8919-cb2d9b6ad32f)



### OUTPUT:
![270767871-6941b531-33ed-41dc-b6f4-9e8bcc0dd113](https://github.com/Prasannalakshmiganesan/EX-3-SubQueries-Views-and-Joins/assets/118610231/fbf68ff5-be7c-4f50-adb6-faafcfb032a7)


## Create a Customer1 Table
```sql
CREATE TABLE Customer1 (customer_id INT,cust_name VARCHAR(20),city VARCHAR(20),grade INT,salesman_id INT);
```
## Inserting Values to the Table
```sql
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3002, 'Nick Rimando', 'New York', 100, 5001);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3007, 'Brad Davis', 'New York', 200, 5001);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3005, 'Graham Zusi', 'California', 200, 5002);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3008, 'Julian Green', 'London', 300, 5002);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3004, 'Fabian Johnson', 'Paris', 300, 5006);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3009, 'Geoff Cameron', 'Berlin', 100, 5003);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3003, 'Jozy Altidor', 'Moscow', 200, 5007);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3001, 'Brad Guzan', 'London', NULL, 5005);
```
## Create a Salesperson1 table
```sql
CREATE TABLE Salesman1 (salesman_id INT,name VARCHAR(20),city VARCHAR(20),commission DECIMAL(4,2));
```
## Inserting Values to the Table
```sql
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5001, 'James Hoog', 'New York', 0.15);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5002, 'Nail Knite', 'Paris', 0.13);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5005, 'Pit Alex', 'London', 0.11);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5006, 'Mc Lyon', 'Paris', 0.14);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5007, 'Paul Adam', 'Rome', 0.13);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5003, 'Lauson Hen', 'San Jose', 0.12);
```
### Q7) Write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.

### QUERY:
SELECT salesman1.name AS "Salesman", customer1.cust_name AS "Customer Name", salesman1.city AS "City" from salesman1 INNER JOIN customer1 ON salesman1.city = customer1.city;


### OUTPUT:
![image](https://github.com/Prasannalakshmiganesan/EX-3-SubQueries-Views-and-Joins/assets/118610231/b370f9cd-b7c0-418d-8112-bbe795e779c7)


### Q8) Write a SQL query to find salespeople who received commissions of more than 13 percent from the company. Return Customer Name, customer city, Salesman, commission.


### QUERY:
SELECT customer1.cust_name AS "Customer Name", customer1.city AS "Customer City", salesman1.name AS "Salesman", salesman1.commission AS "Commission" FROM salesman1 INNER JOIN customer1 ON salesman1.salesman_id = customer1.salesman_id WHERE salesman1.commission > 0.13;

### OUTPUT:
![image](https://github.com/Prasannalakshmiganesan/EX-3-SubQueries-Views-and-Joins/assets/118610231/e1b9f2e5-af93-40e5-bee4-8ee87f0be22c)


### Q9) Perform Natural join on both tables

### QUERY:
 select * from customer1 natural join salesman1;

### OUTPUT:
![image](https://github.com/Prasannalakshmiganesan/EX-3-SubQueries-Views-and-Joins/assets/118610231/7bc0ae17-4340-4be5-be31-bdf7693b28f3)


### Q10) Perform Left and right join on both tables

### QUERY
## LEFT JOIN :
SELECT * FROM salesman1 LEFT JOIN customer1 ON salesman1.salesman_id = customer1.salesman_id;

## RIGHT JOIN :
SELECT * FROM salesman1 RIGHT JOIN customer1 ON salesman1.salesman_id = customer1.salesman_id;

### OUTPUT
## LEFT JOIN :
![image](https://github.com/Prasannalakshmiganesan/EX-3-SubQueries-Views-and-Joins/assets/118610231/4bee4bda-5df2-4e16-94c4-9420494ddf0a)

## RIGHT JOIN :
![image](https://github.com/Prasannalakshmiganesan/EX-3-SubQueries-Views-and-Joins/assets/118610231/d69913e3-3e30-4287-9fa4-0c9e8010a49f)


## RESULT :
The outputs for the views and joins are successfully displayed in Oracle.
