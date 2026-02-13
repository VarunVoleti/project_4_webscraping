# 🚀 Project 4: Live Crypto Price Web Scraper
## Automated Bitcoin Price Tracker with Timestamp Logging
### 📌 Project Overview

This project is a live automated web scraper built in Python that continuously tracks the price of Bitcoin from CoinMarketCap and logs the data into a CSV file every 5 seconds.

### It:

Scrapes live Bitcoin price data
Cleans and formats the extracted value
Attaches a real-time timestamp
Appends data continuously to a CSV file
Runs automatically in an infinite loop
This project demonstrates how to build a mini real-time data pipeline using Python.


https://github.com/user-attachments/assets/b8eea9ce-3b5f-4e63-9050-10346104a82a


### 🛠 Technologies Used

Python
requests – HTTP requests
BeautifulSoup (bs4) – HTML parsing
pandas – Data structuring
datetime – Timestamp generation
os – File existence handling
time – Scheduled execution

### 🌐 Data Source

Bitcoin live price page:

**🔗 https://coinmarketcap.com/currencies/bitcoin/**

### The scraper extracts:

Crypto Name
Live Price
Timestamp of extraction

### 🔎 How It Works

1️⃣ Send Request to Website
``
page = requests.get(url)
``

Fetches the live HTML content from CoinMarketCap.

2️⃣ Parse HTML
```
soup = BeautifulSoup(page.text, 'html')
```

### Converts raw HTML into a searchable structure.

3️⃣ Extract Crypto Name
```
crypto_name = soup.find('span', class_="sc-c1554bc0-0 hhUhBo").text
```

4️⃣ Extract Crypto Price
```
crypto_price = soup.find('span', class_='sc-c1554bc0-0 RbQXx base-text').text
```

Then clean it:
```
final_crypto_p = crypto_price.replace('$', '')
```

5️⃣ Add Timestamp
```
date_time = datetime.now()
```

### Captures the exact time of extraction.

6️⃣ Store Data in Pandas DataFrame
```
df = pd.DataFrame([{
    'crypto name': crypto_name,
    'Price': final_crypto_p,
    'Time stamp': date_time
}])
```

7️⃣ Append to CSV Automatically
```
if os.path.exists(file_path):
    df.to_csv(file_path, mode='a')
else:
    df.to_csv(file_path, index=False)


If file exists → append

If not → create new file
```

🔁 Automation Loop
```
while True:
    automated_crypto_pull()
    time.sleep(5)
```

**This runs the scraper every 5 seconds, continuously collecting live data.**

### 📊 Sample Output

**crypto name	Price	Time stamp**
```
Bitcoin price	70,542.27	2026-02-08 04:13:20
Bitcoin price	70,529.07	2026-02-08 04:13:25
Bitcoin price	70,529.07	2026-02-08 04:13:30
```

**The CSV file continuously grows as new price data is appended.**

### 🧠 What This Project Demonstrates

✅ Live web scraping
✅ HTML structure inspection
✅ Real-time data extraction
✅ Data cleaning
✅ Timestamp logging
✅ File handling & conditional appending
✅ Automation using loops & time intervals
✅ Building a simple real-time data collection pipeline

### 💡 Why This Project Is Powerful

**This isn’t just scraping — it’s automated live tracking.**

It simulates how:

Crypto price trackers work
Financial monitoring systems log data
Market data pipelines collect real-time updates
Time-series datasets are built
You essentially built a mini financial data logger.

### ⚠️ Important Considerations

CoinMarketCap’s HTML structure may change.
Running infinite loops should be handled carefully.
This file continuously updates with fresh Bitcoin price data every 5 seconds.

### 🎯 Learning Outcome

**This project bridges:**

**Web Scraping → Data Cleaning → File Handling → Automation → Time-Series Logging**

**It’s a strong demonstration of:**

Practical Python skills
Real-world data collection
Automation mindset
Building reusable scraping functions
