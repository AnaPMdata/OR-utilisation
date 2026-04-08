# OR-utilisation
Project Summary
This project is a Power BI report analysing operating room (OR) utilization for Q1 2022 using real-world style theatre data. It demonstrates:

Healthcare domain understanding (OR workflows and timings)

Data modelling and DAX

Dashboard design for clinical and operational stakeholders

The report is built from a single Excel dataset and organised into three focused pages:

1.Executive Overview

2.OR Efficiency

3.Service Drilldown

Business Problem
Operating theatres are expensive resources and often a bottleneck for elective and emergency care. Hospitals need to know:

Are ORs being used efficiently compared with what was booked?

Where are the main delays and inefficiencies (late starts, long setup, slow room exit)?

Which services and procedures consume the most time?

This report addresses those questions for Q1 2022.

Your Role
Defined the business questions from a clinical/operations perspective.

Designed the data model and DAX in Power BI.

Built a 3‑page dashboard with clear navigation and slicers for date, OR suite, and service.



Data Source
File: 2022_Q1_OR_Utilization-1.xlsx

Sheet: 2022_Q1

Rows: 2,172 OR cases (Q1 2022)

Key columns:

Date, Encounter ID

OR Suite

Service (surgical specialty)

CPT Code, CPT Description

Booked Time (min)

OR Schedule time

Wheels In, Start Time, End Time, Wheels Out

Data Model & DAX
Single fact table with calculated columns and measures created in Power BI.

Calculated Columns
Procedure Minutes
Procedure Minutes = DATEDIFF('2022_Q1'[Start Time],'2022_Q1'[End Time],MINUTE)

Room Occupancy Minutes
Room Occupancy Minutes = DATEDIFF('2022_Q1'[Wheels In],'2022_Q1'[Wheels Out],MINUTE)

Delay to Wheels In
Delay to Wheels In = DATEDIFF('2022_Q1'[OR Schedule],'2022_Q1'[Wheels In],MINUTE)

Setup Minutes
Setup Minutes = DATEDIFF('2022_Q1'[Wheels In],'2022_Q1'[Start Time],MINUTE)

Exit Minutes
Exit Minutes = DATEDIFF('2022_Q1'[End Time],'2022_Q1'[Wheels Out],MINUTE)

Date helpers

Case Date (DATEVALUE of Date)

Day Name (FORMAT(Date,"dddd"))

Month Name (FORMAT(Date,"MMM"))

Measures (examples)
Total Cases

Total Booked Minutes

Total Procedure Minutes

Total Room Occupancy Minutes

Avg Procedure Minutes

Booked vs Actual Variance

Variance %

These measures compare planned vs actual use and support utilisation and delay analysis.

Report Pages

1. Executive Overview
Goal: High-level snapshot for clinical and operational leaders.

Typical visuals:

KPI cards:

Total Cases

Total Booked Minutes

Total Procedure Minutes

Total Room Occupancy Minutes

Average Procedure Minutes

Cases by Service (bar chart)

Utilization by OR Suite (bar chart)

Daily trend of cases or procedure minutes (line chart)

Value: Shows Q1 theatre workload and how intensively ORs were used overall.


2. OR Efficiency
Goal: Understand how time is used inside each case and where delays arise.

Visuals:

Average Delay to Wheels In by OR Suite and/or Service

Average Setup Minutes (Wheels In → Start Time)

Average Procedure Minutes

Average Exit Minutes (End Time → Wheels Out)

Stacked or clustered charts that show how these components add up to total room occupancy.

Value: Highlights specific rooms or services with late starts, long setup, or slow exit, supporting targeted process improvement.


3. Service Drilldown
Goal: Drill into specialties and procedures.

Visuals:

Matrix:

Rows: Service → CPT Description

Values: Case Count, Avg Procedure Minutes, Avg Room Occupancy Minutes

Top Services by Case Volume (bar chart)

Top CPT procedures by Average Procedure Duration (bar chart)

Slicers:

Date / Month

OR Suite

Service

Value: Helps identify high‑volume or time‑intensive procedures and specialties, useful for planning lists, staffing, and capacity.


Key Insights (Examples You Can Talk About)
These will vary slightly depending on the data, but examples you might highlight:

Which services accounted for the highest case volume and longest average procedure times.

Whether room occupancy is significantly higher than procedure time, indicating long setup or exit phases.

Any OR suites with noticeably higher average delay to Wheels In, suggesting scheduling or flow issues.
