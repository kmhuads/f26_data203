# Homework 4 (HW4)

 This homework requires applying Python's Pandas library to perform end-to-end data engineering on U.S. Census tract-level Social Vulnerability Index (SVI) data from four states—California, Texas, Vermont, and Wyoming—and explore patterns through descriptive statistics and visualization.


## Data Sources:

 The project utilizes raw CSV files from [CDC/ATSDR SVI data](https://atsdr.cdc.gov/place-health/php/svi/index.html)  (limited to four states whose data live in `data/CALIFORNIA.csv`, `data/TEXAS.csv`, `data/VERMONT.csv`, `data/WYOMING.csv`) containing socioeconomic indicators such as population counts (`E_TOTPOP`), land area (`AREA_SQMI`), housing characteristics, and racial demographics to assess community vulnerability. 
 
 ## Objectives to Master:
  
Learn to structure data by merging multiple files into a single DataFrame, clean datasets by removing invalid rows, enrich the dataset by calculating new derived columns like population density (`POP_PER_SQMI`) and classifying tracts as urban/rural via functions, subset variables of interest before exporting, and finally analyze the enriched data to generate summary statistics (medians) and state-specific scatter plots correlating racial themes with minority proportions.