#  ApexBank HR Workforce Analytics Dashboard
# Dashboard powered by Power BI | Employee Retention, Compensation, Leave Utilization & Data Quality Analysis
# Period: Full Year Workforce Snapshot
----
# Table of Contents
----
- [Analysis Overview](#analysis-overview)
- [Objective](#objective)
- [Data Source](#data-source)
- [Preparation Tools](#preparation-tools)
- [Data Processing](#data-processing)
- [Skills Demonstrated](#skills-demonstrated)
- [Insights](#insights)
- [Critical Finding: The Operations Attrition Gap](#critical-finding-the-operations-attrition-gap)
- [Recommendations](#recommendations)
- [Dashboard](#dashboard)
- [Conclusion](#conclusion)

----

## Analysis Overview

This project presents a two-page HR Workforce Analytics Dashboard built for ApexBank Plc, a fictional Nigerian banking institution, to examine employee headcount, gender distribution, compensation, performance, tenure, attrition, and leave utilization across a 2,000-employee dataset.

By combining an executive KPI overview with a deeper compensation, retention, and data-quality analysis, this dashboard transforms a raw, deliberately messy HR dataset into a decision-ready business intelligence tool — surfacing not only workforce composition, but where attrition risk is concentrated and why.

----

## Objective

The primary objectives of this analysis are:

- Determine total and active headcount, broken down by department and grade level.
- Assess gender distribution across the bank and identify the department with the highest female representation.
- Analyze average compensation by grade level and flag salary-band inconsistencies.
- Evaluate average performance ratings by department.
- Measure average employee tenure and identify retention patterns by department.
- Calculate attrition rate overall and by department, and investigate the drivers behind departments with elevated turnover.
- Quantify annual leave utilization by grade level.
- Audit the dataset for data-quality issues and quantify their impact before analysis.

----

## Data Source
----
- Source Type: Fictional Internal HR Employee Dataset (ApexBank Plc)
- Total Records Loaded: 2,080 raw records, cleaned to 2,000 unique employees after removing 80 duplicate Employee IDs
- Total Active Employees: 1,696
- Total Exited Employees: 304
- Departments Covered: Retail Banking, Human Resources, Risk & Compliance, Finance & Accounts, Information Technology, Customer Service, Operations, Corporate Banking, Unknown
- Grade Levels Covered: Director, Manager, Senior, Mid-Level, Junior
- Metrics Tracked: Headcount, Gender Split, Gross Salary, Performance Rating, Tenure, Attrition Rate, Annual Leave Utilization, Data Quality Issue Rate

----

## Preparation Tools
----
The following tools were used across the data preparation, modelling, and visualisation pipeline:
- Power BI Desktop: Primary dashboard development, DAX calculations, and interactive visualisations.
- Power Query: ETL (Extract, Transform, Load) operations for data cleaning and shaping.
- DAX (Data Analysis Expressions): Custom measures for attrition, tenure, gender representation, and data quality reporting.
- Microsoft Excel: Initial dataset review and validation.
- GitHub: Version control, portfolio hosting, and documentation.

----

## Data Processing
----
The data processing workflow followed a structured ETL and data-quality-first approach:

### Data Extraction & Loading:
Raw HR data was extracted from a single Employee_Data table containing 2,080 records and loaded into Power BI via Power Query, covering demographic, compensation, performance, and employment-status fields.

### Data Cleaning & Transformation:
- Removed 80 duplicate Employee ID records (rows sharing the same ID with slightly different name spellings), reducing the dataset from 2,080 to 2,000 unique employees.
- Standardised inconsistent categorical formatting across Gender, Marital Status, and Employment Status fields (e.g., "M" / "Male" / "MALE" / "male" all appearing as separate raw values).
- Standardised inconsistent date formats across Date of Birth and other date fields.
- Cleaned salary field errors including currency symbols, comma formatting, blank values, and negative values.
- Resolved inconsistent department naming and flagged blank department entries as "Unknown."
- Identified and quantified name-field errors (extra spacing, "@" symbol substitutions) and invalid/incomplete email formats.

### Data Modeling:
- Built a single-table employee model with calculated columns and DAX measures layered on top for attrition, tenure, and representation analysis.
- Created DAX measures including Attrition Rate (overall and by department), Average Tenure, Top Female Department, Top Female Count, and Top Female Department Percentage.
- Built a dedicated Data Quality Summary table quantifying every dirty-data category as both a row count and a percentage of the cleaned dataset.

----

## Skills Demonstrated
----
- Data Cleaning: Deduplication logic, categorical standardisation, date format resolution, currency/salary field cleaning.
- Data Analysis: Attrition analysis, compensation analysis, tenure analysis, gender representation analysis.
- Business Intelligence: KPI design, two-page interactive dashboard development, cross-filtering slicers by Department, Grade Level, and Gender.
- DAX & Power Query: Custom measures using CALCULATE, VAR, DIVIDE, TOPN, and ALL() to correctly scope department-level vs. bank-wide calculations.
- Data Visualisation: KPI cards, donut charts, ranked bar charts, and a formatted data-quality table.
- Root-Cause Investigation: Testing tenure and compensation as competing explanations for elevated departmental attrition before drawing conclusions.
- Documentation: Professional GitHub README writing and structured portfolio presentation.

----

## Insights

----

### Executive Overview

----

![Executive Overview](https://raw.githubusercontent.com/osondubc-star/apexbank-hr-workforce-dashboard/main/Executive_overview.png)

The executive overview shows ApexBank employs **2,000 total employees**, of whom **1,696 are active** and **304 have exited** — resigned, terminated, or otherwise separated. This puts the overall **attrition rate at 15.2%**, which sits within the stable 10–18% range typical for the banking sector, though close enough to the upper bound to warrant ongoing monitoring. Average gross salary across the bank sits at **₦1.01M**, with an average performance rating of **3.04**.

Workforce distribution by department (active employees) shows **Retail Banking (216)** as the largest team, closely followed by Human Resources and Risk & Compliance (211 each), while 43 employees fall under "Unknown" due to blank department entries. Grade-level distribution is fairly even, ranging from 371 Seniors down to 319 Directors. Gender split is close to balanced at **51% Male / 49% Female**, with **Risk & Compliance** holding the highest female representation — 131 employees, or 13.4% of all female staff bank-wide. Average performance ratings cluster tightly between 2.9 and 3.1 across all departments.

----

### Workforce, Compensation & Retention

----

![Workforce Overview](https://raw.githubusercontent.com/osondubc-star/apexbank-hr-workforce-dashboard/main/Workforce_overview.png)

|    Metric                        |     Value          |
|------------------------------------|---------------------|
|     Active Employees               |     1,696            |
|     Attrition Rate                 |     15%               |
|     Leave Utilization Rate         |     51.2%             |
|     Average Tenure                 |     9 years           |

Average gross salary rises sharply by grade level — **Directors earn ₦2.4M** on average, compared to **₦1.2M for Managers**, **₦0.8M for Seniors**, **₦0.5M for Mid-Level**, and **₦0.3M for Junior** staff. Annual leave utilization is well-balanced across grades (49.7%–54.3%), with **Seniors making the most use of their entitlement (54.3%)** and Directors the least (49.7%) — no red flags here.

Attrition by department tells a different story: **Operations leads at 19%**, followed by **Corporate Banking (17%)** and **Human Resources (17%)** — all noticeably above the 15.2% company average. **Information Technology sits lowest at 12%**. Average employee tenure, by contrast, is remarkably consistent across every department at **9 years** (Retail Banking dips slightly to 8), ruling out tenure as an explanation for the attrition gap.

----

## Critical Finding: The Operations Attrition Gap

----

During the analysis, a pattern emerged that went beyond a simple attrition ranking:

> **Operations, Corporate Banking, and Human Resources — the three departments with the highest attrition rates — all earn below the company's average gross salary, while several lower-attrition departments earn at or above it.**

This is not proof that compensation drives attrition on its own. But it is a pattern worth sitting with, because these three departments are not peripheral functions — they are among the departments that keep a bank running day to day. Losing people from them faster than average carries real business consequences:

- **Institutional knowledge loss** — Processes and client relationships walk out the door with departing staff.
- **Recruitment and onboarding cost** — Repeated hiring and retraining cycles quietly consume budget.
- **Operational strain** — Remaining staff absorb the workload gap, risking burnout and further attrition.
- **Compounding risk** — If left unaddressed, attrition trending toward the 18% danger threshold could tip a "stable" metric into a genuine retention crisis.

This finding demonstrates that a dashboard's job isn't just to report a number — it's to test competing explanations (tenure vs. compensation) before pointing leadership toward where to look next.

----

## Recommendations

----

Based on the analysis across all dimensions, the following strategic recommendations are proposed:

**Investigate Attrition in Operations, Corporate Banking, and HR**
- Conduct exit interviews and engagement surveys specifically targeting these three departments to understand root causes beyond what the dataset can show.
- Treat the compensation pattern as a hypothesis to test, not a confirmed cause — review workload, career progression, and management practices alongside pay.

**Monitor Overall Attrition Closely**
- At 15.2%, the bank sits only 3 points below the 18% danger threshold — establish a regular monitoring cadence rather than treating the current rate as permanently safe.

**Audit and Standardize Data Entry Going Forward**
- With 100% of records affected by inconsistent Gender, Marital Status, Employment Status, and Date formatting, implement dropdown-based data entry standards to prevent recurrence.
- Resolve the 50 blank department entries and enforce mandatory department assignment at the point of hire.

**Review Compensation Structure by Department**
- Benchmark Operations, Corporate Banking, and HR salaries against market rates and against lower-attrition departments to determine whether a pay adjustment is warranted.

**Maintain Leave Utilization Balance**
- Current leave utilization is healthy and balanced across grades — continue monitoring to ensure no grade level becomes an outlier over time.

----

## Dashboard

![Dashboard Suite](https://raw.githubusercontent.com/osondubc-star/apexbank-hr-workforce-dashboard/main/Summary.png)

- Espresso-brown KPI cards: Key headline metrics for quick scanning
- Donut chart: Gender distribution breakdown
- Ranked bar charts: Department and grade-level comparisons for headcount, salary, attrition, leave utilization, and tenure
- Data Quality Summary table: Row count and percentage impact of every dirty-data category identified during cleaning

----

## Conclusion

----
This ApexBank HR Workforce Analytics Dashboard confirms that the bank's workforce is fundamentally stable — a 15.2% attrition rate within the healthy range for banking, balanced leave utilization, and consistent tenure across departments. However, the analysis surfaces a meaningful pattern that warrants leadership attention: Operations, Corporate Banking, and Human Resources are losing staff faster than the company average, and preliminary investigation points toward compensation as a possible contributing factor — though not a confirmed one.

Most critically, this project demonstrates a discipline beyond surface-level reporting: ruling tenure out and flagging compensation as worth investigating further, rather than jumping to either conclusion. This is the difference between a dashboard that shows numbers and one that guides a real business decision.

By acting on the recommendations surfaced in this dashboard, HR leadership can address both the data-quality gaps at the point of entry and the retention risk building quietly in three of the bank's core departments.

----


**Blessing Osondu**
 Data Analyst | Power BI · Excel · SQL

[LinkedIn](https://www.linkedin.com/in/blessing-osondu-ba4687300)
 
 [GitHub](https://github.com/osondubc-star)
 
