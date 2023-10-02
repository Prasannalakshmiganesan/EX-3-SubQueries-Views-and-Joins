# EX 3 SubQueries, Views and Joins 


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
![image](https://github.com/dineshgl/EX-3-SubQueries-Views-and-Joins/assets/118610231/226b6f5d-933f-4ac6-afa9-ddf1d02e74bf)

### Q2) List the ename,job,sal of the employee who get minimum salary in the company.

### QUERY:
SELECT ename, job, sal FROM empl WHERE sal = (SELECT MIN(sal) FROM empl);

### OUTPUT:
![image](https://github.com/dineshgl/EX-3-SubQueries-Views-and-Joins/assets/118610231/59c641ce-93c1-4e31-b6d2-7808e2a91a10)


### Q3) List ename, job of the employees who work in deptno 10 and his/her job is any one of the job in the department ‘SALES’.

### QUERY:
SELECT ename, job FROM empl WHERE deptno = 10 AND job IN (SELECT job FROM empl WHERE job = 'sales');


### OUTPUT:
![image](https://github.com/dineshgl/EX-3-SubQueries-Views-and-Joins/assets/118610231/eb5fe2fa-e21f-4cde-a228-1bb981f7c460)



### Q4) Create a view empv5 (for the table emp) that contains empno, ename, job of the employees who work in dept 10.

### QUERY:
![image](https://github.com/dineshgl/EX-3-SubQueries-Views-and-Joins/assets/118610231/9a07bc39-e155-4815-a726-87cfdeac5851)


### OUTPUT:
![image](https://github.com/dineshgl/EX-3-SubQueries-Views-and-Joins/assets/118610231/09b257c5-1e6d-49cf-a501-7d4371db5d2e)


### Q5) Create a view with column aliases empv30 that contains empno, ename, sal of the employees who work in dept 30. Also display the contents of the view.

### QUERY:
![image](https://github.com/dineshgl/EX-3-SubQueries-Views-and-Joins/assets/118610231/737e3963-fe9e-45cf-b01a-917bae4c81e5)


### OUTPUT:
![image](https://github.com/dineshgl/EX-3-SubQueries-Views-and-Joins/assets/118610231/6b2693d7-435b-4184-9490-97a5d223672c)


### Q6) Update the view empv5 by increasing 10% salary of the employees who work as ‘CLERK’. Also confirm the modifications in emp table

### QUERY:
![270767939-d83bbdcd-83a3-427e-bd2b-e799958b055d](https://github.com/dineshgl/EX-3-SubQueries-Views-and-Joins/assets/118610231/5b0717dd-c1fe-4bff-b559-807cc9ba1896)


### OUTPUT:
![270767871-6941b531-33ed-41dc-b6f4-9e8bcc0dd113](https://github.com/dineshgl/EX-3-SubQueries-Views-and-Joins/assets/118610231/b1d30d8a-358f-43df-b2e3-fc2b9db64c30)


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
![image](https://github.com/dineshgl/EX-3-SubQueries-Views-and-Joins/assets/118610231/05fa7739-e1ce-4470-a152-dfd89bdcd246)


### Q8) Write a SQL query to find salespeople who received commissions of more than 13 percent from the company. Return Customer Name, customer city, Salesman, commission.


### QUERY:

SELECT customer1.cust_name AS "Customer Name", customer1.city AS "Customer City", salesman1.name AS "Salesman", salesman1.commission AS "Commission" FROM salesman1 INNER JOIN customer1 ON salesman1.salesman_id = customer1.salesman_id WHERE salesman1.commission > 0.13;

### OUTPUT:
![image](https://github.com/dineshgl/EX-3-SubQueries-Views-and-Joins/assets/118610231/64850f7b-5f9f-430e-8d57-8eeca6f44f4d)


### Q9) Perform Natural join on both tables

### QUERY:
select * from customer1 natural join salesman1;

### OUTPUT:
![image](https://github.com/dineshgl/EX-3-SubQueries-Views-and-Joins/assets/118610231/e56fed3d-0e7e-41f0-b1dd-11048c30195a)


### Q10) Perform Left and right join on both tables

### QUERY:
## LEFT JOIN :
SELECT * FROM salesman1 LEFT JOIN customer1 ON salesman1.salesman_id = customer1.salesman_id;

## RIGHT JOIN :
SELECT * FROM salesman1 RIGHT JOIN customer1 ON salesman1.salesman_id = customer1.salesman_id;

### OUTPUT:
## LEFT JOIN :
![image](https://github.com/dineshgl/EX-3-SubQueries-Views-and-Joins/assets/118610231/ebce7b32-b7d6-44d2-9315-bb40c8463bd3)

## RIGHT JOIN :
![image](https://github.com/dineshgl/EX-3-SubQueries-Views-and-Joins/assets/118610231/592112fb-cc89-4a7f-a9c6-49e6509e7bbd)
