# Glassdoor-Salary-Analysis
Repo for the Data Science project that predicts Data Science salaries using Glassdoor data

- Created a tool that estimates mainly Salaries using Glassdoor.com data based on keyword search using python and selenium. The tools is mainly designed for Data Science related jobs.
- For scraping the website, the code from [this](https://towardsdatascience.com/selenium-tutorial-scraping-glassdoor-com-in-10-minutes-3d0915c6d905) article was used as a base. However, the code was outdated and presented a lot of bugs so I fixed extensively
- The scraper collects by default 180 job listings from Glassdoor. After that limit, Glassdoor keeps repeating the same jobs listings.
- Extracted keywords from the job description in order to quantify the value that each skill adds to the salary.
- Optimized Linear, Lasso and Random Forest Regressors using GridsearchCV to reach the best model
