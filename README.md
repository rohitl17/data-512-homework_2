# data-512-homework_2

This repository has assignment for DATA-512 - Human Centered Design Homework 2.


# Goal: Considering Bias in Data

The project aims at acquiring, constructing, analyzing and publishing a dataset and analysis for a set of politician wiki pages. It emphasizes one main aspect/shortcomings of large datasets - bias. The biases in data can lead to bias in models and inferences drawn from them leading to fairness concerns. This analysis highlights how bias affects article quality predictions and such biases can be commonly seen in other data science projects

## Datasource Information


The input data for this project is extracted from the politician wiki pages and prb (population) web pages. We further use PageViews Info API and ORES API. ORES is a machine learning tool that can provide estimates of Wikipedia article quality. The categories for ORES scores are:

FA - Featured article

GA - Good article

B - B-class article

C - C-class article

Start - Start-class article

Stub - Stub-class article

## Dataset source
 - [Politicians by Nationality](https://en.wikipedia.org/wiki/Category:Politicians_by_nationality)
 - [World Population](https://www.prb.org/international/indicator/population/table/)
 
## Relevant APIs
 - [ORES REST API](https://www.mediawiki.org/wiki/ORES)
 - [Wikimedia Foundation REST API terms of use](https://www.mediawiki.org/wiki/REST_API#Terms_and_conditions)

## Data Source License
- [CC-BY-SA 3.0]( CC-BY-SA 3.0 and GFDL licenses)
- [GFDL licenses](CC-BY-SA 3.0 and GFDL licenses)


## Issues and Special Considerations

1. There are few duplicates in the politicians input data file. All the absolute duplicates are filtered from the data but the duplicates at article name level are taken into account for per-capita calculations. 
2. There are few countries where the population is 0. This can be because the value is in millions and is rounded to the nearest decimal. These countries are filtered at Step 4 where the article-per-capita is calculated as they give infinity values because of 0 in the denominator
3. Regions with cumulative population values are eliminated and the countries are mapped to the regions that are closest/lowest in the hierarchy of regions

## Research Implications

Include write-up paragraphs. One of your paragraphs should reflect on what you have learned, what you found, what (if anything) surprised you about your findings, and/or what theories you have about why any biases might exist (if you find they exist).

What biases did you expect to find in the data (before you started working with it), and why?
What (potential) sources of bias did you discover in the course of your data processing and analysis?
What might your results suggest about (English) Wikipedia as a data source?
What might your results suggest about the internet and global society in general?
Can you think of a realistic data science research situation where using these data (to train a model, perform a hypothesis-driven research, or make business decisions) might create biased or misleading results, due to the inherent gaps and limitations of the data?
Can you think of a realistic data science research situation where using these data (to train a model, perform a hypothesis-driven research, or make business decisions) might still be appropriate and useful, despite its inherent limitations and biases?
How might a researcher supplement or transform this dataset to potentially correct for the limitations/biases you observed?

## Repository Structure
Here are the main folders in our github data-512-homework_2 repository:
```bash
├── DATA512-Homework_2_RohitLokwani.ipynb
├── README.md
├── LICENSE
├── input_data
│   ├── politicians_by_country_SEPT.2022.csv - politicians_international_SEPT.2022.csv.csv
│   ├── population_by_country_2022.csv - population_by_country_2022.csv.csv
├── intermediate_outputs
│   ├── Articles_lastrevisionids.csv
│   ├── ores_scores.csv
├── outputs
│   ├── wp_countries-no_match.txt
│   ├── wp_politicians_by_country.csv
```
## Input Data Files
- population data (population_by_country_2022.csv) - Consists of countries, region and population for each country/region
- Politicians data (politicians_by_country.SEPT.2022.csv) - Consists of crawled Wikipedia article pages about politicians fropm wide range of countries

## Output Data Files

### Countries with No Match
wp_countries-no_match.txt - All countries for which there are no matches i.e., either the population dataset does not have an entry for the equivalent Wikipedia country, or vice-versa

### Consolidated Data
wp_politicians_by_country.csv - Consolidated the remaining data that contains politicians data with population data into a single CSV file
