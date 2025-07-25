# Web Page Phishing Project

### Project Overview
In this project, I will determine which components of a URL are most strongly associated with phishing activity by analyzing the relationship between URL structure (special characters, length, redirections, etc.) and the phishing label.

### Data Sources
Vrbančič, Grega (2020), “Phishing Websites Dataset”, Mendeley Data, V1, doi: 10.17632/72ptz43s9v.1
web_page_fishing: contains high-level URL metrics and phishing label
phishing_dataset: contains counts of special characters and other URL components

### Tools

SSQL (for data retrieval and joining tables)
Correlation analysis (to assess linear relationships)
Visualization (scatter plots)

### Data Cleaning/Preparation

In the initial data preparation phase we performed the following 
Data cleaning and formatting

### Exploratory Data Analysis 

What SQL code would you write to query all of the data contained in the provided dataset?
Which field(s) has/have the strongest correlation with the “phishing” field?  Which field(s) has/have the weakest correlation with the “phishing” field?
Would you say that the URL length is a strong indicator of whether or not the URL is phishing?  Why or why not?  What metrics do you have to support your answer?
Would you say the number of redirections is a strong indicator of whether or not the URL is phishing?  Why or why not?  What metrics do you have to support your answer?
Based on your analysis, what advice would you give to others for deciphering whether or not a URL is phishing?

### Data Analysis

```sql
SELECT
    w.unique_id,
    w.url_length,
    w.n_redirection,
    w.phishing,
    p.n_dots,
    p.n_hyphens,
    p.n_underline,
    p.n_slash,
    p.n_questionmark,
    p.n_equal,
    p.n_at,
    p.n_and,
    p.n_exclamation,
    p.n_space,
    p.n_tilde,
    p.n_comma,
    p.n_plus,
    p.n_asterisk,
    p.n_hashtag,
    p.n_dollar,
    p.n_percent
FROM
    web_page_fishing w
JOIN
    phishing_dataset p
ON
    w.unique_id = p.unique_id;
```

### Results/Findings 
This analysis highlights that certain structural URL features, especially slashes and hyphens, are strong indicators of phishing. Other common assumptions, like URL length or Google indexing, have minimal value.
By focusing on high-signal indicators and combining them in a multi-feature system, organizations can more accurately flag suspicious URLs and protect users from phishing attacks.




