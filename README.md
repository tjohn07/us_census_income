
# Predicting Income:
## A Study of US Census Data (1994-95)

By: Terri John


This ReadMe contains:

* [Project Contents](#contents)
* [Problem Statement](#problemstatement)
* [Project Planning and Methodology](#planning)
* [A description of the data and Project Requirements](#data)
* [Modeling and Analysis](#model)
* [Conclusion](#conclusion)
* [Sources](#sources)



## <a name="contents"></a>Project Contents:

|Name|Description|
|---|---|
|1_cleaning_eda|Cleans and prepares data for modeling. Initial EDA.|
|2_modeling|Binary classification model predicting income greater or lesser than $50k.|

## <a name="problemstatement"></a>Problem Statement and Background

Every 10 years, the US Census Bureau conducts a survey to count every resident of the United States, collecting a variety of demographic data from individuals. The results of this census can be used to help the US government make data driven decisions regarding the disbursement of funding. By having a better understanding of the demographic characteristics of subpopulations, we can better understand the strengths and weaknesses within our society and address them accordingly. For this study, I’m looking specifically at the characteristics of individuals who earn an income of greater or lesser than $50,000 annually.



## <a name="planning"></a>Project Planning and Methodology

For this study I began by examining the data and preparing for modeling. At first glance it appeared to be a very complete data set. Closer analysis revealed that many columns were missing 50% or more of values. This is because the US census will fill a blank with ‘Not in universe’ if a question is not asked. For example, I ended up opting not to use state of residence because about 50% of these fields were listed as ‘Not in universe.

Moving onto feature engineering, the data contained several categorical features. For features that could be justified as ordinal in nature, such as level of education, I encoded the features. For features that could be considered to be ordinal, such as race, I used sparse matrices to create a column for each category, with each field containing either a 0 or a 1.

Once the data was ready for modeling, I built a variety of binary classification models, which I’ll discuss later in this document. Finally, I’ll provide some analysis of my findings.


## <a name="data"></a>Data:

### Get the Data:
* The data for this study was acquired from Dataiku's talent aquisition team:

You have been provided a sample dataset from the US Census archive containing detailed, but anonymized, information for ~300,000 individuals. This archive contains three files:
1. census_income_learn.csv (data for model training)
2. census_income_test.csv (data for model testing)
3. census_income_metadata.txt (metadata for both datasets).

You may download this data archive here: https://t.lever-analytics.com/email-link?dest=http%3A%2F%2Fthomasdata.s3.amazonaws.com%2Fds%2Fus_census_full.zip&eid=fa860e43-c512-44d5-a62b-404c8c1f6dcf&idx=3&token=ttkjOcDfJAbkWA9gaGnUF9H2Yto.

Save the data files under the folder: data --> raw


### Project Requirements:   

* scikit-learn==1.0.1
* matplotlib==3.5.0
* numpy==1.21.2
* pandas==1.3.4
* seaborn==0.11.2


## <a name="model"></a>Modeling and Analysis
I created several binary classification models in my process to understand the characteristics that are most decisive regarding whether a person earns more or less than $50,000 annually. While most models did not outperform the null model, I focused on building highly interpretable models. My goal in this project wasn't to build a perfect model - it was to better understand what is happening in our society.

|Model|Null Model|Train Accuracy|Test Accuracy|F1 Score|
|---|---|---|---|---|
|KNN|74%|82%|82%|72%|


Developing effective models was made more challenging by the highly unbalanced classes, alongside the general difficulties that come along with trying to predict human behavior.

Because of the goal of my project, I had to spend some time considering which metric I wanted to prioritize - accuracy, precision, recall, or f1. I decided that a balance was key, but with a focus on minimizing false positives. Because I think it is more important to understand reasons for earning under $50k, I want to make sure that I'm not classifying under-earners as over-earners.


## <a name="conclusion"></a>Conclusion:
### Limitations and


### Recommendations for next steps:





### <a name="sources"></a>Sources
