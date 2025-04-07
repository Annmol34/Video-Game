# Video-game-sales-analysis
Project analyzing video game sales data by using python.

## Project Title
**Anaysis of Video Game Sales Using Python**

## Short Description
This project analyzes video game sales data using Python and Pandas. It provides sales records for games released before 2005 and after 2005.

## Getting Started

### Prerequisites
- Python 3.x
- pandas
- pymysql
- sqlalchemy
- matplotlib
- seaborn
  
## Installing
Clone the repository to your local machine:
git clone https://github.com/annmol34/video-Game.git
cd video-Game

Running the Tests
To verify that the script functions correctly, follow these steps:
Ensure you have a sample dataset (CSV or from MySQL) containing video game sales data.
Modify the script to read from your data source if necessary.
Execute the script using the following command:
python video_game_sales_analysis.py
Validate the output to ensure:

The dataset is loaded correctly.

The filtering criteria (e.g., games released after 2005) work as expected.

No errors occur during execution.

Ensure your database is set up and accessible.
Place the dataset (vgsales.csv) in the project directory if using the CSV method.
## Importing Libraries
import pandas as pd
import pymysql
from sqlalchemy import create_engine
import matplotlib.pyplot as plt
import seaborn as sns
## Connecting to MySQL
engine = create_engine('mysql+pymysql://user10:123@localhost/ap')
conn = engine.connect()
## Reading Data
 df = pd.read_sql_query("SELECT * FROM data1202.vgsales", conn)
df.head()
## Adding a Time Period Column
SELECT *,
  CASE
    WHEN YEAR <= 2005 THEN 'pre-2005'
    WHEN YEAR > 2005 THEN 'post-2005'
    ELSE NULL
  END AS TimePeriod
FROM data1202.vgsales
## Calculating Average Global Sales by Time Period
 SELECT
  CASE
    WHEN YEAR <= 2005 THEN 'pre-2005'
    WHEN YEAR > 2005 THEN 'post-2005'
    ELSE NULL
  END AS Time_Period,
  AVG(Global_Sales) AS Average_Global_Sales
FROM data1202.vgsales
GROUP BY Time_Period
## Using Pandas for Aggregation
time_period_data = df.groupby('Time Period')['Global_Sales'].mean()
df = pd.DataFrame(time_period_data)
Breakdown of End-to-End Tests
These tests confirm that the data extraction, processing, and filtering functions operate as expected.

Example Test Cases:

Open a CSV or SQL table containing video game sales info.

Filter games released after 2005.

Calculate average global sales for each period.

Display output in a structured table or plot.

## Deployment
To use this script in a production environment:
- Ensure the dataset is securely stored and accessible.
- Optimize data processing if handling large datasets.
- Consider automating the script execution if frequent updates are required.

## Author
**Annmol Shaji**  
Data Analytics Student, Durham College

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

## Acknowledgments
Special thanks to Durham College 
