# Employee Attendance Analysis
### Project over_view.
This is an analysis aimed at gaining insights into employees' preference of working from home or working from the office, employee absenteeism and the number of paid and sick leaves taken. The aim is to increase productivity, improve employee wellness and resource utilization. 

### Data Source
The data is sourced from an excel file obtained from a youtube channel: AttenanceSheet2022.xls for May to June 2022.

### Tools
- Excel
   - Power Query for data cleaning, data wrangling and data transformation.
- Power Bi - Visualization.

### Data Preparation/Cleaning
- Change of data typeS
- Unpivoting columns
- Replacing values
- Creation of functions to reuse the applied steps for each month.
- Creation of parameters based on the month of the data
- Data loading

### Exploratory Data Analysis
The analysis seeks to answer the followng questions:
1. Which days have the highest office attendance.
2. Which days do employees prefer working from home.
3. Who are the most absent employees.
4. Which days have the lowest work attendance whether work from home or from the office.

### Assumption
- Absenteeism is regarded as abscondment of duty.

### Data Analysis
- I created measures to calculate the total working days which is exlusive of holidays, weekly offs and weekends. The total is a summation of the total number of employees (stating whether they are in the office, working from home, absent or on leave).
- I also created measures to see the rate of office attendance, work from home, absenteeism and leaves.
```WorkingDays = 
var workdays = CALCULATE(COUNT('Final Data'[Dates]))
var offs=   CALCULATE(COUNT('Final Data'[Dates]), FILTER('Final Data', 'Final Data'[Reason] in {"WO","HO"} &&
'Final Data'[Day] IN {"Sat", "Sun"}))
return workdays-offs
 ```
