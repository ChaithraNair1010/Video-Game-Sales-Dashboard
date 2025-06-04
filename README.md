# Video-Game-Sales-Dashboard
Power BI Dashboard

🎮 Power BI Video Game Sales Dashboard
An end-to-end BI solution that demonstrates how to extract, transform, and visualize video game sales data using AWS services and Power BI. The report explores sales trends, regional preferences, and genre popularity using dynamic and interactive visuals.

⚙️ Tools & Technologies Used
Tool/Service	Purpose
AWS S3	Cloud storage for the raw video_games.csv file
AWS Glue	Crawler and Data Catalog metadata management
AWS IAM	Role-based access control for Glue & Athena
Amazon Athena	SQL query interface for structured data in S3
Simba ODBC	Connector for integrating Athena with Power BI
Power BI	Data modeling, transformation & storytelling

📁 Dataset
Name: video_games.csv

Size: 16,577 records

Source: Uploaded to Amazon S3

Content: Regional sales data, platform, genre, year of release, and publisher for various video games.

🔄 ETL Process Overview
1. Upload to S3
Created S3 bucket power-bi-project-aws

Uploaded video_games.csv

2. AWS Glue Configuration
Created Glue Database: powerbi_test_aws_db

Defined Glue Crawler: power-bi-crawler

Configured with custom IAM role

Successfully extracted schema and registered metadata

3. Athena Querying
Verified metadata in AWS Data Catalog

Previewed and tested queries using Athena SQL editor

4. Power BI Integration
Installed Simba ODBC driver

Created DSN with appropriate authentication

Loaded data into Power BI and performed data transformation using Power Query

Authentication Used for ODBC:

Username: IAM Access Key ID

Password: IAM Secret Access Key

📊 Visualizations & Report Pages
🔹 Page 1 – Global Overview
A high-level dashboard landing page with sleek dark aesthetics. It features KPIs like:

Total Global Sales

Total Games Published

Number of Platforms
And a line chart depicting Sales Trend Over Years. This page sets the stage for exploring the rest of the report and includes a left-aligned page navigator for smooth multi-page transitions.

🔹 Page 2 – Regional Gaming Leaders: Top Games & Platforms
This page presents region-wise top 5 games and platforms, driven by a slicer. Users can toggle between regions (e.g., North America, Japan) to see local market champions. This supports regional strategy decisions, localization planning, and trend analysis across platforms and franchises.

🔹 Page 3 – Dynamic Radar Chart (Slicer & Unpivoted Data)
A single radar chart visual powered by unpivoted sales data and controlled via a slicer. Users select a region, and the chart updates dynamically to show genre popularity in that region. This approach reduces visual clutter and provides an interactive, scalable solution ideal for business users.

🔹 Page 4 – Radar Charts via Bookmarks (Static Comparison)
An alternate take on genre visualization using five separate radar charts, one for each region. Bookmark navigation allows switching between charts. This is helpful for stakeholders who prefer side-by-side layout control or require static visual storytelling for presentations.

🧠 Business-Driven Charting Strategy
Radar Chart Implementation: Bookmarks vs. Slicer
Criteria	Bookmark Approach	Slicer + Unpivot Approach
📐 Layout Control	Strong (individual layout)	Single dynamic visual
🧩 Scalability	Limited (manual per region)	High (easily adapts to more regions)
🎯 Best For	Static reporting, demos	Interactive dashboards
🛠 Maintenance	Tedious as scope expands	Easier to manage and extend

✅ Conclusion:
Both implementations serve distinct purposes. Bookmarks provide layout control and visual separation, which is ideal for presentations. However, the slicer approach is more dynamic, scalable, and user-centric, aligning better with evolving business needs.

🧼 Data Cleaning & Fixes
Null Handling: Replaced null in sales columns with 0 (as 0 was the most frequent value)

Unit Conversion: Sales originally in millions converted to units (× 1,000,000)

Year Column Issue:

Errors occurred when converting Year to numeric due to dirty values from Athena.

Segregated error rows into a Year Errors table.

Validated using Excel VLOOKUP against original CSV.

Fixed manually and re-integrated valid values back into reporting dataset.

🧠 Key Learnings
IAM configuration and file path setup in AWS are crucial for successful ETL pipelines.

Handling schema mismatches and partial import errors is a real-world necessity.

Visual strategy must be tied to business user behavior — static vs interactive consumption.

Power Query is powerful for shaping and merging multi-source datasets in Power BI.

