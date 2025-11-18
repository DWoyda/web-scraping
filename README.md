# Disney Movie Data Scraper & OMDb Enrichment

A Python project that scrapes **Walt Disney Pictures film data** from Wikipedia and enriches it with additional metadata (IMDb, Metascore, Rotten Tomatoes ratings, and genres) from the **OMDb API**.

---

## Project Overview

This project was created as a practical exercise in web scraping.  
It automates the process of collecting movie information directly from [Wikipedia’s List of Walt Disney Pictures films](https://en.wikipedia.org/wiki/List_of_Walt_Disney_Pictures_films), cleans the data, and integrates it with metadata retrieved from the [OMDb API](https://www.omdbapi.com/).

---

## Features

- Scrapes structured movie data (title, release date, budget, box office, etc.)
- Cleans and standardizes raw HTML tables into a Python list of dictionaries
- Converts string dates into Python `datetime` objects
- Enriches each movie with:
   - IMDb rating  
   - Metascore  
   - Rotten Tomatoes rating  
   - Genres list  
- Handles API limits and missing data gracefully  
- Saves results to JSON and CSV for later analysis in Pandas  

---

## Tech Stack

- **requirements.txt**
- **External API:** [OMDb API](https://www.omdbapi.com/)

---

## Environment Variables

Create a `.env` file in the project root:

```bash
OMDB_API_KEY=your_omdb_api_key_here

```
---

## How to run

```bash
# 1️⃣ Install dependencies
pip install -r requirements.txt

# 2️⃣ Run the main scraper
python main.py

# 3️⃣ Check progress (prints every 10 movies)
# Example output:
# 0
# 10
# 20
# ...
```
> If you hit the OMDb API daily limit (1000 requests/day), the script will stop automatically and print:
```pgsql
API limit reached at index (index_number) for ("movie_name")
```

---

## Output example
Each movie record is stored as a dictionary
```python
 {
        "title": "Pinocchio",
        "Directed by": [
            "Ben Sharpsteen",
            "Hamilton Luske",
            "Bill Roberts",
            "Norman Ferguson",
            "Jack Kinney",
            "Wilfred Jackson",
            "T. Hee"
        ],
        "Story by": [
            "Ted Sears",
            "Otto Englander",
            "Webb Smith",
            "William Cottrell",
            "Joseph Sabo",
            "Erdman Penner",
            "Aurelius Battaglia"
        ],
        "Based on": [
            "The Adventures of Pinocchio",
            "by",
            "Carlo Collodi"
        ],
        "Produced by": [
            "Walt Disney"
        ],
        "Music by": [
            "Leigh Harline",
            "Paul J. Smith"
        ],
        "Production company": [
            "Walt Disney Productions"
        ],
        "Distributed by": [
            "RKO Radio Pictures"
        ],
        "Running time": [
            "88 minutes"
        ],
        "Country": [
            "United States"
        ],
        "Language": [
            "English"
        ],
        "Budget": [
            "$2.6 million"
        ],
        "Box office": [
            "$164 million"
        ],
        "Running time (int)": 88,
        "Budget (float)": 2600000.0,
        "Box office (float)": 164000000.0,
        "Release date": [
            "February 7, 1940 ( Center Theatre )",
            "February 23, 1940 (United States)"
        ],
        "Release date (datetime)": "1940-02-07T00:00:00",
        "imdb": "7.5",
        "metascore": "99",
        "rotten_tomatos": "100%",
        "genres": [
            "Animation",
            "Adventure",
            "Comedy"
        ]
    },
```
---
## Next steps
- Load the dataset into MongoDB (JSON-friendly structure)
- Perform deeper EDA and visualization
- Build and interactive dashboard

