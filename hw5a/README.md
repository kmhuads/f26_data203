# HW5A: ChocoDB Feature Analysis Repository 

This repository contains assigmnet files for HW5A analyzing the Flavors of Cacao dataset using Pandas. The primary tasks are an extension of HW3 to transform raw CSVs into structured binary feature matrices suitable for machine learning or clustering tasks, helping you master exploratory data analysis techniques.

## Key Tasks

*   **Data Cleaning**: Load quoted `chocodb.csv` and remove irrelevant columns (Review Date, Ingredients), normalize text (lowercase + strip spaces), and parse percentage strings to floats.
*   **Descriptive Analytics**: Compute summary stats using efficient groupby operations—most frequent review dates, mean cocoa %, Madagascar counts, median ratings by Central American region, etc.
*   **Feature Engineering**: Convert the messy "Most Memorable Characteristics" column into ~1095 binary columns.
*   **Sparse Selection & Export**: Filter out unnecessary zero-columns, retain only features appearing more than 11 times across the dataset, and save a clean feature matrix.
