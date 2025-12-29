
# 📊 Attendance Insight Dashboard (Power BI)

## Case Study Overview
This project focuses on analysing employee attendance data to provide HR teams with a clear, data-driven view of on-site presence, work-from-home (WFH), and sick leave (SL) patterns. The goal was to transform raw attendance records into actionable, easy-to-consume insights through an interactive Power BI dashboard.

---

## Business Problem
Human Resources required a centralised reporting solution to:
- Monitor employee presence and absence trends
- Understand the balance between on-site work and remote work
- Track sick leave usage across employees and weekdays
- Identify consistent attendance patterns at both employee and organisational levels

---

## Data Scope
- **Time period:** April – June 2022  
- **Coverage:** Organisation-wide employee attendance records  
- **Granularity:** Daily attendance by employee  

---

## Key KPIs
- **On-site Presence:** 91.83%  
- **Work From Home (WFH):** 10.00%  
- **Sick Leave (SL):** 1.10%  

---

## Key Insights
- Overall on-site presence remained consistently high throughout the period.
- WFH usage was highest on Fridays, followed by Thursdays.
- Monday to Wednesday showed the strongest on-site attendance levels.
- Sick leave usage remained low and stable across all weekdays.
- Employee-level analysis identified staff with 100% on-site attendance during the period.

---

## Dashboard Features
- KPI cards summarising Presence, WFH, and SL percentages
- Daily trend analysis for Presence, WFH, and SL
- Day-of-week attendance breakdowns
- Employee-level attendance table for detailed review

---

## Visual Reference
![Attendance Insight Dashboard](./HR_Attendance.png)

---

## DAX Measures (Sample)
Below are simplified examples of DAX measures used to calculate core KPIs.

### Presence Percentage
```DAX
Presence Working Days % = DIVIDE([Present Days],[Total Working Days],0)
Present Days = 
var presentdays = calculate(count('Combined Dataset'[Value]),'Combined Dataset'[Value] in {"P"})
return
    presentdays + [WFH Count]

Total Working Days = 
 var totaldays = COUNTROWS('Combined Dataset')
 var nonworkdays = CALCULATE(Count('Combined Dataset' [value]), 'Combined Dataset'[Value] in {"WO","HO"})
 return 
    totaldays - nonworkdays
    
```

### Work From Home Percentage
```DAX

WFH % = DIVIDE([WFH Count], [Present Days],0)
WFH Count = SUM('Combined Dataset'[wfh count])



```

### Sick Leave Percentage
```DAX
SL % = DIVIDE ([SL Count],[Total Working Days],0)
SL Count = SUM('Combined Dataset'[SL count])

```

---

## Tools & Technologies
- **Power BI** – Data modelling, DAX calculations, and dashboard development
- **Excel / CSV** – Data cleaning and preparation

---

## Outcome
The final dashboard provides HR stakeholders with a reliable, repeatable view of attendance patterns, enabling consistent monitoring of workforce presence, remote work adoption, and sick leave trends.

---

## Notes
This project demonstrates practical use of Power BI for HR analytics, focusing on clarity, accuracy, and business-ready reporting rather than assumptions or speculative insights.
