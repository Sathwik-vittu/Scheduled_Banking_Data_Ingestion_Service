# Project Overview
This project implements an automated Extract, Transform, Load (ETL) pipeline designed to process global banking data. The pipeline extracts information regarding the top 10 largest banks by market capitalization from a web source, transforms the financial data into multiple currencies using real-time exchange rates, and stores the processed data in both CSV and Database formats for further analysis.

# Features
- **Web Scraping:** Extracts live banking data from Wikipedia using BeautifulSoup.
- **Data Transformation:** Converts Market Capitalization from USD to GBP, EUR, and INR based on provided exchange rate data.
- **Dual Storage:** Saves processed data to a localized CSV file and a SQLite database.
- **Automated Logging:** Tracks every step of the ETL process with timestamps in a code_log.txt file.
- **Database Querying:** Includes pre-configured SQL queries to verify data integrity and extract insights directly from the database.

# Project Structure
- **Automated ETL Pipeline for Banking Data Analysis.ipynb:** The primary Python notebook containing the ETL logic.
- **Largest_banks_data.csv:** The output file containing the final transformed data.
- **Banks.db:** SQLite database storing the processed bank information.
- **code_log.txt:** Log file recording the pipeline's execution history.

# Pipeline Stages
1. **Extraction**
The pipeline targets a Wikipedia archive page to scrape the "By market capitalization" table. It identifies the top 10 banks and captures their names and USD market cap.

2. **Transformation**
Using an exchange rate CSV, the pipeline adds three new columns:
MC_GBP_Billion: Market Cap in British Pounds.
MC_EUR_Billion: Market Cap in Euros.
MC_INR_Billion: Market Cap in Indian Rupees. All values are rounded to two decimal places.

3. **Loading**
The data is loaded into:
  -**CSV:** A flat file for easy distribution.
  -**SQLite:** A relational database table named Largest_banks.

# How to Run
1. **Dependencies:** Ensure you have the following Python libraries installed:
   - **Bash**
       - pip install pandas numpy beautifulsoup4 requests
3. **Execution:** Open the .ipynb file in Jupyter Notebook or VS Code and run all cells.

4. **Outputs:**
Check Largest_banks_data.csv for the processed table.
Check code_log.txt to verify the execution timestamps and process flow.

# Sample Queries Included
The script automatically executes the following queries upon completion:
- **View All:** SELECT * FROM Largest_banks
- **Average Market Cap (GBP):** SELECT AVG(MC_GBP_Billion) FROM Largest_banks
- **Top 5 Names:** SELECT Name FROM Largest_banks LIMIT 5
