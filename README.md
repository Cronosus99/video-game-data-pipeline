# Video Game Data Pipeline (Data Engineering Project)

**Author:** Kevin Danh  
**Program:** Master of Data Science – Bellevue University  
**Course:** DSC 540: Data Preparation  

## Project Summary

This project builds an end-to-end data pipeline that integrates video game data from three different source types: a flat file, a scraped website, and a public API. Each source is cleaned and transformed independently, then merged into a single relational database and explored through visualizations. The focus of this project is data acquisition, wrangling, and integration rather than predictive modeling.

## Project Type
Data Engineering | Data Wrangling | Multi-Source Integration

## Data Sources

This project combines three distinct source types, related through video game titles:

- **Flat file (CSV):** A Kaggle video game dataset containing sales and metadata
- **Website (web scraping):** A Wikipedia page listing Game of the Year awards, parsed directly from the HTML using BeautifulSoup
- **API:** The RAWG Video Games API, queried with pagination to retrieve game metadata

## Methods

### Data Extraction
- Loaded flat file data with Pandas
- Scraped and parsed structured HTML tables from Wikipedia with BeautifulSoup
- Queried the RAWG API across multiple pages and flattened nested JSON responses

### Data Cleaning & Transformation
- Applied at least five transformation steps to each source, including:
  - Replacing and standardizing headers
  - Fixing data types and inconsistent casing
  - Removing duplicates and unnecessary columns
  - Handling missing values
  - Reformatting nested or non-tabular fields into clean columns

### Data Integration & Storage
- Loaded each cleaned dataset into a SQLite database as separate tables
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
├── video_game_data_pipeline.ipynb     # Main pipeline notebook
├── (source and cleaned data files)    # CSV / HTML data sources and outputs
├── final_database.db                  # SQLite database with merged tables
└── README.md
```

## How to Run

1. Clone this repository
2. Install dependencies: `pip install pandas numpy beautifulsoup4 matplotlib seaborn`
3. To re-run the API extraction, obtain a free RAWG API key from https://rawg.io/apidocs and store it locally (see note below)
4. Open `video_game_data_pipeline.ipynb` in Jupyter and run the cells

> **Note on the API key:** The notebook reads the RAWG API key from a local file outside the repository. The key is never stored in the notebook or committed to GitHub. To reproduce the API steps, supply your own key. The cleaned data files are included so the merge and visualization steps can be run without re-querying the API.

## Ethical Considerations

All data sources are publicly available and used for educational purposes. Web scraping was limited to a single publicly accessible Wikipedia page, and API usage stayed within the provider's free-tier terms. No personal or sensitive data is involved. Transformations were documented at each step to keep the data lineage transparent and reproducible.

## References

- RAWG. (2024). *RAWG Video Games Database API.* https://rawg.io/apidocs
- Wikipedia. (2024). *List of Game of the Year awards.* https://en.wikipedia.org/wiki/List_of_Game_of_the_Year_awards
