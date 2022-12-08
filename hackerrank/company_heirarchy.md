Amber's conglomerate corporation just acquired some new companies. 
  
Given the table schemas below, write a query to print the company_code, founder name, total number of lead managers, total number of senior managers, total number of managers, and total number of employees. Order your output by ascending company_code.

**Note:**
- The tables may contain duplicate records.
- The company_code is string, so the sorting should not be numeric. For example, if the company_codes are C_1, C_2, and C_10, then the ascending company_codes will be C_1, C_10, and C_2.

**Input Format**

The following tables contain company data:
- Company: The company_code is the code of the company and founder is the founder of the company

![IMG](https://s3.amazonaws.com/hr-challenge-images/19505/1458531125-deb0a57ae1-ScreenShot2016-03-21at8.50.04AM.png) 

- Lead Manager: The lead_manager_code is the code of the lead manager, and the company_code is the code of the working company. 

![IMG](https://s3.amazonaws.com/hr-challenge-images/19505/1458534960-2c6d764e3c-ScreenShot2016-03-21at8.50.12AM.png)  

- Senior_Manager: The senior_manager_code is the code of the senior manager, the lead_manager_code is the code of its lead manager, and the company_code is the code of the working company

![IMG](https://s3.amazonaws.com/hr-challenge-images/19505/1458534973-6548194998-ScreenShot2016-03-21at8.50.21AM.png)

- Manager: The manager_code is the code of the manager, the senior_manager_code is the code of its senior manager, the lead_manager_code is the code of its lead manager, and the company_code is code of the working company

![IMG](https://s3.amazonaws.com/hr-challenge-images/19505/1458534988-7fc0af46ce-ScreenShot2016-03-21at8.50.29AM.png)

- Employee: The employee_code is the code of the employee, the manager_code is the code of its manager, the senior_manager_code is the code of its senior manager, the lead_manager_code is the code of its lead manager, and the company_code is the code of the working company. 

![IMG](https://s3.amazonaws.com/hr-challenge-images/19505/1458535002-d47f63cbb4-ScreenShot2016-03-21at8.50.41AM.png)  

```sql
select company.company_code,company.founder,count(Distinct employee.lead_manager_code),
count(Distinct employee.senior_manager_code),count(Distinct employee.manager_code),count(Distinct employee.employee_code) from company
inner join employee
on employee.company_code = company.company_code
group by company.company_code,company.founder
order by company.company_code
```