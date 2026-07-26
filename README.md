# Amazon Prime TV Shows and Movies - Exploratory Data Analysis

## Project Overview

This project performs an Exploratory Data Analysis (EDA) on Amazon Prime Video's content library to uncover meaningful business insights. The analysis examines ~9,800 titles (movies and TV shows) and ~124,000 credit entries to understand genre distribution, release trends, country-wise content production, ratings, popularity, and the contribution of actors and directors.

## Dataset

The dataset consists of two files:

- **titles.csv** - Detailed information about each title (~9,871 records, 15 columns):
  - `id` - Unique identifier
  - `title` - Name of the movie or TV show
  - `type` - MOVIE or SHOW
  - `description` - Brief summary
  - `release_year` - Year of release
  - `age_certification` - Content rating (PG, R, TV-MA, etc.)
  - `runtime` - Duration in minutes
  - `genres` - Genres associated with the title
  - `production_countries` - Countries of production
  - `seasons` - Number of seasons (for TV shows)
  - `imdb_id`, `imdb_score`, `imdb_votes` - IMDb identifiers and ratings
  - `tmdb_popularity`, `tmdb_score` - TMDB popularity and ratings

- **credits.csv** - Cast and crew information (~124,235 records, 5 columns):
  - `person_id` - Unique identifier for cast/crew member
  - `id` - Title identifier (links to titles dataset)
  - `name` - Name of actor/director/crew
  - `character` - Character played
  - `role` - ACTOR or DIRECTOR

## Business Objective

Analyze Amazon Prime Video's content library to identify trends in genres, production countries, release years, popularity, and ratings. Provide actionable insights to improve content acquisition, understand audience preferences, optimize regional offerings, and make data-driven business decisions.

## Analysis Performed

### Section 1: Data Loading & Inspection
- Loaded both datasets from compressed CSV files
- Examined structure, data types, and summary statistics
- Identified missing values and duplicate records

### Section 2: Understanding Variables
- Cataloged all features and their descriptions
- Analyzed unique values for each variable
- Identified 2 content types (MOVIE/SHOW), 110 unique release years, 2028 genre combinations, 497 production countries

### Section 3: Data Wrangling
- Removed 3 duplicate records from titles, 56 from credits
- Handled missing values:
  - `age_certification` - filled with "Unknown"
  - `imdb_score`, `tmdb_score`, `tmdb_popularity`, `imdb_votes` - filled with median
  - `seasons` - filled with 0 (not a TV show)
  - `description` - filled with "Description not available"
  - `character` - filled with "Unknown"
  - `imdb_id` - left unchanged (external identifier, not used in analysis)

### Section 4: Data Visualization (20 Charts)

#### Univariate Analysis
1. **Content Type Distribution** - Pie chart: 86.2% Movies vs 13.8% TV Shows
2. **Release Year Distribution** - Histogram: heavy skew toward post-2000 content
3. **IMDb Score Distribution** - Histogram: normal-like distribution centered at ~6.5
4. **Runtime Distribution** - Histogram: peaks at 20-30 min (episodes) and 90-120 min (movies)
5. **TMDB Popularity Distribution** - Histogram (log scale): highly right-skewed
6. **Top 15 Genres** - Horizontal bar: Drama leads, followed by Comedy, Thriller
7. **Top 15 Production Countries** - Horizontal bar: US dominates (5,334 titles)
8. **Age Certification Distribution** - Count plot: TV-MA and R most common
9. **Seasons Distribution for Shows** - Histogram: most shows have only 1 season

#### Bivariate Analysis
10. **Type vs IMDb Score** - Box plot: similar median scores (~6-7)
11. **Type vs Runtime** - Box plot: movies ~90-110 min, shows ~20-40 min
12. **Release Year vs Avg IMDb Score** - Line chart: older content scores higher
13. **Runtime vs IMDb Score** - Scatter plot: no strong correlation
14. **Top Genres by Avg IMDb Score** - Bar chart: War, Documentary, History score highest
15. **Type vs Age Certification** - Stacked bar: movies more R/PG-13, shows more TV-MA
16. **IMDb Votes vs IMDb Score** - Scatter plot: weak positive correlation

#### Multivariate Analysis
17. **Correlation Heatmap** - IMDb & TMDB scores strongly correlated (r~0.58)
18. **Pair Plot** - Weak correlations between most variables
19. **Genre Popularity Across Decades** - Heatmap: Drama consistent across all decades
20. **Content Production Trend by Type** - Line chart: exponential growth from 1980s

## Key Insights

1. **Content Mix**: Movies dominate (86.2%) but TV shows are growing
2. **Regional Bias**: US produces >50% of all content - opportunity for regional expansion
3. **Genre Strategy**: Drama/Comedy/Thriller are most abundant; War/Documentary/History score highest
4. **Quality Trends**: Older content rates higher (survivorship bias); recent content shows stable ~6.5 avg
5. **Rating Correlation**: IMDb and TMDB scores correlate strongly, but most other variables are weakly correlated
6. **Content Duration**: Standard formats dominate (20-30min episodes, 90-120min movies)
7. **Show Longevity**: Most shows are single-season, few long-running series

## Technologies Used

- Python 3.14+
- Pandas 3.0 - Data manipulation
- NumPy 2.5 - Numerical operations
- Matplotlib 3.11 - Visualization
- Seaborn 0.13 - Statistical visualization
- Jupyter Notebook - Interactive development

## Recommendations

1. **Increase TV Show Investment** to drive subscriber retention
2. **Expand Regional Content** production to attract international audiences
3. **Focus on High-Performing Genres** (Documentary, History, Crime) for quality perception
4. **Balance Age Certifications** with more family-friendly content
5. **Leverage Classic Content** as critically acclaimed offerings
6. **Use Multi-Factor Recommendations** rather than single-metric reliance
7. **Monitor Recent Trends** - declining recent ratings and niche genre growth

## Future Scope

- Sentiment analysis on content descriptions
- Recommendation system using merged credits and titles datasets
- Director/actor impact analysis on ratings and popularity
- Time series forecasting for content production trends

## Links

- GitHub Repository: https://github.com/abhaykumarvishwakarma/Amazon-Prime-TV-Shows-and-Movies.git
