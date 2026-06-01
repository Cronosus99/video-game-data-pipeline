# Video Game Data Pipeline (Data Engineering Project)

**Author:** Kevin Danh  
**Program:** Master of Data Science – Bellevue University  
**Course:** DSC 540: Data Preparation  

## Project Summary

This project analyzes trends in the video game industry by integrating data from three different source types: a flat file, a public API, and a scraped website. It explores factors such as sales, performance, awards, and ratings to uncover insights about the global video game market. Each source is cleaned and transformed independently, then merged into a single relational database and explored through visualizations. The focus of this project is data acquisition, wrangling, and integration rather than predictive modeling.

## Project Type
Data Engineering | Data Wrangling | Multi-Source Integration

## Data Sources

This project combines three distinct source types, related through common keys such as game name, genre, platform, and publisher:

- **Flat file (CSV) – Kaggle:** Global video game sales and performance data from 1980 to 2016.  
  https://www.kaggle.com/datasets/modiash/video-game-sales-and-performance-data
- **API – RAWG.io:** Comprehensive video game metadata including descriptions, ratings, playtime, genres, and platforms.  
  https://rawg.io/apidocs
- **Website – Wikipedia:** Lists of Game of the Year awards given to games across different regions and criteria, parsed directly from the saved HTML using BeautifulSoup.  
  https://en.wikipedia.org/wiki/List_of_Game_of_the_Year_awards

### Relationships
The three sources are linked through shared attributes (game name, genre, platform, publisher), enabling analysis of how sales and performance relate to awards and critical reception, trends across genres and platforms over time, and patterns in ratings, playtime, and global popularity.

## Methods

### Data Extraction
- Loaded flat file data with Pandas
- Scraped and parsed structured HTML tables from a saved Wikipedia page with BeautifulSoup
- Queried the RAWG API across multiple pages and flattened nested JSON responses

### Data Cleaning & Transformation
- Applied at least five transformation steps to each source, including:
  - Replacing and standardizing headers
  - Fixing data types and inconsistent casing
  - Removing duplicates and unnecessary columns
  - Handling missing values
  - Reformatting nested or non-tabular fields into clean columns

### Data Integration & Storage
- Loaded each cleaned dataset into a SQLite database as separate tables (kaggle, wiki, api)
- Joined the tables with SQL into a unified dataset
- Created visualizations, including charts spanning multiple joined sources

## Key Skills Demonstrated

**Data Engineering & Wrangling**
- Multi-source data extraction (flat file, web scraping, REST API)
- API pagination and nested JSON flattening
- Data cleaning and standardization across heterogeneous sources
- Relational data modeling and SQL joins
- Database loading and querying with SQLite

**Tools & Technologies**
- Python
- Pandas
- NumPy
- BeautifulSoup
- urllib / REST API
- SQLite (sqlite3)
- Matplotlib / Seaborn
- Jupyter Notebook
- GitHub

## Project Structure

```text
video-game-data-pipeline/
├── video_game_data_pipeline.ipynb                      # Main pipeline notebook
├── preprocessed_video_games.csv                        # Flat file source (Kaggle)
├── List of Game of the Year awards - Wikipedia.html    # Website source (scraped)
├── rawg_games.csv                                      # API source (RAWG, raw pull)
├── cleaned_videogames.csv                              # Cleaned flat file data
├── cleaned_wiki.csv                                    # Cleaned website data
├── cleaned_api.csv                                     # Cleaned API data
├── final_database.db                                   # SQLite database with merged tables
├── .gitignore
└── README.md
```

## How to Run

1. Clone this repository
2. Install dependencies: `pip install pandas numpy beautifulsoup4 matplotlib seaborn`
3. To re-run the API extraction, obtain a free RAWG API key from https://rawg.io/apidocs and store it locally (see note below)
4. Open `video_game_data_pipeline.ipynb` in Jupyter and run the cells

> **Note on the API key:** The notebook reads the RAWG API key from a local file outside the repository (`api_keys.json`), which is excluded from version control and never committed to GitHub. To reproduce the API steps, supply your own key. The cleaned data files and the SQLite database are included so the merge and visualization steps can be run without re-querying the API.

## Ethical Considerations

All data sources are publicly available and used for educational purposes. Web scraping was limited to a single publicly accessible Wikipedia page, and API usage stayed within the provider's free-tier terms. No personal or sensitive data is involved. Transformations were documented at each step to keep the data lineage transparent and reproducible.

## References

- Modiash. (2024). *Video Game Sales and Performance Data* [Data set]. Kaggle. https://www.kaggle.com/datasets/modiash/video-game-sales-and-performance-data
- RAWG. (2024). *RAWG Video Games Database API.* https://rawg.io/apidocs
- Wikipedia. (2024). *List of Game of the Year awards.* https://en.wikipedia.org/wiki/List_of_Game_of_the_Year_awards
