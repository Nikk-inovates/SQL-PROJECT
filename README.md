# SQL-PROJECT
SQL Practice Project

This project is a practical demonstration of my SQL skills, involving the creation and querying of a database with two tables: Records and Tax_Report. Using HeidiSQL, I practiced various SQL concepts, including joins, filtering, and payroll calculations, while working with real-world scenarios such as employee details and tax reports.

Project Overview

Database Tables

1. Records

This table contains details about employees, such as:

EMP_ID (Primary Key): Unique identifier for each employee.

EMP_NAME: Name of the employee.

SALARY: Total salary of the employee.

DATE_OF_JOINING: The date the employee joined the company.

2. Tax_Report

This table contains payroll details for each employee, including:

EMP_ID (Primary Key): Links to the EMP_ID in the Records table.

BASIC_SALARY: 50% of the total salary.

TA (10%): Travel Allowance (10% of Basic Salary).

DA (15%): Dearness Allowance (15% of Basic Salary).

HRA (20%): House Rent Allowance (20% of Basic Salary).

INSURANCE: Fixed amount of ₹2000 for all employees.

TAX: Calculated based on total salary (₹5000 tax for salaries above ₹50,000; 15% for salaries exceeding ₹50,000).

NET_SALARY: Total gross salary after deductions.

Key Queries Practiced

Example Query 1: Employees Paying High Tax and Earning High Salaries

Retrieve employees who pay more than ₹5000 in taxes and earn a salary above ₹60,000:

SELECT
    r.EMP_NAME,
    t.TAX,
    r.SALARY
FROM
    Records r
INNER JOIN
    Tax_Report t
ON
    r.EMP_ID = t.EMP_ID
WHERE
    t.TAX > 5000
    AND r.SALARY > 60000;

Example Query 2: Discrepancies in Salary and Payroll

Find employees whose total salary from the Records table does not match twice their basic salary in the Tax_Report table:

SELECT
    r.EMP_ID,
    r.EMP_NAME,
    r.SALARY AS Total_Salary,
    t.BASIC_SALARY,
    (t.BASIC_SALARY * 2) AS Calculated_Salary
FROM
    Records r
INNER JOIN
    Tax_Report t
ON
    r.EMP_ID = t.EMP_ID
WHERE
    r.SALARY != (t.BASIC_SALARY * 2);

Example Query 3: Employees Who Joined After 2015

Retrieve employees who joined the company after 2015:

SELECT
    EMP_NAME,
    DATE_OF_JOINING
FROM
    Records
WHERE
    DATE_OF_JOINING > '2015-12-31';

Tools and Technologies Used

SQL: For database creation, data manipulation, and querying.

HeidiSQL: For managing and visualizing the database.

What I Learned

How to design normalized tables and establish relationships between them.

The importance of joins in retrieving data from multiple tables.

Writing conditional logic (e.g., CASE statements) in SQL queries for dynamic calculations.

Effective filtering and querying for specific datasets.

How to Use This Project

Clone the repository to your local system.

Import the provided .sql files into HeidiSQL or your preferred SQL client.

Explore the queries and modify them to experiment with different scenarios.

Repository Contents

database_schema.sql: Contains the schema and sample data for the Records and Tax_Report tables.

practice_queries.sql: Includes the SQL queries I wrote and practiced.

README.md: This documentation file explaining the project.

Connect with Me

Feel free to connect with me on LinkedIn or check out my other projects on GitHub. I’d love to hear your feedback or collaborate on future projects!

