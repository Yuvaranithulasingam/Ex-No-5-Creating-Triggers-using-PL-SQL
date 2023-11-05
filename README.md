# Ex-5-Creating-Triggers-using-PL-SQL

## Date:

## AIM:
To create a Trigger using PL/SQL.

## STEPS:

1)Create employee table with following attributes (empid NUMBER, empname VARCHAR(10), dept VARCHAR(10),salary NUMBER);

2)Create salary_log table with following attributes (log_id NUMBER GENERATED ALWAYS AS IDENTITY, empid NUMBER,empname VARCHAR(10),old_salary NUMBER,new_salary NUMBER,update_date DATE);

3)Create a trigger named as log_salary-update.

4)Inside the trigger block, Insert the values into the salary_log table whenever the salary is updated.

5)End the trigger.

6)Update the salary of an employee in employee table.

7)Whenever a salary is updated for the employee it must be logged into the salary_log table with old salary and new salary.

8)Display the employee table, salary_log table

## PROGRAM:

### Create table for employee:
```
CREATE TABLE empl
(
empid NUMBER,
empname VARCHAR2(10),
dept VARCHAR2(10),
salary NUMBER
);
```
### Create table for wages_log:
```
CREATE TABLE wages_log
(
log_id NUMBER GENERATED ALWAYS AS IDENTITY,
empid NUMBER,
empname VARCHAR2(10),
old_salary NUMBER,
new_salary NUMBER,
update_date DATE
);
```
### Create a trigger named logging_sal_update:
```
CREATE OR REPLACE TRIGGER logging_sal_update
BEFORE UPDATE ON empl
FOR EACH ROW
BEGIN
IF :OLD.salary != :NEW.salary THEN
INSERT INTO wages_log (empid, empname, old_salary, new_salary, update_date)
VALUES (:OLD.empid, :OLD.empname, :OLD.salary, :NEW.salary, SYSDATE);
END IF;
END;
/
```
###  Inserting data into the employed table:
```
insert into empl values(1,'Divya','IT',100000);
insert into empl values(2,'Sujithra','SALES',50000);
insert into empl values(3,'Pavithra','HR',110000);
insert into empl values(4,'Saranya','SALES',50000);
insert into empl values(5,'Dharshini','IT',100000);
```
### Update the salary of an employed:
```
UPDATE empl
SET salary = 120000
where empid=3;
```
### Display the employee table:
```
select * from empl;
```
### Display the salary_log table:
```
select * from wages_log;
```

## OUTPUT:

### Create table for employee:
![image](https://github.com/Yuvaranithulasingam/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/121418522/37c99988-d1cb-4c7c-9c13-8118d981818d)
### Create table for wages_log:
![image](https://github.com/Yuvaranithulasingam/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/121418522/fd224585-9cbe-430d-846b-b3a0c26edf36)
### Create a trigger named logging_sal_update:
![image](https://github.com/Yuvaranithulasingam/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/121418522/a09d382b-71a8-40e3-bd97-2f8dfb467f73)
###  Inserting data into the employed table:
![image](https://github.com/Yuvaranithulasingam/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/121418522/d45ce568-14b0-4339-9c3a-aa09e5a3bb57)
### Update the salary of an employed:
![image](https://github.com/Yuvaranithulasingam/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/121418522/3de4a61a-4653-4682-8572-b11ce15621be)
### Display the employee table:
![image](https://github.com/Yuvaranithulasingam/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/121418522/4d9673ce-6a0c-418a-9c04-f720f1eb09f5)
### Display the salary_log table:
![image](https://github.com/Yuvaranithulasingam/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/121418522/47831045-366b-4614-8ff0-19b39965d1fb)

## RESULT:
The program has been implemented successfully.
