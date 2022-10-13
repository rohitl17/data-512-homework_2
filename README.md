# data-512-homework_2

This repository has assignment for DATA-512 - Human Centered Design Homework 2.


# Goal: 

### Considering Bias in Data

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

1. Countries are mapped to the regions that are closest/lowest in the hierarchy of regions
2. The politician entries have duplicates, these have eliminated to keep the data consistent. 
3. To avoid divide-by-zero errors, we have removed the countries with 0 population. This is probably a shortcoming of having input population data in millions and not choosing the right data type/precision for the data from the source. 

## Research Implications
 
To start with what I learnt in this assignment is it is always better to backup data with domain knowledge before working on a data science project. Majority of the data on the internet have some inherent bias. The biases can exist due to multiple reasons: demographic, gender or in general cultural biases for countries where the advent of internet hasn't been that much, especially places where the literacy rates might be low. Additionally, carrying on the documentation and reproducibility lessons from the last assignment. One thing I suspected at the start of the analysis was if articles_per_capita is a good measure to analyze the coverage and if that correlates with ORES scores. Seems like the former has very low values and the values are highly dependent on the country/region's population. For example, majority of the top coverage countries/regions are the ones with lowest population and vice-versa for the bottom. Also, when it came to article quality the non-native English speaking population had lesser high quality articles over the native speakers, which is a cultural-linguistic bias. One of the surprising aspects about the API were that the same politician's names occurred under different countries and could cause redundancy issues if we go further deeper into the analysis.

What biases did you expect to find in the data (before you started working with it), and why?

##### Expected biases: Smaller countries would have less number of articles but higher number of articles_per_capita. The ratings of politicians from these countries would have been lessser since many of the politicians wouldnt be famous. Also, some of the recent articles by Wikipedia founder said that there were multiple occurrences of idealogical biases. So, I believe ORES scores would be related to a country or might have an inherent idealogical bias. The asian and african countries articles would have less number of articles per capita attributing to literacy rates or the population in general there.

What (potential) sources of bias did you discover in the course of your data processing and analysis?
What might your results suggest about (English) Wikipedia as a data source?

##### Issues: Data is dynamically changing on multiple runs hence could lead to inconsistency in analysis. The ORES scores probably might not be trustworthy as they come from an AI model which could be a victim of idealogical, racial, gender or cultural bias.

What might your results suggest about the internet and global society in general?
Can you think of a realistic data science research situation where using these data (to train a model, perform a hypothesis-driven research, or make business decisions) might create biased or misleading results, due to the inherent gaps and limitations of the data?
#### Yes, the content moderation or NLP-based tools which scrape data from the internet, might have inherent biases. For example, we saw in the readings that how cultural-linguistic, demographic or gender biases lead to potential incorrect predictions from the models. Or the Islamaphobia article suggests how GPT-3 was against the particular religion. These limitations are due to data.

Can you think of a realistic data science research situation where using these data (to train a model, perform a hypothesis-driven research, or make business decisions) might still be appropriate and useful, despite its inherent limitations and biases?
How might a researcher supplement or transform this dataset to potentially correct for the limitations/biases you observed?
#### If the data is fed into the ML model, I would think of normalizing it as to make the data more representative of the fact that each country has almost the same number of politicians. 

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
## Input Data 
- population data (population_by_country_2022.csv) - The schema consists of countries, region and population for each country/region
- Politicians data (politicians_by_country.SEPT.2022.csv) - Consists of crawled Wikipedia article pages about politicians different countries

## Output Data 
### Country data and Politician data missing mapping
wp_countries-no_match.txt - All countries for which population dataset does not have an entry for the equivalent Wikipedia country, or vice-versa

### Consolidated Data
wp_politicians_by_country.csv - Refined data output with politicians mapped to countries and region, basically the data table used for analysis.
