# SQL Filtering 
__Description__: Ran SQL queries to retrieve information from a database called organization, that contained two tables with login attempts for employees. I applied AND, OR and NOT operators to filter various SQL queries. 

## **Structure of the tables**

 1. Table Name: **log_in_attempts**

>The `log_in_attempts` table has the following columns:
+ event_id : The identification number assigned to each login event
+ username : The username of the employee
+ login_date : The date the login aŵempt was recorded
+ login_time : The time the login aŵempt was recorded
+ country : The country where the login aŵempt occurred
+ ip_address : The IP address of that employee’s machine
+ success : The success of the login aŵempt; FALSE indicates a failed aŵempt

2. Table Name: **employees**

>The `employees` table has the following columns:
+ employee_id : The identification number assigned to each employee
+ device_id : The identiůcation number assigned to each device used by the employee
+ username : The username of the employee
+ department : The department the employee is in
+ office : The oũce the employee is located in

### FILTERS APPLIED

**a. Retrieve after hours failed login attempts**
+ The query was to determine failed login attempts that were made after business hours. I had to retrieve
this information from the login activity by identifying all unsuccessful attempts after 18:00. The sql
query i ran is listed below:
```
SELECT *
FROM log_in_attempts
WHERE login_time > '18:00' AND success = 0;
```
+ In the code above; I selected all fields from the `log_in_attempts` table, then filtered by login_time field
  and the success field, ensuring to use the `AND` operator in order to have records returned that had users who failed
  any login attempts after hours. I had used 0 in the sql for the success field. I could have also used the
  Boolean variable of FALSE as well.

**b. Retrieve login aŵempts on specific dates**
+ In the code below i was investigating a suspicious event that occurred on '2022-05-09'. I had to retrieve all login
attempts that occurred on this day and the day before ('2022-05-08'). The sql query i ran is listed below:
```
SELECT *
FROM log_in_attempts
WHERE login_date = '2022-05-09' OR login_date = '2022-05-08';
```

**c. Retrieve login attempts outside of Mexico**
+ I was investigating logins that did not originate in Mexico, and needed to find this information.
The sql query i ran is listed below:
```
SELECT *
FROM log_in_attempts
WHERE NOT country LIKE 'MEX%';
```
+ In the `country` field Mexico has entries that are ‘Mexico’ and ‘Mex’ - so the `LIKE` operator had to be
used with a wildcard represented by the percentage sign ‘Mex%’ to find patterns, alongside the `NOT`
operator which returned all countries that are not mexico.

**d. Retrieve employees in Marketing**
+ I needed to obtain the information about employees in the 'Marketing' department who are located in all
  offices in the East building (such as 'East-170' or 'East-320' ). The sql query i ran is listed below:
```
SELECT *
FROM employees
WHERE department = 'Marketing' AND office LIKE 'East%';
```
+ Again the `LIKE` operator had to be used with a pattern of ‘East%’, alongside the `AND` operator which
returned all employees from the Marketing department from all East offices.

**e. Retrieve employees in Finance or Sales Department**
+ Information abour all employees in the Finance or the Sales department, and I need to locate information
  on these employees. The sql query i ran is listed below:
```
SELECT *
FROM employees
WHERE department = 'Finance' OR department = 'Sales';
```

**f. Retrieve all employees not in IT Department**
+ Information about employees who are not in the Information Technology department is requested.
  The sql query i ran is listed below:
```
SELECT *
FROM employees
WHERE NOT department = 'Information Technology';
```

### Summary
> [!IMPORTANT]
> During this project I was able to refresh my practical experience in using SQL to
> + run SQL queries to retrieve information from a database and
> + apply AND , OR , and NOT operators to fi SQL queries.






























