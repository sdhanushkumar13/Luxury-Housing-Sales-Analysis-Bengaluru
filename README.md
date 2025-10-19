# Luxury Housing Sales Analysis – Bengaluru Dashboard

## Overview
The Luxury Housing Sales Analysis – Bengaluru Dashboard provides end-to-end analytics on Bengaluru’s luxury real-estate market.
Using Python (ETL), PostgreSQL (Data Warehouse), and Power BI (Visualization), this project explores how factors like amenities, micro-markets, and builder performance influence sales and booking conversions.
The project analyzes 101K property transactions, producing insights that help understand market trends, buyer preferences, and builder efficiency.

## Data Pipeline
### Step 1 – Data Cleaning & Feature Engineering (Python)
Imported 101,000 raw housing records into a Jupyter Notebook (DCL.ipynb).

Cleaned inconsistent numeric and currency values (ticket_price_cr, price_per_sqft).

Handled missing data for amenity_score, booking_flag, and categorical columns.

Created derived fields:price_per_sqft, quarter_number, year, booking_flag (1 = booked, 0 = not booked)

Exported the cleaned dataset as a CSV for SQL loading.

### Step 2 – Load Clean Data into RDBMS (PostgreSQL)
After cleaning, a Python–PostgreSQL connection was established using the SQLAlchemy library.

Created a new PostgreSQL database and table (luxury_housing_cleaned)

Loaded the cleaned dataset directly from Python to PostgreSQL.

Verified successful upload using pgAdmin with the following queries:

-- Row Count

SELECT COUNT(*) FROM luxury_housing_cleaned;

-- Booking Flag Distribution

SELECT booking_flag, COUNT(*) 

FROM luxury_housing_cleaned

GROUP BY booking_flag

ORDER BY booking_flag;

-- Top Builders by Average Ticket Price

SELECT developer_name, ROUND(AVG(ticket_price_cr)::numeric, 2) AS avg_ticket_price

FROM luxury_housing_cleaned

GROUP BY developer_name

ORDER BY avg_ticket_price DESC

LIMIT 10;

### Step 3 – Visualization & Dashboard (Power BI)
Data was connected from PostgreSQL into Power BI to create an interactive 2-page dashboard.

## Tech Stack
TL & Cleaning	 - Python (pandas, numpy, sqlalchemy, psycopg2)

Database	- PostgreSQL (pgAdmin 4)

Visualization	- Power BI

Environment	- Jupyter Notebook, DAX, SQL

## Results & Learnings
Built a complete data pipeline: raw → cleaned → relational → dashboard.

Derived quantitative insights on luxury housing demand and builder performance.

Developed skills in ETL, SQL integration, and Power BI visualization.
