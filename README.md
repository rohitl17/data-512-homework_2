# data-512-homework_1: Professionalism & Reproducibility
This repository has assignment for DATA-512 - Human Centered Design Homework 1.

## Goal

The project aims at acquiring, constructing, analyzing and publishing a dataset and analysis from a subset of wikipedia pages. The goal is to follow best practices in scientific research not only from the coding but also the documentation stanspoint which entails reproducing workflows referring to the articles "Assessing Reproducibility" and "The Basic Reproducible Workflow Template" from The Practice of Reproducible Research.

## Datasource Information

The data for this project is extracted from the Pageviews API. The Pageviews API (documentation, endpoint) provides access to desktop, mobile web, and mobile app traffic data from July 2015 through the previous complete month. Leveraging the API, I collected the pageviews information using a subset of Wikipedia article pages. Please find below the subset of the English Wikipedia that represents a large number of dinosaur related articles.

#### Dataset Source and License
 - [Dinosaur articles](https://docs.google.com/spreadsheets/d/1zfBNKsuWOFVFTOGK8qnTr2DmHkYK4mAACBKk1sHLt_k/edit?usp=sharing)
 - Creative Commons Attribution-ShareAlike License 3.0[https://en.wikipedia.org/wiki/Wikipedia:Copyrights#:~:text=Creative%20Commons%20Attribution%2DShareAlike%20License%203.0]  

#### Relevant APIs
 - [Pageviews API Endpoint](https://wikimedia.org/api/rest_v1/#!/Pageviews_data/get_metrics_pageviews_aggregate_project_access_agent_granularity_start_end)
 - [Pageviews API Documentation](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Pageviews)

#### API Terms
 - [Wikimedia Foundation REST API terms of use](https://www.mediawiki.org/wiki/REST_API#Terms_and_conditions)


## Issues and Special Considerations

The code has been accustomed to handle any exceptions occurring with regards to data manipulation operations. Also, if the URL or article titles do not exist, the code wouldn't break and is entirely reproducible. As of now, everything just works fine and we have all the relevant information

## Repository Structure
Here are the main folders in our github data-512-homework_1 repository:
```bash

├── DATA512-Homework_1_RohitLokwani.ipynb
├── README.md
├── LICENSE
├── input_data
│   ├── dinosaur_genera.cleaned.SEPT.2022 - dinosaur_genera.cleaned.SEPT.2022.csv.csv
├── intermediate_outputs
│   ├── dinosaurs_data.csv
├── json_outputs
│   ├── dino_monthly_cumulative_201507-202209.json
│   ├── dino_monthly_desktop_201507-202209.json
│   └── dino_monthly_mobile_201507-202209.json
├── plotted_graphs
│   ├── top_max_min_average_views.png
│   ├── top_ten_peak_page_views.png
│   └── articles_with_fewest_data_monthly.png
```
## JSON Outputs

The following files are a part of data acquisition output as it is a time-consuming process and we can rerun the rest of the steps using these files.

dino_monthly_desktop_201507-202209.json - JSON file that contains all articles pages view data for desktop access type
dino_monthly_mobile_201507-202209.json - JSON file that contains all articles pages view data for mobile access type
dino_monthly_cumulative_201507-202209.json - JSON file that contains the cumulative page views of all articles for both desktop and mobile access type


### Data Fields
project - Source of data.   
article - Title of the article.  
granularity - Time period for Cumulative data.  
timestamp - Time checkpoint for data.   
agent - type of views.  
views - Views between two timestamps as per the specified granularity.  
Note: Access types are mentioned on the filenames. 

#### Sample
{
        "project": "en.wikipedia",
        "article": "Coelosaurus_antiquus",
        "granularity": "monthly",
        "timestamp": 2015070100,
        "agent": "user",
        "views": 79
    }  
    
### Languages used: Python

## Other References
Rokem, Marwick, and Staneva. [Assessing Reproducibility](http://www.practicereproducibleresearch.org/core-chapters/2-assessment.html) in Kitzes, J., Turek, D., & Deniz, F. (Eds.). (2018). The Practice of Reproducible Research: Case Studies and Lessons from the Data-Intensive Sciences. Oakland, CA: University of California Press. 

Kitzes. [The Basic Reproducible Workflow Template](http://www.practicereproducibleresearch.org/core-chapters/3-basic.html) in Kitzes, J., Turek, D., & Deniz, F. (Eds.). (2018). The Practice of Reproducible Research: Case Studies and Lessons from the Data-Intensive Sciences. Oakland, CA: University of California Press. 
