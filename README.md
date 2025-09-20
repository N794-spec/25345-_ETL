# 25345-_ETL
API KEY --- 56d73215dcd34cc352ed6804c37e1762

1. The ETL Code (etl_code.py)
This script's job is to prepare the data. It follows the classic ETL (Extract, Transform, Load) pattern.

Extract : It connects to an external data source, the Federal Reserve Economic Data (FRED) API, to pull the latest U.S. Non-Farm Payrolls data. This is the raw material.

Transform : The raw data isn't ready for analysis. This step cleans it up and enriches it. It uses the pandas library to calculate key metrics that analysts will want to see, such as the month-over-month absolute and percentage changes in employment.

Load : Once the data is transformed into a clean, useful format, this step loads it into a permanent, structured storage: a PostgreSQL database. This database acts as a data warehouse—a central source of truth for the dashboard. The refactored code uses the highly efficient copy_from command, the recommended method in the PostgreSQL documentation for bulk-loading data quickly.




2. The Dashboard Code (dashboard_code.py)
This script's job is to present the data to the end-user. It's a web-based, interactive Business Intelligence dashboard built with Streamlit.

Database Connection : It connects directly to the PostgreSQL database that the ETL script populated. The refactored code uses a connection pool, which is a critical performance optimization that reuses database connections instead of creating new ones for each user, making the app faster and more scalable.



OLAP Analysis : This is the core of the dashboard. It allows users to perform Online Analytical Processing (OLAP) without writing any code. It lets them:

Slice: Look at a specific time period (e.g., jobs created between 2010 and 2020).

Dice: Filter on multiple criteria (e.g., view growth trends for Q4 only).

Roll-Up: Aggregate data to a higher level (e.g., view annual growth instead of monthly).

Drill-Down: Investigate high-level numbers in more detail (e.g., explore the specific months that contributed to a record-breaking year).




Interactive Visualization : Using the Plotly library, the script turns the data and analysis into interactive charts and graphs. Users can hover over data points, zoom in on time periods, and select different views, allowing them to explore the data and discover insights on their own.
