# Learning web scraping for data ectracting 
---

### google colab code file link:
https://colab.research.google.com/drive/1Y_sxl1ms800k7lrZXRmQioEl76ubXNjW?usp=sharing

---

## Features
- Extract data from websites
- Parse HTML content
- Save scraped data to CSV/JSON
- Handle HTTP requests and responses
- Error handling and retry mechanism
- Configurable scraping targets

## Technologies Used
- Python 3.x
- Requests
- BeautifulSoup4
- lxml (optional)
- Pandas (optional)
- Selenium (optional, for dynamic websites)

## Best Practices

- Respect the website's `robots.txt`.
- Avoid sending too many requests in a short period.
- Use appropriate request headers.
- Add delays between requests to prevent server overload.
- Ensure compliance with the website's Terms of Service.

## Dataset Description

The dataset was created by scraping the **Books to Scrape** website, which is designed for practicing web scraping. Data was collected from all **50 catalogue pages**, covering a total of **1,000 books**.

For each book, the following information was extracted:
- **Title** – Name of the book.
- **Price** – Book price (converted to numeric format).
- **Rating** – Book rating converted from text (One–Five) to numeric values (1–5).
- **Availability** – Stock status (e.g., "In stock").
- **Category** – Book category extracted from the individual product page.

After scraping, the data was cleaned using **Pandas** by converting data types, removing the currency symbol from prices, mapping ratings to numerical values, and exporting the final dataset as **`books_data.csv`**.

---

## Author

*Rishav Raj*

---
