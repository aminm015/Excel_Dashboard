Workbook Structure



1. List Sheet
Purpose: Stores reference data for regions and dynamic chart headings

Structure:

Column	Content	Description
B	Regions	Contains region names for filtering
E	Chart Headings	Dynamic titles that reference the Dashboard sheet
Key Features:

Contains 7 regions: All Regions, UK, Germany, Italy, Spain, France, Switzerland

Uses formulas like ="Revenue "&DASHBOARD!$B$2 to create dynamic chart titles

Serves as a data source for dropdown lists and UI elements

2. Data Sheet
Purpose: Contains raw sales transaction data with calculated metrics

Columns:

Salesman

Product (Product 1 or Product 2)

Sale Date

Region

Hours

Sales

Sales Per Hour (calculated: Sales/Hours)

Revenue

Revenue Per Hour (calculated: Revenue/Hours)

Calls

Excellent/Good/Fair/Poor (customer feedback categories)

Total (sum of feedback counts)

Client Satisfaction (weighted score calculation)

Positive/Negative (feedback summaries)

Key Formulas:

Client Satisfaction:
=(K2*5 + L2*4 + M2*3 + N2*2)/(O2*5)
(Weighted average where Excellent=5, Good=4, etc.)

Positive Feedback: =K2+L2

Negative Feedback: =M2+N2

3. Calcs Sheet
Purpose: Aggregates data for dashboard reporting

Columns:

Rank (currently empty)

Product

Salesman

Region

Hours

Sales

Sales PH

Revenue

Revenue PH

Calls

Positive Calls

Negative Calls

TOTAL CLIENT SATISFACTION (dashboard-focused metrics)

Key Features:

Uses SUMIFS formulas to aggregate data by product/salesman/region
Example:
=SUMIFS(Data!E$2:E$121, Data!$B$2:$B$121, $B2, Data!$A$2:$A$121, $C2, Data!$D$2:$D$121, $D2)

Contains dashboard-specific calculations:

=IF(DASHBOARD!B2="All Regions", AVERAGE(Data!P2:P121), AVERAGEIF(Data!D2:D121, DASHBOARD!B2, Data!P2:P121))

Key Functionalities
Dynamic Reporting:

Chart titles update based on DASHBOARD sheet selections

Region filtering through DASHBOARD!B2 cell

Performance Metrics:

Sales and Revenue per hour calculations

Customer satisfaction scoring

Positive/negative call analysis

Data Aggregation:

Summary views by product, salesman, and region

Comprehensive sales performance analysis

Usage Notes
The DASHBOARD sheet (not included in this sample) is the main interface

Set region in DASHBOARD!B2 to control:

Chart headings in the List sheet

Region-specific calculations in the Calcs sheet

Data sheet contains 121 records covering sales from August-November 2023

Calcs sheet contains 71 rows of aggregated data

Maintenance
Data Updates: Add new records to the Data sheet - formulas will auto-calculate

Region Management: Update the List sheet to add/remove regions

Dashboard Controls: Ensure DASHBOARD!B2 contains valid region names matching the List sheet

Note: Circular reference detected in Calcs!N3 (=1-N3). This needs correction to prevent calculation errors.

this readme  wried by ai 
