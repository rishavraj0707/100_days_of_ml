# 🎬 TMDB Top Rated Movies Dataset using Python API

## 📌 Project Overview

This project demonstrates how to collect **Top Rated Movies** data from **The Movie Database (TMDB) API** using Python. The data is extracted from multiple API pages, converted into a Pandas DataFrame, and finally saved as a CSV dataset.

---

## 🛠️ Technologies Used

- Python
- Pandas
- Requests
- Time Module
- TMDB API

---

## 📖 About TMDB API

TMDB (The Movie Database) provides a free API to access movie, TV show, and actor information.

API Documentation:
https://developer.themoviedb.org/

Example Endpoint:

```
https://api.themoviedb.org/3/movie/top_rated?api_key="YOUR_API_KEYS"&language=en-US&page=1
```

---

## 🔑 API Key

Create your free account on TMDB and generate your own API Key.
Example:
```python
api_key = "YOUR_API_KEY"
```
Replace:
```
YOUR_API_KEY
```
with your own key.

---

### Export dataset.

```python
df.to_csv("movies.csv", index=False)
```

---

## 📈 Output

The final output is a CSV file containing thousands of top-rated movies.

Example:

```
movies.csv
```

---

## 🎯 Learning Outcomes

After completing this project, you will understand:

- REST APIs
- HTTP GET requests
- JSON Parsing
- Working with Pandas
- Data Collection
- Dataset Creation
- Looping through API Pagination
- Exporting Data to CSV

---

## 👨‍💻 Author
*Rishav Raj*