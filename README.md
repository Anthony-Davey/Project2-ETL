# Project2-ETL

## Business Questions

- How does the number of companies worked impact an employee's job satisfaction?

- How does the number of companies worked impact attrition?

- Are employees with relatively low percent salary hikes more likely to leave the organization?

- Are employees with relatively low percent salary hikes more likely to be dissatisfied at work?

	
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
- Interestingly, employees who quit had a higher average salary than employees who decided to stay with the organization.
- While employees with higher percent salary hikes were more likely to quit, they were not doing so based on a lack of job satisfaction.

## Project Report

### Extract
The original data sources consisted of 3 CSV files involving general HR employee data, employee survey data, and manager survey data. The general employee data consists of 13 integer, 8 character, and 2 float columns. The "Education" and "JobLevel" columns are ordinal data with numeric representation. The employee survey data and manager survey data consist of 3 and 2 float columns, respectively. All three datasets are linked with a primary key named "EmployeeID". All variables can be decoded with the [Data Dictionary](https://www.kaggle.com/datasets/vjchoudhary7/hr-analytics-case-study?select=data_dictionary.xlsx).

### Transform
All 3 datasets were converted into pandas dataframes for transformation. Since there is a shared key among the 3 datasets we set the index of all dataframes to "EmployeeID". We then joined both the employee and manager survey data. The general employee dataframe was also joined but only joining on variables of interest, which included "NumCompaniesWorked", "Attrition", and "PercentSalaryHike". The new combined dataframe for the company was then determined to have missing data. We noticed this by printing a count of all variables and finding different totals among them. Using the "dropna()" function we were able to eliminate all rows with missing data. To create a more efficient dataset for loading in PostgreSQL we decided to convert all of our data types to integers. By printing the datatypes we determined that even though our variables only consisted of whole numbers, the majority were classified as floats. We used the ".astype()" function to convert them all to int32. A common naming convention in programming called snake case was used, which involves replacing spaces with underscores and keeping the first letter of each word lowercase.  

*All transformations were done with the python pandas software library*

### Load
We loaded our newly joined and transformed dataframe containing all relevant variables needed to answer our business questions to PostgreSQL. Our methodology for loading involved leveraging SQLAlchemy, which is an open-source SQL toolkit and object-relational mapper for python. The three variables needed to create our connection path (username, password, and connection) were concealed for security-purposes using the .gitignore file in our Github repository. Using the ".to_sql" function we were able to create our table in PostgreSQL which we named "company_data". Our python script was designed so that it can be re-run in the future. We added a try and except statement in our jupyter-notebook to allow the user to create new tables in PostgreSQL, but prevent old tables from being replaced. In cases where a pre-existing table is going to be overwritten the user must answer an input question which provides acknowledgement of the old table being overwritten. 
