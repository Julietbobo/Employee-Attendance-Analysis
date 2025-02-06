# Employee Attendance Analysis
### Project over_view.
This is an analysis aimed at gaining insights into employees' preference of working from home or working from the office, employee absenteeism and the number of paid and sick leaves taken. The aim is to increase productivity, improve employee wellness and resource utilization. 

![git](https://github.com/user-attachments/assets/5dc2c951-84b6-4f98-8891-eedef54f9201)
![tooltip](https://github.com/user-attachments/assets/5a2a2e18-4ba7-463f-96dc-31f348601eac)
![Screenshot (23)](https://github.com/user-attachments/assets/6cdaffe7-a855-44ac-988b-72b8416297b8)

## Table of contents
1. [Data Source](#data-source)
2. [Tools](#tools)
3. [Data Preparation](#data-preparation)
4. [Exploratory Data Analysis](#exploratory-data-analysis)
5. [Assumption](#assumption)
6. [Data Analysis](#data-analysis)
7. [Findings](#findings)
8. [Recommendations](#recommendations)

### Data Source
The data is sourced from an excel file obtained from a youtube channel: AttenanceSheet2022.xls for May to June 2022.

### Tools
- Excel
   - Power Query for data cleaning, data wrangling and data transformation.
- Power Bi - Visualization.

### Data Preparation
- Data loading and inspection
- Change of data types
- Unpivoting columns
- Replacing values
- Creation of functions to reuse the applied steps for each month.
- Creation of parameters based on the month of the data
- Visualization


### Exploratory Data Analysis
The analysis seeks to answer the followng questions:
1. Which days have the highest office attendance.
2. Which days do employees prefer working from home.
3. Who are the most absent employees.
4. Which days have the lowest work attendance whether work from home or from the office.

### Assumption
- Absenteeism is regarded as abscondment of duty.

### Data Analysis
- I created measures to calculate the total working days (exlusive of holidays, weekly offs and weekends) which is like a register to show total attendance for all working days. 
- I also created measures to see the rate of office attendance, work from home, absenteeism and leaves.
- Below are some examples of measures I calculated;
  
```WorkingDays = 
var workdays = CALCULATE(COUNT('Final Data'[Dates]))
var offs=   CALCULATE(COUNT('Final Data'[Dates]), FILTER('Final Data', 'Final Data'[Reason] in {"WO","HO"} &&
'Final Data'[Day] IN {"Sat", "Sun"}))
return workdays-offs
 ```
```
 WFH =CALCULATE(COUNT('Final Data'[Dates]), FILTER('Final Data', 'Final Data'[Reason] = "WFH"))
```

```%WFH = DIVIDE([WFH], [WorkingDays])```

### Data visualization.
- For trend analysis I used an area chart which is the most suitable to show attendance for each day.
- I used a tooltip in the area chart to gain deeper insights on the different leaves taken, absenteeism and employee preference of working from home or from the office.
- I also used column charts to see the most absent employees and the weekdays which employees prefer being at the office or working from home.
- I used an information button to help viewers understand some of the acronyms, the scope of data and how I have calculated some of the measures.

### Findings
1. Generally there is a higher preference of working from the office to working from home.
2. Wednesdays have the highest office attendance.
3. Its worth noting that on Monday the percentage of people working from home is the highest.
4. The highest number recorded of absentees due to sickness in a single day is 4 (30th May 2022) which is not a significant figure to cause an alarm.
5. There are 8 employees who have been absent from work for more than 3 days in a span of 3 months.
6. From 20th June there was very low attendance whether work from home or from the office.

### Recommendations
1. Critical office activities like meetings, team lunches etc to be held on Wednesdays where we have the highest office attendance.
2. Investigate the top 8 absent employees to find out the reason for the high rate of absenteeism.
3. Check if high absenteeism from June 20th is linked to excessive workload or burnout.
4. Encourage the employees to go on leave for high productivity and to avoid burnout. 
5. On the flip side discourage extreme taking of leave days as this causes a workforce gap and low productivity.

