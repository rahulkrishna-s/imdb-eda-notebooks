# IMDb Top 1000 Movies: Exploratory Data Analysis Report

**Author:** Rahul Krishna S  

**Date:** December 15, 2025  

**Dataset:** IMDb Top 1000 Movies from Kaggle 

**Analysis Tool:** Python and libraries like pandas, matplotlib and seaborn


## Summary

This report presents the exploratory data analysis of the IMDb Top 1000 movies dataset that I got from Kaggle. It explores the relationships between movie ratings, box office performance, genres, certifications, directors, and temporal trends. The analysis reveals many key insights into what drives critical acclaim and commercial success of movies and challenges common assumptions about the film industry.

**Key Finding:** Box office revenue follows a power law distribution where most movies earn modest amounts while also having a few blockbusters that become big commercial successes. Volume does not equal value and the most common genres are not the most profitable.


## 1. Dataset Overview

### 1.1 Source and Scope
  **Dataset:** IMDb Top 1000 Movies from Kaggle

  **Initial Size:** 1,000 rows × 16 columns

  **Final Size (after cleaning):** 831 rows × 16 columns

### 1.2 Key Variables
  **Numerical:** IMDB_Rating, Meta_score, Runtime, Gross, No_of_Votes, Released_Year

  **Categorical:** Genre, Certificate, Director

  **Derived:** Gross_Millions, Certificate_Cleaned, Decade, Score_Difference


## 2. Data Cleaning Methodology

### 2.1 Missing Value Treatment
  Released year value of one row was missing and was added using manual look up after getting the Series_Title. 

  Rows missing the Certificate value was filled with Unrated because it wasnt too important for analysis. 

  Metascore missing values was replaced by median.

  Rows missing Gross was dropped reducing the total number of rows in the cleaned dataset from 1000 to 831. This was done because Gross was an important column and visualization of the column suggested using median as a replacement wont work.

### 2.2 Data Type Conversions
  Released_Year: object converted to int.

  Runtime:  obj converted int also removing min.

  Gross: from obj to float.

### 2.3 Feature Engineering
  **Gross_Millions:** Converted gross revenue to millions for readability

  **Certificate_Cleaned:** Mapped 15+ certificate types to 4 categories called Universal, Parental Guidance, Adult and Unrated

  **Decade:** Binned years into decades for temporal analysis

  **Score_Difference:** (IMDB_Rating × 10) - Meta_score to compare the IMDb ratings with metascore.

## 3. Key Findings
### 3.1 Revenue Distribution and Economics
  The univariate analysis and the histplot showed the revenue distribution follows a powerlaw. Most movies earned little while some outlier movies like StarWars and Avengers earned in hundreds of millions. Median earning was way below 100 million dollars.
### 3.2 Genre Analysis: Volume vs. Value
  After splitting the dataframe, it was noted that 'Drama' genre dominated the dataset in terms of volume with close to 600 movies of that type. The second and third movies of that count, 'Comedy' and 'Crime' each had count below only 200. But the ratings and gross by genre analysis showed a different story.
  Among the top 10 genres by count, 'Mystery' had the highest median rating. 'Adventure', 'Animation' and 'Action' was the genres that had highest median gross near 100 million dollars. Drama had low median gross only with many outliers. It showed 'Adventure', 'Animation' and 'Action' were more safer investments in terms of risk from a financial perspective despite the high volume of 'Drama' genre movies among the top rated movies list.
### 3.3 Rating vs. Revenue: Weak Correlation
  The correlation heatmap of the dataframe showed how interdependant each variabls were and how they affected eachother. The most interesting observation was the weak correlation between Revenue and IMDB_Rating. The correlation was very low of only 0.1. This implies just because a film have very positive reception or high ratings doesnt mean it will have high gross revenue. That is, revenue doesnt necessarily follow ratings.
  But the good correlation of Number of votes with IMDB rating and gross was noted, with the correlation being 0.5.
### 3.4 Critics vs. Audience: General Agreement with Outliers
  The reg plot of Meta_Score vs IMDB_ratings showed a line that indicated positive linear relationship. It means critics and audience tend to agree with eachother on movie ratings more often than not in this dataset. But there were also movies that both disagreed on, like the movie 'Notorious(1946)' that the critics rated a perfect 100 but only got 7.9 imdb rating and also movies like 'I am Sam(2001)' that got only 28 out of 100 from the movie critics but was loved by the general audience.
### 3.5 Certificate Analysis: Family-Friendly Profitability
  The many different Certifications in the dataset was grouped into four categories for easier analysis: Universal, Parental guidance, adult and unrated. During the analysis, it was noted that Adult certification movies dominated the dataset with 315 entries. Universal was second with 239 and Parental guidance third with 230. Despite the high volume of Adult movies, they performed poorly in terms of median gross revenue compared to universal and parental guidance movies. Parental guidance type movies with its many outliers had the highest median gross and universal was second. Universal had the highest median rating. So many adult movies get high ratings, but they are not the most consistent in terms of rating nor high in terms of median grossing in this dataset. The broader appeal of Parental guidance and Universal movies makes them better in terms of financial return in this dataset.
### 3.6 Director Quality: Nolan's Consistent Excellence
  Steven Spielberg had the most movies in this dataset with 13 entries. Christopher Nolan had 8 movies that appeared in this top imdb rated movies list, but he had the highest median rating for his movies, showing how excellent of a director he is.
### 3.7 Temporal Trends: The Rating Decline Paradox
  The decade wise analysis showed how most movies in the list was from 2000s and 2010s, with number of movies making into the list increasing with time. But paradoxically, average ratings was better for older decade movies with it noticably dropping with time.
## 7. Conclusion
  Working through this analysis revealed how complex movie success really is. It showed how film making and cinemas have evolved through time. Quality doesn't guarantee profits, volume doesn't mean value, and what audiences love isn't always what critics appreciate. Despite cinema evolving dramatically, great storytelling remains timeless.