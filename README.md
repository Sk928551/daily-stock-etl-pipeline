# 📈 Daily Stock Price ETL Pipeline with Apache Airflow

This project automates the process of extracting stock data, transforming it using pandas, and uploading the processed data to an AWS S3 bucket. The pipeline is scheduled to run daily using Apache Airflow.

---

## 🚀 Features

- 📊 Extracts 200 days of historical stock price data from the FMP API (Financial Modeling Prep)
- 🧮 Computes 50-day and 200-day Simple Moving Averages (SMA) using pandas
- ☁ Uploads the transformed data to an AWS S3 bucket in CSV format
- ⏰ Scheduled to run daily using Apache Airflow DAG
- ✅ Built and tested using WSL + VS Code environment

---

## 🛠 Technologies Used

- Python 3
- Apache Airflow
- Pandas
- Boto3
- AWS S3
- FMP API
- WSL (Windows Subsystem for Linux)
- VS Code

---

## 📁 Project Structure


Daily_Stock_ETL_Project/ ├── airflow/ │ └── dags/ │ └── daily_stock_etl.py # Airflow DAG ├── .env.example # Sample environment variable file ├── requirements.txt # Python dependencies ├── output/ # (Optional) Sample output CSVs │ └── AAPL_sample.csv ├── README.md # Project documentation

## ⚙️ How It Works

1. **Extract**: Pulls the last 200 days of stock data for AAPL using the FMP API.
2. **Transform**: Calculates SMA_50 and SMA_200 using the `pandas` library.
3. **Load**: Saves the transformed DataFrame as a `.csv` file and uploads it to AWS S3.
4. **Schedule**: Apache Airflow runs this ETL pipeline daily as a DAG.

---

## 📦 Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/Sk928551/daily-stock-etl-pipeline.git
cd daily-stock-etl-pipeline
2. Install Dependencies
bash
Copy
Edit
pip install -r requirements.txt
3. Configure Environment Variables
Create a .env file in the root directory (you can copy from .env.example):

env
Copy
Edit
FMP_API_KEY=your_fmp_api_key_here
AWS_ACCESS_KEY_ID=your_aws_access_key
AWS_SECRET_ACCESS_KEY=your_aws_secret_key
AWS_REGION=ap-south-1
AWS_BUCKET_NAME=daily-stock-etl-data
4. Initialize Airflow
bash
Copy
Edit
export AIRFLOW_HOME=$(pwd)/airflow
airflow db init
5. Start Airflow Services
bash
Copy
Edit
airflow webserver --port 8080
# In another terminal
airflow scheduler
Access the UI at: http://localhost:8080

📂 Output
Uploaded files are saved in your S3 bucket:


s3://daily-stock-etl-data/AAPL_data/YYYY-MM-DD.csv
Each CSV includes:

date

open, high, low, close

SMA_50

SMA_200

📈 Sample Output (CSV Preview)

date	close	SMA_50	SMA_200
2025-04-15	150.23	NaN	NaN
...	...	...	...
2025-04-20	165.88	160.44	158.32 ✅

🧠 Future Enhancements
Add support for multiple stocks (e.g. MSFT, TSLA)

Build a dashboard using Streamlit or Power BI

Add Slack/email notifications

Dockerize the entire project

Store to AWS RDS instead of S3

🙋‍♂️ Author
Aman Kanthiwar
Connect with me on LinkedIn : https://www.linkedin.com/in/aman-kanthiwar-272725240/
GitHub: @Sk928551
