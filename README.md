# Web Page Phishing Project

### Project Overview
In this project, I will analyze web page URL phishing data to determine which fields in a URL suggest that the URL may be phishing.

### Data Sources
Vrbančič, Grega (2020), “Phishing Websites Dataset”, Mendeley Data, V1, doi: 10.17632/72ptz43s9v.1

### Tools

SQL SERVER - Data Analysis 
Python - Creating Reports 

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

