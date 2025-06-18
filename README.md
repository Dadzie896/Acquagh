ACQUARIOUS OIL  TRANSFER PROJECT 
PROJECT OVERVIEW Objective This project investigates the root causes of delays in the oil transfer process and proposes a strategic solution plan. Through data analysis of operational workflows, resource allocation, and process efficiency, this project seeks to identify trends and key areas for improvement.
Scope The analysis covers:
•	Current transfer and handling protocols
•	Staffing and equipment utilization patterns
•	Service delay patterns and external influencing factors
•	Operational bottlenecks and improvement opportunities
Methodology
•	Data Collection: Gathering logs, staffing data, equipment status, and service records.
•	Analysis: Identifying delay trends and correlating them with operational factors.
•	Root Cause Analysis: Identifying the primary contributors to the delay.
•	Solution Proposal: Recommending solutions, such as process optimization and resource allocation.
Data Source Data set provided by the client as a CSV file, which was downloaded and processed for analysis.
Tools
1.	Microsoft Excel: Utilized for preliminary data correction and initial review of the dataset.
EXPLORATORY DATA ANALYSIS (EDA) In this EDA phase, we will examine the human resource dataset to address key operational questions that can impact the efficiency and reliability of oil transfer services. These insights will help identify potential areas for improvement and facilitate data-driven decision-making. Key Questions to Address:
1.	Total Number of Truck Drivers
o	Determine the number of truck drivers to assess if current staffing meets operational demands.
2.	Number of Efficient Trucks
o	Identify the count of trucks classified as efficient to understand fleet reliability and potential operational constraints.
3.	Coverage Areas (Distances in Kilometers)
o	Analyze distances covered to evaluate the geographic reach and the adequacy of logistical support across areas served.
4.	Truck Breakdown and Maintenance Frequency
o	Assess the frequency of truck breakdowns and scheduled maintenance to pinpoint areas needing additional support or preventive measures.
These insights from EDA will contribute to optimizing workforce planning, improving fleet management, and enhancing the overall efficiency of oil transfer services.
SQL
SELECT COUNT(*) AS TotalTruckDrivers
FROM employees
WHERE job_title = 'Truck Driver';
SELECT COUNT(*) AS EfficientTrucks FROM trucks WHERE efficiency_status = 'Efficient';
SELECT truck_id, SUM(distance_in_km) AS TotalDistanceCovered FROM deliveries GROUP BY truck_id;
SELECT truck_id, COUNT(*) AS BreakdownCount FROM maintenance_log WHERE maintenance_type = 'Breakdown' GROUP BY truck_id;
SELECT truck_id, COUNT(*) AS MaintenanceCount FROM maintenance_log GROUP BY truck_id;
SELECT COUNT(*) AS EmployeesHiredInLastYear FROM employees WHERE hire_date >= DATE_SUB(CURDATE(), INTERVAL 1 YEAR);
SELECT YEAR(hire_date) AS Year, MONTH(hire_date) AS Month, COUNT(*) AS EmployeesHired FROM employees GROUP BY YEAR(hire_date), MONTH(hire_date) ORDER BY YEAR(hire_date) DESC, MONTH(hire_date) DESC;
RESULTS
•	Truck Drivers: 120 drivers employed, potential shortages during peak periods.
•	Efficient Trucks: 85 out of 150 trucks are efficient, and 65 trucks are underperforming.
•	Coverage Areas: Average distance of 250 km daily; some trucks cover 450 km.
•	Truck Breakdowns: Average of 2.5 breakdowns per month; some trucks need urgent replacement.
•	Employee Hiring: 40 new employees hired, 15 truck drivers in the past year.
•	Hiring Trend: 15 truck drivers hired in the last quarter, indicating demand or turnover.
•	Insight: Fleet and workforce optimization are needed for efficiency and cost reduction.
RECOMMENDATIONS
Based on the Exploratory Data Analysis (EDA) and insights derived from the SQL queries, here are some recommendations to improve the efficiency and reliability of the oil transfer service:
1.	Optimize Workforce Allocation
•	Recommendation: Based on the total number of truck drivers, assess if the current workforce is sufficient to meet demand, especially during peak periods. If there are shortages, consider hiring additional drivers or redistributing work hours to avoid delays.
•	Actionable Steps:
o	Evaluate whether the number of drivers matches the number of trucks and expected delivery volumes.
o	Consider flexible staffing models, such as on-demand or seasonal hires, to meet peak service needs.
2.	Fleet Management and Maintenance Optimization
•	Recommendation: Analyze the number of efficient trucks and the breakdown/maintenance frequency. If a significant percentage of trucks are not efficient, or if maintenance is frequent, consider upgrading or replacing older trucks. Actionable Steps:
o	Perform a detailed analysis of trucks' age, usage patterns, and maintenance logs to identify inefficiencies.
o	Develop a preventive maintenance schedule to reduce breakdowns, including replacing parts before they fail.
o	Investigate leasing or acquiring newer, more efficient trucks if maintenance costs are too high for older ones.
