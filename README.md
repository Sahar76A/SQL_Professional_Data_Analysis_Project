# SQL_Professional_Data_Analysis_Project

## Overview

This project analyzes **Data Analyst job postings** using SQL to uncover insights about:
- Top-paying roles in the market  
- Most in-demand technical skills  
- Skills associated with higher salaries  
- Optimal skills to focus on for career growth  

The goal of this analysis is to better understand the current job market and use data-driven insights to guide my **career strategy and skill development path**.

🧭 All SQL queries used in this project are available in the `project_sql/` folder.

---

## 🎯 Project Objectives

This analysis was designed to answer the following key questions:

- What are the top-paying data analyst jobs?
- What skills are required for these high-paying roles?
- What skills are most in demand in the job market?
- Which skills are associated with higher salaries?
- What are the most optimal skills to learn for career growth?

---

## 🛠️ Technologies Used

- **SQL** – Core language for data querying and analysis  
- **PostgreSQL** – Database management system used for job posting data  
- **Visual Studio Code** – SQL development and query execution  
- **Git & GitHub** – Version control and project sharing  

---

## 📊 Analysis & Key Insights

### 1. Top-Paying Data Scientist Jobs

To identify the highest-paying roles, I filtered remote Data Scientist positions and sorted them by average salary.

```sql
SELECT
    job_id,
    job_title,
    salary_year_avg,
    company_dim.name AS Company_Name,
    job_location,
    job_schedule_type,
    job_posted_date
FROM job_postings_fact
LEFT JOIN company_dim 
    ON job_postings_fact.company_id = company_dim.company_id
WHERE
    job_title_short = 'Data Scientist'
    AND job_location = 'Anywhere'
    AND salary_year_avg IS NOT NULL
ORDER BY salary_year_avg DESC
LIMIT 10;
