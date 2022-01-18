# Glassdoor-Salary-Analysis
Repo for a Data Science project that predicts Data Science salaries using Glassdoor data

- Created a tool that estimates mainly Salaries using Glassdoor.com data based on keyword search using python and selenium. The tools is mainly designed for Data Science related jobs.
- For scraping the website, the code from [this](https://towardsdatascience.com/selenium-tutorial-scraping-glassdoor-com-in-10-minutes-3d0915c6d905) article was used as a base. However, the code was outdated and presented a lot of bugs so I fixed extensively
- The scraper collects by default 180 job listings from Glassdoor. After that limit, Glassdoor keeps repeating the same jobs listings.
- Extracted keywords from the job description in order to quantify the value that each skill adds to the salary.
- Optimized Linear, Lasso and Random Forest Regressors using GridsearchCV to reach the best model
- This project is part of my learning process in order to improve my coding and Data Science skills and is based on a [Youtube walkthrough](https://www.youtube.com/playlist?list=PL2zq7klxX5ASFejJj80ob9ZAnBHdz5O1t)

## Code and Resources
- **Python version:** 3.9.6
- **Packages:** pandas, numpy, sklearn, matplotlib, seaborn, selenium
- **Scraper Github:** https://github.com/arapfaik/scraping-glassdoor-selenium
- **Scraper Article:** https://towardsdatascience.com/selenium-tutorial-scraping-glassdoor-com-in-10-minutes-3d0915c6d905
- **Youtube Walkthrough**: https://www.youtube.com/playlist?list=PL2zq7klxX5ASFejJj80ob9ZAnBHdz5O1t

## Web Scraping
Tweaked the web scraper github repo (above) to scrape 180 job postings from glassdoor.com.
After 180 job postings, Glassdoor would repeat the same ones.
Also, many parts of the code were deprecated and the website had changed so I had to rewrite most of it

With each job, we got the following:

- Job title
- Minimum Salary Range
- Maximum Salary Range
- Estimated Salary
- Job Description
- Rating
- Company
- Location
- Company Size
- Company Founded Date
- Type of Ownership
- Industry
- Sector
- Revenue

## Data Cleaning
After scraping the data, I needed to clean it up so that it was usable for our model. I made the following changes and created the following variables:

- Parsed numeric data out of Min, Max and Mean Salary
- Mean Salary out of Minimum and Maximum Salary
- Removed rows without salary
- Removed rows with hourly salary
- Removed rows with no Rating
- Parsed rating out of company text
- Made a new column for company state
- Transformed founded date into age of company
- Made columns for if different skills were listed in the job description:
  - Python
  - R
  - R Studio
  - Excel
  - AWS
  - Spark
- Column for simplified job title and Seniority
- Column for description length

## EDA
I looked at the distributions of the data and the value counts for the various categorical variables. Below are a few highlights from the pivot tables

## Model Building
First, I transformed the categorical variables into dummy variables. I also split the data into train and tests sets with a test size of 20%.

I tried three different models and evaluated them using Mean Absolute Error. I chose MAE because it is relatively easy to interpret and outliers aren’t particularly bad for this type of model.

I tried three different models:

- **Multiple Linear Regression** – Baseline for the model
- **Lasso Regression** – Because of the sparse data from the many categorical variables, I thought a normalized regression like lasso would be effective.
- **Random Forest** – Again, with the sparsity associated with the data, I thought that this would be a good fit.
