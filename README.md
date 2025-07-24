# Web Page Phishing Project

### Project Overview
In this project, I will analyze web page URL phishing data to determine which fields in a URL suggest that the URL may be phishing.

### Data Sources
Vrbančič, Grega (2020), “Phishing Websites Dataset”, Mendeley Data, V1, doi: 10.17632/72ptz43s9v.1

### Tools

SQL SERVER - Data Analysis 
Python - Creating Reports 

### SQL Practice

Pretend there is an additional field in this dataset that assigns each row a unique number, or key.  This additional field is called unique_id and it is the first field in the dataset.  Pretend this data was stored in two different tables in a SQL server.  The first table is named web_page_fishing and it contains the following fields:

unique_id
url_length
n_redirection
phishing

### The second table is named phishing_dataset and it contains the following fields:
unique_id
n_dots
n_hyphens
n_underline
n_slash
n_questionmark
n_equal
n_at
n_and
n_exclamation
n_space
n_tilde
n_comma
n_plus
n_asterisk
n_hashtag
n_dollar
n_percent

