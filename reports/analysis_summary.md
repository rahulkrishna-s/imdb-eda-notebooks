# IMDb Top 1000 Movies: Exploratory Data Analysis Report

**Author:** Rahul Krishna S  
**Date:** December 15, 2025  
**Dataset:** IMDb Top 1000 Movies (Kaggle)  
**Analysis Tool:** Python (pandas, matplotlib, seaborn)


## Summary

This report presents the exploratory data analysis of the IMDb Top 1000 movies dataset. It explores the relationships between movie ratings, box office performance, genres, certifications, directors, and temporal trends. The analysis reveals many key insights into what drives critical acclaim and commercial success of movies and challenges common assumptions about the film industry.

**Key Finding:** Box office revenue follows a power law distribution where most movies earn modest amounts while also having a few blockbusters that become big commercial successes. Volume does not equal value and the most common genres are not the most profitable.


## 1. Dataset Overview

### 1.1 Source and Scope
  **Dataset:** IMDb Top 1000 Movies from Kaggle
  **Initial Size:** 1,000 rows × 16 columns
  **Final Size (after cleaning):** 773 rows × 16 columns

### 1.2 Key Variables
  **Numerical:** IMDB_Rating, Meta_score, Runtime, Gross, No_of_Votes, Released_Year
  **Categorical:** Genre, Certificate, Director
  **Derived:** Gross_Millions, Certificate_Cleaned, Decade, Score_Difference


## 2. Data Cleaning Methodology

### 2.1 Missing Value Treatment
Released year value of one row was missing and was added using manual look up after getting the Series_Title. Rows missing the Certificate value was filled with Unrated because it wasnt too important for analysis. Metascore missing values was replaced by median. Rows missing gross was dropped because it was an important column.

### 2.2 Data Type Conversions
  Released_Year: object converted to int
  Runtime:  obj converted int also removing min
  Gross: from obj to float
