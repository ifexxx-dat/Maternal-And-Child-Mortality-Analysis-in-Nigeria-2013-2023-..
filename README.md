Nigerian Maternal And Child Health Dashboard (2013-2023)

Project Overview

This project analyzes 10 years of maternal and child health data across Nigeria’s 37 states to track progress, identify disparities, and evaluate the effectiveness of healthcare interventions. Using Power BI, I built a two-page interactive dashboard that tells the story of Nigeria’s healthcare journey from 2013 to 2023 the wins, the gaps, and where urgent action is needed.

The Core Question: Has Nigeria made meaningful progress in maternal and child health over the past decade, and who is being left behind?

Dataset

Source: Synthetically generated dataset based on real Nigeria health trends and patterns

Reference Data: WHO Global Health Observatory, UNICEF, Nigeria Demographic and Health Survey (NDHS)

Coverage: All 37 states (36 states + FCT) across 5 survey years (2013, 2015, 2018, 2021, 2023)

Tables: 2 CSV files

Health Indicators Table (~925 rows, 14 columns)
Population Data Table (185 rows, 5 columns)

Health Indicators Tracked:

- Under-5 mortality rate, infant mortality rate, neonatal mortality rate
- Maternal mortality ratio
- Vaccination coverage (DPT3 and Measles)
- Skilled birth attendance and antenatal care (4+ visits)
- Stunting, wasting, underweight prevalence
- Exclusive breastfeeding rates

Data Quality Issues (Intentional for cleaning practice):

- Inconsistent state name formatting (“Lagos” vs “LAGOS” vs “Lagos State”)
- 8% missing values in mortality columns
- Population figures in thousands (required scaling)
- Duplicate rows

Tools & Technologies

- Power BI Desktop - Dashboard development and visualization
- Power Query (M) - Data cleaning and transformation
- DAX - Calculated measures and analytics


Project Workflow

1. Data Cleaning (Power Query)

- Standardized inconsistent state names using Capitalize Each Word and Replace Values
- Removed ~8% null rows from mortality columns
- Multiplied all population columns by 1,000 to correct data scale
- Removed duplicate rows
- Fixed data types (years as whole numbers, rates as decimals)
- Created composite key column (StateYear) by merging State and Year columns

2. Data Modeling

- Built a Calendar table from scratch to enable time intelligence functions
- Created relationships between three tables (Health, Population, Calendar)
- Used composite key (StateYear = “Lagos-2023”) to establish clean one-to-one relationship between Health and Population tables
- Marked Calendar table as Date table for DATEADD functions to work

3. DAX Measures (10 Total)

Time Intelligence:

- Previous Year U5 Mortality
- YoY Change % U5 Mortality
- U5 Mortality % Improvement Since 2013
- Previous Year Maternal Mortality
- YoY Change % Maternal Mortality
- Maternal Mortality % Improvement Since 2013

Rankings & Comparisons:

- State Rank U5 Mortality (using RANKX)

Weighted Calculations:

- Weighted National U5 Mortality Average (using SUMX)

Target Analysis:

- Gap From WHO Target

Impact Measurement:

Estimated Lives Saved Since 2013

4. Dashboard Design

Page 1: National Overview - Progress and Challenges

A fixed executive summary showing Nigeria’s overall national story from 2013-2023. No slicers - everyone sees the same definitive national narrative.

The Visuals:

5 KPI cards (U5 mortality, YoY change, maternal mortality, vaccination coverage, lives saved)
Line chart: Under-5 mortality trend with WHO target reference line
Line chart: Maternal mortality trend with SDG target reference line
Clustered column chart: Vaccination coverage over time (DPT3 vs Measles)
Area chart: Skilled birth attendance and antenatal care trends
Key insight text box summarizing main findings

Page 2: Regional Analysis - Where Are the Disparities?

An interactive deep-dive into state and regional inequalities. Fully filterable by year and geopolitical zone.

Visuals:

Year slicer and geopolitical zone filter
Filled map: States colored by mortality rate (green to red heat map)
Table: Top 10 best performing states
Table: Bottom 10 worst performing states
Clustered bar chart: Mortality gap from WHO target by geopolitical zone
Clustered bar chart: Vaccination coverage vs mortality by zone
Key insights text box with findings and recommendation

Key Findings

National Progress (2013-2023):

- Under-5 mortality improved by 13.9% (134 → 115 per 1,000 live births)
- Estimated 3.1 million children’s lives saved through healthcare improvements
- Vaccination coverage (DPT3) increased from ~50% to 72%
- Maternal mortality declined by ~11% (682 → 610 per 100,000 live births)
- Skilled birth attendance increased to 68%
  
Critical Challenges:

- Nigeria remains 4x above WHO under-5 mortality target (115 vs 25 per 1,000)
- 3x gap between best performing state (Rivers: 65) and worst (Kogi: 196)
- Northern states have mortality rates 2-3x higher than Southern states
- 12 states still have mortality rates above 150 per 1,000

Key Correlation Discovered
States with higher vaccination coverage consistently show lower child mortality rates - clear evidence that immunization programs save lives.


Challenges & Solutions

Problem: Population data was in thousands, breaking the Lives Saved calculation
Solution: I Multiplied all population columns by 1,000 in Power Query. Lives Saved jumped from 3,150 to 3.1 million

Problem: Many-to-many relationship between Health and Population tables caused wrong matches
Solution: I Created composite key (StateYear = State & “-” & Year) for a clean one-to-one relationship

Problem: Time intelligence functions errored without a proper Date table
Solution: I Built Calendar table from scratch, marked as Date table, connected to both fact tables

Problem: Inconsistent state names broke relationships across tables
Solution:I Standardized all names using Power Query transformations before creating relationships

What I Learned

- Data cleaning is 80% of the work 
- Relationships are the backbone of accurate analysis
- Filter context in DAX is everything 
- Context transforms numbers: 14% improvement is abstract, “3.1M lives saved” is real
- Design matters as much as analysis bad visuals kill good insights
- Done beats perfect ship it, reflect, improve

How to Use This Project

1. Download Power BI Desktop (free from Microsoft)
1. Clone or download this repository
1. Open Nigeria_Maternal_Child_Health_Dashboard.pbix
1. Explore Page 1 for the national overview
1. Use Page 2 slicers to filter by year and region

Future Improvements

- Add drill-through pages for individual state profiles
- Implement What-If parameter (impact of achieving 90% vaccination)
- Add bookmarks for switching between mortality and maternal health focus
- Build pharmaceutical access companion dashboard
- Integrate Python for forecasting 2025-2030 trend

About

Built by Okoli Ifechukwu - Pharmacy Student | Healthcare Data Analyst

This is my first complete Power BI project, built as part of my journey learning data analytics in public. Every mistake, debug session, and breakthrough is documented across my LinkedIn and Medium.

Connect with me:

- LinkedIn: http://linkedin.com/in/ife-okoli
- Medium: https://medium.com/@ifechukwuokoli97 
sed on WHO, UNICEF, and Nigeria DHS published statistics. Synthetic dataset generated for learning purposes.*
