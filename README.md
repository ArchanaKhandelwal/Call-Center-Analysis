# Project brief

ServiceSpot, an IT company, has approached you to help them analyze their call center data. They receive daily calls from customers and are seeking a streamlined solution to consolidate and analyze their data effectively. Your objective is to create a comprehensive analytics solution that integrates multiple data files, enabling them to generate visually appealing reports for performance monitoring and strategic insights.

# Solution

Refer to the 'Call Center Analysis.pbix' file for detailed analysis OR view 'Call Center Analysis.pdf' to get an overview of the report. 

# Findings in the PBI report

## I. Load & Data Transformation:

1. The transformation steps include functions such as ‘Use first Rows as Headers’, ‘Unpivot Only Selected Column’, ‘Split Column by Delimiter’, ‘Replace Values’, ‘Append tables’, among others.
2. We had to create an additional table ‘Dim_DateCalendar’ to use time-intelligence DAX functions across the data model.
3. Improper data type for CallTimestamp (Text) in the files Data 2018, Data 2019, and Data 2020; changed later using locale English (United States).
4. The data type for CallTimestamp in Data 2021 was correctly provided.
5. The columns CallDuration and WaitTime were provided in seconds. We had to convert them into proper duration (days, hours, minutes, seconds) using DAX time-intelligence functions.
6. A single Fact_Data table is constructed out of the 4 data files using the option ‘Append Query’.
7. We had to create a new column ‘StateCD’ out of the ‘Site’ column using the Split Column function to join the table with ‘States’.
8. There are only 3 call types with their respective unique Call type IDs.
9. We had to Unpivot the 4 columns ‘Call Charges / Min (XXXX)’ to properly structure the data for analysis.

## II. Relationship (Data Model):

1. The ‘Fact_Data’ table shares a Many-to-One relationship with ‘Dim_DateCalendar’ via Call Date, ‘Dim_Call Types’ via Call Type, and Dim_Employees via EmployeeID.
2. ‘Dim_Employees’ shares a Many-to-One relationship with ‘Dim_States’ via StateCD.
3. ‘Dim_Call Types’ shares a One-to-Many relationship with ‘Dim_call charges per year’ via CallTypeID.

## III. Report:

### Overview:

1. The three charts (Call Type, Call Abandoned, Call Waiting) show the number of calls, abandoned calls, and the total waiting time over four years of call services. Among the three types of call services, the most frequent call type is Tech Support, followed by Billing and Sales.
2. The "Total Calls by Site" pie chart shows the proportion of call counts by office location, with Spokane at 30%, Aurora at 34%, and Jacksonville at 36%, indicating that they share almost the same portion.
3. The Call Charges bar chart shows the annual movement of total call counts. Globally, the total numbers are increasing, and the most charged call type of service is Tech Support, followed by Billing and Sales.
4. Another bar chart, “Year to Year Growth,” shows the evolution of call service charges: 5.48% for 2019, 5.68% for 2020, and 7.56% for 2021. During 2019 and 2020, there was a drop in performance, but in 2021, there was a significant increase in performance.
5. There is a total of 64 employees and 12 managers working across 3 sites (Aurora, Jacksonville, Spokane) in 2 regions (West, South) of the United States for any given year.
6. Over the 4 years, the employee Chantell Tibbits made the highest number of calls (2,200). However, the employee Noella Valentin generated the highest revenue for the company ($33,782).
7. The calls are distributed across 3 Call Types: Sales, Billing, and Tech Support.
8. The call charge has increased annually for all call types, while the total number of calls has consecutively decreased each year.
9. Although the call charge per minute for Billing is the highest for any given year, Tech Support generated the highest revenue.
10. Out of the total calls, 36% of calls are made in the South region, whereas 64% are made in the West region.
11. There are no call records for the Northeast region and the Midwest region.
12. 2018 recorded the highest number of calls (33,057), whereas 2021 recorded the least number of calls (32,846).
13. 2019 recorded the highest number of abandoned calls (2,009), whereas 2021 recorded the least number of abandoned calls (1,983).
14. The site Jacksonville, FL recorded the highest number of calls (47,481), whereas the site Spokane, WA recorded the least number of calls (39,061).
15. Out of the total calls made, there are about 6% of calls that were abandoned for any given year.
16. The average call duration for each year lasts about 12 minutes.
17. The minimum and the maximum wait time for calls for any given year are 0 seconds and 5 minutes, respectively.
18. The average wait time for any call type is 30 seconds.
