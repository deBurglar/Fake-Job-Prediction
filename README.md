## Problem Statement

This project aims to create a classifier that will have the capability to identify fake and real jobs. The final result will be evaluated based on two different models. Since the data provided has both numeric and text features one model will be used on the text data and the other on numeric data. The final output will be a combination of the two. 
The final model will take in any relevant job posting data and produce a final result determining whether the job is real or not. 

This project uses data from [Kaggle](https://www.kaggle.com/shivamb/real-or-fake-fake-jobposting-prediction).

## Metrics

The models will be evaluated based on two metrics:

1. Accuracy: 


2. F1-Score: F1 score is a measure of a model’s accuracy on a dataset. 

F1-score is used because in this scenario both false negatives and false positives are crucial. This model needs to identify both categories with the highest possible score since both have high costs associated to it. 

# Analysis

## Data Exploration

The data for this project is available at Kaggle - https://www.kaggle.com/shivamb/real-or-fake-fake-jobposting-prediction. The dataset consists of 17,880 observations and 18 features. 

The data is combination of integer, binary and textual datatypes. A brief definition of the variables is given below:

|     #     |     Variable               |     Datatype    |     Description                                                                                                                                                                                            |
|-----------|----------------------------|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     1     |     job_id                 |     int         |     Identification number given   to each job posting                                                                                                                                                      |
|     2     |     title                  |     text        |     A name that describes the   position or job                                                                                                                                                            |
|     3     |     location               |     text        |     Information about where the   job is located                                                                                                                                                           |
|     4     |     department             |     text        |     Information about the   department this job is offered by                                                                                                                                              |
|     5     |     salary_range           |     text        |     Expected salary range                                                                                                                                                                                  |
|     6     |     company_profile        |     text        |     Information about the   company                                                                                                                                                                        |
|     7     |     description            |     text        |     A brief description about   the position offered                                                                                                                                                       |
|     8     |     requirements           |     text        |     Pre-requisites to qualify   for the job                                                                                                                                                                |
|     9     |     benefits               |     text        |     Benefits provided by the   job                                                                                                                                                                         |
|     10    |     telecommuting          |     boolean     |     Is work from home or remote   work allowed                                                                                                                                                             |
|     11    |     has_company_logo       |     boolean     |     Does the job posting have a   company logo                                                                                                                                                             |
|     12    |     has_questions          |     boolean     |     Does the job posting have   any questions                                                                                                                                                              |
|     13    |     employment_type        |     text        |     5 categories – Full-time,   part-time, contract, temporary and other                                                                                                                                   |
|     14    |     required_experience    |     text        |     Can be – Internship, Entry   Level, Associate, Mid-senior level, Director, Executive or Not Applicable                                                                                                 |
|     15    |     required_education     |     text        |     Can be – Bachelor’s degree,   high school degree, unspecified, associate degree, master’s degree, certification,   some college coursework, professional, some high school coursework,   vocational    |
|     16    |     Industry               |     text        |     The industry the job   posting is relevant to                                                                                                                                                          |
|     17    |     Function               |     text        |     The umbrella term to   determining a job’s functionality                                                                                                                                               |
|     18    |     Fraudulent             |     boolean     |     The target variable  0: Real, 1: Fake                                                                                                                                                                 |

Since most of the datatypes are either Booleans or text a summary statistic is not needed here. The only integer is job_id which is not relevant for this analysis. The dataset is further explored to identify null values.

![missing values](Images/missing_values.png)

Variables such as department and salary_range have a lot of missing values. These columns are dropped from further analysis. 

After initial assessment of the dataset, it could be seen that since these job postings have been extracted from several countries the postings were in different languages. To simplify the process this project uses data from US based locations that account for nearly 60% of the dataset. This was done to ensure all the data is in English for easy interpretability. 
Also, the location is split into state and city for further analysis. The final dataset has 10593 observations and 20 features.

The dataset is highly unbalanced with 9868 (93% of the jobs) being real and only 725 or 7% of the jobs being fraudulent. A countplot of the same can show the disparity very clearly. 


## Exploratory Analysis

The first step to visualize the dataset in this project is to create a correlation matrix to study the relationship between the numeric data.


