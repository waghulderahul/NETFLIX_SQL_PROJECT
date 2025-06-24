
# 📺 Netflix SQL Analytics Project

This project contains a comprehensive set of SQL queries to analyze Netflix's movie and TV show data using PostgreSQL (via pgAdmin 4). It covers everything from content breakdown, top genres, actor appearances, to keyword-based categorization.

The database is created from a structured CSV file and explored using SQL queries that demonstrate aggregation, filtering, window functions, string operations, and date handling.

---

## 🔧 Project Structure

- `netflix.sql` – Creates and loads the Netflix table
- `analysis_queries.sql` – Contains all 15 analytical SQL tasks
- `README.md` – Project overview and documentation

---

## 🗄️ Netflix Table Schema

```sql
CREATE TABLE netflix (
  show_id        VARCHAR(6),
  type           VARCHAR(10),
  title          VARCHAR(150),
  director       VARCHAR(208),
  casts          VARCHAR(1000),
  country        VARCHAR(150),
  date_added     VARCHAR(50),
  release_year   INT,
  rating         VARCHAR(10),
  duration       VARCHAR(15),
  listed_in      VARCHAR(100),
  description    VARCHAR(250)
);

📊 SQL Tasks Overview
Count Movies vs TV Shows
Count number of each type using GROUP BY.

Most Common Rating for Each Type
Use RANK() with PARTITION BY on type to find the most frequent rating.

List All Movies Released in 2020
Simple filter on type = 'Movie' and release_year = 2020.

Top 5 Countries with Most Content
Use UNNEST(STRING_TO_ARRAY(...)) to split multiple countries.

Identify the Longest Movie
Subquery to find MAX(duration) where type is 'Movie'.

Content Added in Last 5 Years
Use TO_DATE() and interval logic.

Movies or Shows by Director 'Rajiv Chilaka'
Filter using ILIKE '%Rajiv Chilaka%'.

TV Shows with More Than 5 Seasons
Check duration string for season count.

Count of Content Items in Each Genre
Use UNNEST() to split genres and count occurrences.

Top 5 Years with Highest Average Content from India
Combine EXTRACT(YEAR) and subquery to calculate percentages.

List All Documentaries
Filter listed_in ILIKE '%documentaries%'.

Find All Content Without a Director
Filter WHERE director IS NULL.

Movies Featuring Salman Khan in the Last 10 Years
Use ILIKE '%Salman Khan%' with release_year filter.

Top 10 Actors by Count (India Only)
Use UNNEST() on casts and group by name.

Label Content as 'Good' or 'Bad' Based on Description Keywords
Use CASE and ILIKE '%kill%' OR '%violence%' to label content.



