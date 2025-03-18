# Stock-Web-Scrapping-Project
This web scraping project monitors stock prices and sends email notifications when the stock reaches or falls to a predefined target price

## Project Overview
This is a Python-based web scraping project that monitors the stock price of Ghalemdi Hydro Limited (GHL) on the ShareSansar website. The script checks the stock price daily, logs the data into a CSV file, and sends email notifications to specified recipients if the price exceeds $350. The project is designed for automated stock price tracking, making it useful for investors or financial enthusiasts who want to stay updated on specific stock thresholds.

## Features
- Web Scraping: Scrapes the current stock price of GHL from ShareSansar using requests and BeautifulSoup.
- Data Logging: Appends the stock title, price, and date to a CSV file (NepseWebScrapperDataset.csv) for historical tracking.
- Email Notifications: Sends an email alert to specified recipients when the stock price exceeds $350 using smtplib.
- Automated Monitoring: Runs continuously, checking the price every 24 hours with a sleep timer.

## Prerequisites
Before running the project, ensure you have the following:

- Python 3.12 or higher installed.
- Required Python libraries (install via pip):
  - requests
  - beautifulsoup4
  - smtplib (part of Python’s standard library)
  - time (standard library)
  - datetime (standard library)
  - csv (standard library)
  
## Setup Instructions  
  1.Clone the Repository:
    - git clone https://github.com/your-username/stock-price-monitor.git
    - cd stock-price-monitor 
    
  2. Install Dependencies:
    -Install the required Python libraries using pip:
       pip install requests beautifulsoup4  
       
  3. Set Up Email Authentication:
    - The script uses Gmail’s SMTP server to send emails. You’ll need a Gmail account and an App Password (since Google no longer supports "less secure apps").
    - To generate an App Password:
      - Go to myaccount.google.com > Security > 2-Step Verification (enable it if not already).
      - Under "2-Step Verification," find App passwords, generate a new one for "Mail," and copy the 16-character password.
    - Replace the password variable in the send_email function with your App Password:
  python
    password = "your-app-password-here"  
    
  4. Update Email Recipients:
  In the send_email function, modify the receivers list to include the email addresses you want to notify:
  python
    - receivers = ["your-email@gmail.com", "another-email@gmail.com"]

## File Structure

- stock_price_monitor.py: The main Python script containing the web scraping, CSV logging, and email notification logic.
- NepseWebScrapperDataset.csv: The output CSV file where stock data is logged (generated automatically when the script runs).
- README.md: This documentation file.

## Usage
  1.Run the Script: Execute the script in your terminal or IDE:
  
    python stock_price_monitor.py
    The script will:
      - Scrape the stock price of GHL from ShareSansar.
      - Log the title, price, and date to NepseWebScrapperDataset.csv.
      - Send an email if the price exceeds $350.
      - Sleep for 24 hours before checking again.
      
  2. Monitor Output:
    - Check the terminal for logs (e.g., "Current Stock Price: $312.0", "Data appended to CSV").
    - Open NepseWebScrapperDataset.csv to view the logged data with columns: Title, Price, and Date.
     
  3.Stop the Script:
    -Press Ctrl+C in the terminal to stop the script.
    
## Example Output

When the script runs, you’ll see output like this in the terminal:

  - Starting the price checker...
  - Title: Ghalemdi Hydro Limited(GHL )
  - Current Stock Price: $312.0
  - Data appended to CSV
  - Price is under $350 or not found - no email sent
  - Sleeping for 24 hours...
  
If the price exceeds $350, an email will be sent with the subject "Price Alert: Over 350!" and a body like:

  The price of GHL just hit $360.0 - it's above 350!
  
## Key Details
    - Stock Monitored: Ghalemdi Hydro Limited (GHL) on ShareSansar.
    - Price Threshold: Email notifications are sent if the price exceeds $350.
    - Check Frequency: Every 24 hours (86,400 seconds).
    - CSV Format:
    - Columns: Title, Price, Date.
    - Example row: Ghalemdi Hydro Limited(GHL ), 312.0, 2025-03-17.
