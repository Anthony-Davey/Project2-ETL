# Project2-ETL

## Business Questions

- How does the number of companies worked impact an employee's job satisfaction?

- How does the number of companies worked impact attrition?

- Are employees with relatively low precent salary hikes more likely to leave the organization?

- Are employees with relatively low precent salary hikes more likely to be dissatisfied at work?

	
## Project Proposal

#### Data Sources - Obtained from [Kaggle: HR Analytics Case Study](https://www.kaggle.com/datasets/vjchoudhary7/hr-analytics-case-study)
- [General Employee Data](https://www.kaggle.com/datasets/vjchoudhary7/hr-analytics-case-study?select=general_data.csv)
- [Employee Survey Data](https://www.kaggle.com/datasets/vjchoudhary7/hr-analytics-case-study?select=employee_survey_data.csv)
- [Manager Survey Data](https://www.kaggle.com/datasets/vjchoudhary7/hr-analytics-case-study?select=manager_survey_data.csv)

*All data extracted were in CSV format*

#### Database Used
We decided that a relational database would be more beneficial given that we already had structured data from CSV files. The relational database that we leveraged was PostgreSQL.

#### Findings

- Employees who've worked for 4 or less companies throughout their professional careers were found to have higher job satisfaction when compared to those who've worked for more than 4 companies.
- On average, employees that quit tend to have worked for more companies than those that have not quit their jobs. 

## Project Report

### Extract
The original data sources consisted of 3 CSV files involves general HR employee data (general , employee survey data, and manager survey data. The general employee data consisted of 13 integer, 8 character, and 2 float columns. The employee survey data and manager survey data consisted of 3 and 2 float columns, respectively. 

### Transform

### Load
