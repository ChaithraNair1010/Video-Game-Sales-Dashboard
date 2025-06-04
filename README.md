# 🎮 Global Video Game Sales Dashboard

An end-to-end Business Intelligence (BI) project to analyze and visualize video game sales data using AWS (S3, Glue, Athena), Power BI, and ODBC integration. The dashboard enables insights into global and regional sales performance by genre, game, and platform.

---

## ⚙️ Tools & Technologies Used

| Tool/Service     | Purpose                                      |
|------------------|----------------------------------------------|
| **AWS S3**        | Storage for raw CSV dataset                 |
| **AWS Glue**      | Crawler and metadata cataloging             |
| **AWS IAM**       | Role-based access for secure ETL            |
| **Amazon Athena** | Query engine for data stored in S3          |
| **Simba ODBC**    | Connector to bring Athena data into Power BI|
| **Power BI**      | Data transformation and interactive visuals |

---

## 📁 Dataset

- **Name:** `video_games.csv`
- **Source:** Uploaded to Amazon S3
- **Records:** 16,577
- **Includes:** Title, Genre, Platform, Year, Publisher, Regional Sales

---

## 🔄 ETL Process Overview

### Step 1: Upload to S3
- Created a bucket: `power-bi-project-aws`
- Uploaded `video_games.csv`

### Step 2: AWS Glue Configuration
- Created Glue database: `powerbi_test_aws_db`
- Setup crawler: `power-bi-crawler`
- Assigned custom IAM role for permission
- Generated a metadata table

### Step 3: Query with Athena
- Previewed records via Athena using SQL
- Validated schema from Glue Data Catalog

### Step 4: Connect to Power BI
- Installed **Simba ODBC** driver
- Created DSN and authenticated via IAM credentials
- Pulled in dataset for modeling and cleaning

---

## 🧽 Data Cleaning Highlights

- Replaced null values in sales columns with 0
- Converted sales figures from millions to unit counts
- Fixed Year column issues by isolating invalid entries, validating via Excel, and reintegrating clean rows
- Applied **Power Query transformations** and unpivoted regional sales for dynamic slicing

---

## 📊 Report Pages & Visualizations

### 🔹 Page 1 – **Overview Dashboard**
Features KPIs like:
- Total Global Sales
- Total Games
- Total Platforms
- Total Publishers
Includes a line chart to display **Sales Trend Over Years**. Serves as the landing page with a **page navigator** at the bottom.

---

### 🔹 Page 2 – **Regional Gaming Leaders**
Visualizes:
- Top 5 Games
- Top 5 Platforms  
Region selection via **button-based slicer**. Highlights dominant franchises and platforms in each region for market-specific insight.

---

### 🔹 Page 3 – **Radar Chart (Slicer-Based Approach)**
Built using **unpivoted data**.  
Allows dynamic filtering of genre-wise sales using a **single radar chart** controlled by a region slicer.  
Ideal for interactive and scalable analysis.

---

### 🔹 Page 4 – **Radar Chart (Bookmark Approach)**
Contains five separate radar charts — one per region — navigated via **bookmark buttons**.  
Useful for static presentations and storytelling when layout control is preferred.

---

## 📊 Charting Strategy: Bookmark vs Slicer

| Feature                 | Bookmark Charts      | Slicer + Unpivot        |
|------------------------|----------------------|--------------------------|
| Visual Count           | Multiple visuals     | One visual               |
| User Interactivity     | Low                  | High                     |
| Maintenance            | Tedious              | Scalable & flexible      |
| Best For               | Storytelling/presentations | Exploratory analysis |

**🔍 Insight:**  
While bookmarks provide structure and control, slicers offer a better UX for growing datasets and evolving needs.

---

## 🧠 Key Learnings

- Importance of IAM, bucket policies & schema matching in AWS pipelines
- Power Query is powerful for transformation and error isolation
- Unpivoting enables scalable, user-driven filtering in reports
- Effective storytelling in dashboards depends on audience needs

---

## 🚀 Future Improvements

- Publish to Power BI Service
- Enable scheduled refresh via Athena
- Incorporate predictive analytics (e.g., future genre trends)
- Add tooltips, page navigation icons, and usage metrics

---

## 📎 Files Included

- `Video Games Report.pbix` – Final Power BI Report  
- `video_games.csv` – Raw dataset  
- `README.md` – Project overview and documentation

---

Feel free to clone, explore, and build upon this project!

> _For questions or suggestions, reach out via GitHub Issues._

