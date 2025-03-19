# HR Data Analysis Project

## Overview
Welcome to the HR Data Analysis project repository! This project focuses on leveraging SQL and Power BI for insightful Human Resources analytics for HR and finance Dept.

![Dashboard](https://github.com/user-attachments/assets/133a30c0-a5ec-42fa-9096-082c7e9277a3)

## Steps Performed
1. **Data Import:** Imported raw data from sheets and the university's Postgres DB using Excel and SQL to Power BI for seamless analysis.
2. **Transformation:** Utilized Power Query for data transformation, ensuring clean and structured datasets.
3. **KPI and Charts:** Created multiple Key Performance Indicators (KPIs) and charts for a comprehensive view of workforce dynamics.
4. **DAX Measures:** Employed DAX (Data Analysis Expressions) functions to derive additional measures, including Average Salary, Average Leave Balance, Greater Than Average Salary by Department, and personalized greetings based on time.

# Database Schema

## Overview  
This database schema gives an overview of the HR and payroll data, supporting key HR functions such as employee records, payroll processing, attendance tracking, and benefits management.

---

## **1. Employees Table**  
Stores details of all employees within the organization.  

| Column Name       | Data Type | Description |
|------------------|-----------|-------------|
| employee_id | INT (PK) | Unique identifier for each employee |
| first_name | VARCHAR | First name of the employee |
| last_name | VARCHAR | Last name of the employee |
| dob | DATE | Date of birth |
| gender | CHAR(1) | Gender of the employee ('M' or 'F') |
| hire_date | DATE | Date when the employee was hired |
| department_id | INT (FK) | Links to the `departments` table |
| job_title | VARCHAR | Employee's job title |
| employment_type | VARCHAR | Type of employment (e.g., Full-time, Part-time, Contract) |
| salary | DECIMAL | Base salary of the employee |
| status | VARCHAR | Employment status (e.g., Active, Terminated, On Leave) |

---

## **2. Departments Table**  
Maintains information about different departments.  

| Column Name       | Data Type | Description |
|------------------|-----------|-------------|
| department_id | INT (PK) | Unique identifier for each department |
| department_name | VARCHAR | Name of the department (e.g., HR, Finance, IT) |
| manager_id | INT (FK) | Employee ID of the department manager |

---

## **3. Payroll Table**  
Tracks salary payments and deductions.  

| Column Name       | Data Type | Description |
|------------------|-----------|-------------|
| payroll_id | INT (PK) | Unique identifier for each payroll entry |
| employee_id | INT (FK) | Links to the `employees` table |
| pay_date | DATE | Date of salary payment |
| basic_salary | DECIMAL | Employee’s base salary |
| tax_deduction | DECIMAL | Amount deducted as tax |
| overtime_pay | DECIMAL | Additional pay for extra hours worked |
| bonus | DECIMAL | Performance-based or other bonuses |
| net_salary | DECIMAL | Final salary after deductions |

---

## **4. Attendance Table**  
Records employee attendance and work hours.  

| Column Name       | Data Type | Description |
|------------------|-----------|-------------|
| attendance_id | INT (PK) | Unique identifier for each attendance record |
| employee_id | INT (FK) | Links to the `employees` table |
| date | DATE | Date of attendance |
| check_in_time | TIME | Time when the employee checked in |
| check_out_time | TIME | Time when the employee checked out |
| total_hours | DECIMAL | Number of hours worked |

---

## **5. Benefits Table**  
Tracks employee benefits such as health insurance and allowances.  

| Column Name       | Data Type | Description |
|------------------|-----------|-------------|
| benefit_id | INT (PK) | Unique identifier for each benefit |
| employee_id | INT (FK) | Links to the `employees` table |
| benefit_type | VARCHAR | Type of benefit (e.g., Health Insurance, Travel Allowance) |
| amount | DECIMAL | Monetary value of the benefit |

---

## **6. Training Table**  
Stores information on employee training programs.  

| Column Name       | Data Type | Description |
|------------------|-----------|-------------|
| training_id | INT (PK) | Unique identifier for each training session |
| employee_id | INT (FK) | Links to the `employees` table |
| training_name | VARCHAR | Name of the training program |
| completion_status | VARCHAR | Whether the employee completed the training (Yes/No) |

---

## **Relationships**  
- `employees.department_id` → `departments.department_id` (One-to-Many)  
- `payroll.employee_id` → `employees.employee_id` (One-to-Many)  
- `attendance.employee_id` → `employees.employee_id` (One-to-Many)  
- `benefits.employee_id` → `employees.employee_id` (One-to-Many)  
- `training.employee_id` → `employees.employee_id` (One-to-Many)  

---
