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
        "title": "Snow White and the Seven Dwarfs",
        "Directed by": [
            "Perce Pearce",
            "William Cottrell",
            "Larry Morey",
            "Wilfred Jackson",
            "Ben Sharpsteen"
        ],
        "Story by": [
            "Ted Sears",
            "Richard Creedon",
            "Otto Englander",
            "Dick Rickard",
            "Earl Hurd",
            "Merrill De Maris",
            "Dorothy Ann Blank",
            "Webb Smith"
        ],
        "Based on": [
            "\"",
            "Snow White",
            "\"",
            "by the",
            "Brothers Grimm"
        ],
        "Produced by": [
            "Walt Disney"
        ],
        "Music by": [
            "Frank Churchill",
            "Leigh Harline",
            "Paul Smith"
        ],
        "Production company": [
            "Walt Disney Productions"
        ],
        "Distributed by": [
            "RKO Radio Pictures"
        ],
        "Running time": [
            "83 minutes"
        ],
        "Country": [
            "United States"
        ],
        "Language": [
            "English"
        ],
        "Budget": [
            "$1.5 million"
        ],
        "Box office": [
            "$418 million"
        ],
        "Running time (int)": 83,
        "Budget (float)": 1500000.0,
        "Box office (float)": 418000000.0,
        "Release date": [
            "December 21, 1937 ( Carthay Circle Theatre )",
            "February 4, 1938 (United States)"
        ],
        "Release date (datetime)": "1937-12-21T00:00:00",
        "imdb": "7.6",
        "metascore": "96",
        "rotten_tomatos": null,
        "genres": [
            "Animation",
            "Adventure",
            "Family"
        ]
```
---
## Next steps
- Load the dataset into MongoDB (JSON-friendly structure)
- Perform deeper EDA and visualization
- Build and interactive dashboard

