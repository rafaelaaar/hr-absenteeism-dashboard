Employee Absenteeism Analysis
This project analyses employee absenteeism in a manufacturing company to identify key patterns across departments, stores, and employee demographics using SQL and Power BI.
Overview
Metric	Value
Total Employees	8,336
Total Absent Hours	510.86
AVG Absent Hours	61.28
AVG Age	42.01
AVG Tenure	4.78 years


The dataset captures absenteeism hours per employee along with demographic attributes (age, gender, length of service) and organisational context (department, store location).
Key Insights
1. Department Analysis
The Processed Food department has the highest absenteeism rate, with employees averaging 63.63 hours absent. The workforce in this department is mid-age and mid-tenure, suggesting that physical strain from the nature of the work may be a key driver.
2. Store Analysis
Fort St John is the most critical store within the Processed Food department, standing out as the location with the highest concentration of absent hours. This may warrant further investigation into local working conditions or staffing levels.
3. Employee Outliers
Employee 7431 (aged 62) is a significant outlier — much older than the department average of 39 years. This reinforces the pattern that older employees with longer tenure tend to accumulate more absent hours, likely due to health-related factors.
4. Age & Tenure
Older employees with longer service tend to have higher absenteeism, suggesting that physical wear and chronic health conditions accumulate over time. This pattern is consistent across departments.
5. Gender
Despite similar average ages, women show slightly higher absenteeism than men. While the difference is not dramatic, it may point to additional factors worth exploring, such as caregiving responsibilities or role distribution.
Conclusion
The data reveals that absenteeism is not evenly distributed. The Processed Food department, and Fort St John in particular, carry a disproportionate share of absent hours. Employee demographics play a clear role: older employees with longer tenure are more likely to be absent, and women show slightly higher rates than men.
This suggests that targeted interventions — such as ergonomic improvements in physically demanding departments, health support programmes for long-tenured staff, and location-specific reviews — could help reduce absenteeism where it matters most.
Data Preparation & Measures
•	Dataset: Absenteeism at Work in a Manufacturing Company
•	Source: Kaggle — https://www.kaggle.com/datasets/HRAnalyticRepository/absenteeism-dataset
•	Tools: SQL (data exploration) + Power BI (dashboard and DAX measures)
SQL Queries
The following SQL queries were used to explore the dataset — covering totals, averages, department-level breakdowns, and per-employee rankings:
-- Total employees and total absent hours
SELECT COUNT(EmployeeNumber) AS Total_employees,
       ROUND(SUM(AbsentHours), 2) AS Total_absent
FROM absenteeism

-- Average absent hours, age, and tenure
SELECT ROUND(AVG(AbsentHours), 2) AS AVG_hour_absent,
       ROUND(AVG(Age), 2) AS AVG_Age,
       ROUND(AVG(LengthService), 2) AS Tenure
FROM absenteeism

-- Department breakdown with absenteeism rate per employee
SELECT DepartmentName,
       COUNT(EmployeeNumber) AS Total_employees,
       ROUND(SUM(AbsentHours), 2) AS Total_absent,
       ROUND(SUM(AbsentHours), 2) / COUNT(EmployeeNumber) AS Hours_per_employee
FROM absenteeism
GROUP BY DepartmentName
ORDER BY Hours_per_employee DESC

-- Top employees by absent hours
SELECT EmployeeNumber, Surname, GivenName,
       DepartmentName, AbsentHours
FROM absenteeism
ORDER BY AbsentHours DESC

Power BI Measures (DAX)
The following DAX measures were created in Power BI to support the dashboard KPIs:
Total Employees = COUNT(MFGEmployees4[EmployeeNumber])

Total Absent Hour = SUM(MFGEmployees4[AbsentHours])

AVG Absent Hour = AVERAGE(MFGEmployees4[AbsentHours])

AVG Age = AVERAGE(MFGEmployees4[Age])

AVG Length of Service = AVERAGE(MFGEmployees4[LengthService])
Dashboard Preview
KPI Overview
This section presents the main HR metrics, including total employees, total absent hours, average absent hours, average age, and average length of service.
![KPI Overview](images/KPI.png)
Absenteeism Analysis
This dashboard explores absenteeism by department and store, identifying which areas carry the highest burden and where targeted interventions could have the most impact.
![Absenteeism Analysis](images/Absenteeism Analysis.png)
Store & Workforce Insights
This view analyses absenteeism patterns by age, gender, and tenure, highlighting demographic factors that correlate with higher absent hours.
![Store & Workforce Insights](images/Store & Workforce Insights.png)
Contact
Created by Rafaela Araujo.
•	LinkedIn: https://www.linkedin.com/in/rafaelaaaraujo

