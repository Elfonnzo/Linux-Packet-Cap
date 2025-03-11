# **Project Overview**

The goal of this project is to update and strengthen the organisation’s current systems by identifying and locating employee devices to ensure they are up to date and secure. This project details the methods used to access and filter SQL queries using the AND, OR, and NOT operators.

## **Retrieve After-Hours Failed Login Attempts**

After receiving a security incident report concerning failed login attempts occurring after business hours (after 18:00), I applied the following SQL query to filter any failed login attempts that matched these conditions.

![Alt Text](image3.png)

The first section specifies that the data is to be collected from the `log_in_attempts` table (`SELECT * FROM log_in_attempts`), then the `WHERE` and `AND` operators are used to filter all data from the `login_time` column, displaying only login attempts past 18:00 (`WHERE login_time > '18:00'`) and those marked as failed in the `success` column (`AND success = 0;`).

## **Retrieve Login Attempts on Specific Dates**

A suspicious event occurring on 2022-05-09 was reported, requiring an examination of any login activity between 2022-05-08 and 2022-05-09. Below is the SQL query I used to filter for login attempts within those dates.

![Alt Text](image4.png)

The first section specifies that the data is to be collected from the `log_in_attempts` table (`SELECT * FROM log_in_attempts`), then the `WHERE` and `OR` operators are used to filter all data from the `login_date` column, displaying entries where the login date equals 2022-05-09 (`WHERE login_date = '2022-05-09'`) or 2022-05-08 (`OR login_date = '2022-05-08';`).

## **Retrieve Login Attempts Outside of Mexico**

Based on the login attempt records, it was suspected that a login request did not originate from Mexico. Below is the SQL query I used to filter login attempts that occurred outside of Mexico.

![Alt Text](image6.png)

The first section specifies that the data is to be collected from the `log_in_attempts` table (`SELECT * FROM log_in_attempts`), then the `WHERE`, `NOT`, and `LIKE` operators are used to filter all data where the country does not match "MEX" (`WHERE NOT country LIKE 'MEX%'`). The `%` wildcard is used to represent an unknown string of zero or more characters.

## **Retrieve Employees in Marketing**

I was assigned to update all computers used by employees in the Marketing department. Below is the SQL query I used to filter for computers used by Marketing employees.

![Alt Text](image5.png)

The first section specifies that the data is to be collected from the `employees` table (`SELECT * FROM employees`), then the `WHERE`, `AND`, and `LIKE` operators are used to filter all data in the `department` column where the value equals "Marketing" (`WHERE department = 'Marketing'`) and to search for office locations that start with "East-" (`AND office LIKE 'East-%'`). The `%` wildcard represents an unknown string of zero or more characters.

## **Retrieve Employees in Finance or Sales**

The Finance and Sales department systems also required updates, with different security patches for each, requiring me to filter employees from only these two departments. Below is the SQL query I used.

![Alt Text](image2.png)

The first section specifies that the data is to be collected from the `employees` table (`SELECT * FROM employees`), then the `WHERE`, `LIKE`, and `OR` operators are used to filter data in the `department` column where the value matches "Finance" (`WHERE department LIKE 'Finance'`) or "Sales" (`OR department LIKE 'Sales';`). The `OR` operator was used instead of `AND` to ensure employees from both departments were included.

## **Retrieve All Employees Not in IT**

My team was required to install an additional update for employees who are **not** in the Information Technology (IT) department. This required filtering employees via the `department` column.

![Alt Text](image1.png)

The first section specifies that the data is to be collected from the `employees` table (`SELECT * FROM employees`), then the `WHERE`, `NOT`, and `LIKE` operators are used to exclude employees in the IT department (`WHERE department NOT LIKE 'Information Technology'`).

## **Summary**

By using SQL query operators such as `AND`, `OR`, `LIKE`, and `NOT`, along with the `%` wildcard filter, I was able to efficiently sort and analyse patterns within the organisation's database. This process allowed me to identify vulnerabilities and reduce potential security risks, helping to safeguard the system from future intrusions. 
