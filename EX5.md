# Ex. No: 5 Creating Triggers using PL/SQL

## Date:

### AIM: To create a Trigger using PL/SQL.

### Steps:
1. Create employee table with following attributes (empid NUMBER, empname VARCHAR(10), dept VARCHAR(10),salary NUMBER);
2. Create salary_log table with following attributes (log_id NUMBER GENERATED ALWAYS AS IDENTITY, empid NUMBER,empname VARCHAR(10),old_salary NUMBER,new_salary NUMBER,update_date DATE);
3. Create a trigger named as log_salary-update.
4. Inside the trigger block, Insert the values into the salary_log table whenever the salary is updated.
5. End the trigger.
6. Update the salary of an employee in employee table.
7. Whenever a salary is updated for the employee it must be logged into the salary_log table with old salary and new salary.
8. Display the employee table, salary_log table.

### Program:
### Create employee table
```py
create table employee1(empid NUMBER, empname VARCHAR(10), dept VARCHAR(10),salary NUMBER);
```
### Create salary_log table
```py
 create table salary_log(log_id NUMBER GENERATED ALWAYS AS IDENTITY, empid NUMBER,empname VARCHAR(10),old_salary NUMBER,new_salary NUMBER,update_date DATE);
```
### PLSQL Trigger code
```py
create or replace trigger log_salary_update
before update on employee1
for each row
declare
v_old_salary number;
v_new_salary number;
begin
v_old_salary := :old.salary;
v_new_salary := :new.salary;
if v_old_salary <> v_new_salary then
insert into salary_log(empid,empname,old_salary,new_salary,update_date)
values(:old.empid, :old.empname , v_old_salary ,v_new_salary , SYSDATE);
end if;     
end;
 /
```
### Output:
![image](https://github.com/kanishka2305/Ex-5-Creating-Triggers-using-PL-SQL/assets/113497357/9970274c-4a09-4edb-9c40-bc9e75d0ba79)
![image](https://github.com/kanishka2305/Ex-5-Creating-Triggers-using-PL-SQL/assets/113497357/08deaa4a-411e-4f5f-b8a1-7f57ef6130fe)
![image](https://github.com/kanishka2305/Ex-5-Creating-Triggers-using-PL-SQL/assets/113497357/dd589662-d808-4498-9aa4-d1b03b5d3056)
![image](https://github.com/kanishka2305/Ex-5-Creating-Triggers-using-PL-SQL/assets/113497357/6b0a25f7-4d1c-42ad-adb8-154693ab6053)

### Result:
Thus the program implemented successfully.
