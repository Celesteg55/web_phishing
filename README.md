# Web Page Phishing Project

## Table of Contents
- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [Tools](#tools)
- [Data Cleaning and Preparation](#data-cleaning-and-preparation)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Data Analysis](#data-analysis)
- [Results and Findings](#results-and-findings)
- [Recommendations](#recommendations)
- [Limitations](#limitations)
- [References](#references)

### Project Overview

In this project, I will determine which components of a URL are most strongly associated with phishing activity by analyzing the relationship between URL structure (special characters, length, redirections, etc.) and the phishing label.

### Data Sources

-web_page_fishing: contains high-level URL metrics and phishing label
-phishing_dataset: contains counts of special characters and other URL components

### Tools

SSQL (for data retrieval and joining tables)
Correlation analysis (to assess linear relationships)
Visualization (scatter plots)

### Data Cleaning and Preparation

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

### Results and Findings 

1. Strongest Correlation
Feature: n_slash (number of slashes in the URL)
Interpretation:
URLs with a higher number of slashes are significantly more likely to be phishing. This suggests deeper, suspicious path structures are commonly used in phishing URLs.
2. Weakest Correlations
Feature: url_google_index
Correlation: -0.009
Feature: domain_google_index
Correlation: 0.0008
Interpretation:
These fields show almost no relationship to phishing activity. Whether or not a URL or domain is indexed by Google has minimal predictive value in identifying phishing.
3. URL Length Analysis
Feature: url_length
Observation: Scatter plot shows no clear pattern
Correlation: Very weak or negligible
Conclusion:
URL length is not a strong indicator of phishing. While long URLs can look suspicious, many legitimate services also generate long URLs.
Correlation Coefficient: 0.699
This analysis highlights that certain structural URL features, especially slashes and hyphens, are strong indicators of phishing. Other common assumptions, like URL length or Google indexing, have minimal value.
By focusing on high-signal indicators and combining them in a multi-feature system, organizations can more accurately flag suspicious URLs and protect users from phishing attacks.

### Recommendations

Focus on strong indicators, ‘qty_slash_url’ field showed the highest correlation with phishing, which suggests that URL’s with higher number of slashes are more likely to be phishing. 
I would also advise to monitoring key special characters, other fields with moderate correlations include, 
- Number of Dots (qty_dot_url): This has a positive correlation of 0.171128, indicating some level of association with phishing.
- Number of Hyphens (qty_hyphen_url): This shows a correlation of 0.200382, also suggesting some relevance.
Combine Features: Use a combination of features and possibly machine learning models to improve detection accuracy.
Update Regularly: Keep your detection methods current and validate them with new data to maintain effectiveness.

By integrating these practices, you can develop a more robust and reliable system for identifying phishing URLs

### Limitations 

The analysis identifies statistical relationships but cannot confirm cause-and-effect. For example, URLs with more slashes may correlate with phishing, but that doesn’t mean slashes cause phishing behavior.

### References 

Vrbančič, Grega (2020), “Phishing Websites Dataset”, Mendeley Data, V1, doi: 10.17632/72ptz43s9v.1

