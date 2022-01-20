
# Predicting Income:
## A Study of US Census Data (1994-95)

By: Terri John


<a name="top"></a>This ReadMe contains:

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
|1_cleaning_eda|Cleans and prepares data for modeling. Exploratory Data Analysis.|
|2_modeling|Binary classification model predicting income greater or lesser than $50k.|

## <a name="problemstatement"></a>Problem Statement and Background

Every 10 years, the US Census Bureau conducts a survey to count every resident of the United States, collecting a variety of demographic data from individuals. The results of this census can be used to help the US government make data driven decisions regarding the disbursement of funding. By having a better understanding of the demographic characteristics of subpopulations, we can better understand the strengths and weaknesses within our society and address them accordingly. For this study, I’m looking specifically at the characteristics of individuals who earn an income of greater or lesser than $50,000 annually.



## <a name="planning"></a>Project Planning and Methodology

For this study I began by examining the data and preparing for binary classification modeling. At first glance it appeared to be a very complete data set. Closer analysis revealed that many columns were missing 50% or more of values. This is because the US census will fill a blank with ‘Not in universe’ if a question is not asked. For example, I ended up opting not to use state of residence because about 50% of these fields were listed as ‘Not in universe.' With such a significant number of fields missing, I was unable to reliably impute missing values and opted to remove these features from the dataset for modeling.

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

Save the data files under the folder: data --> raw_data

##### Please note that the data dictionary is available in the census_income_metadata.txt file.

[Return to the top of the page](#top)
### Project Requirements:   

* scikit-learn==1.0.1
* matplotlib==3.5.0
* numpy==1.21.2
* pandas==1.3.4
* seaborn==0.11.2


## <a name="model"></a>Modeling and Analysis
I created several binary classification models in my process to understand the characteristics that are most decisive regarding whether a person earns more or less than $50,000 annually. While most models did not outperform the null model, I focused on building highly interpretable models. My goal in this project wasn't to build a perfect model - it was to better understand what is happening in our society.

 The model that I felt gave me the strongest understanding of what was happening under the hood was a LogisticRegression model. However, the strongest performing model was a RandomForest model, which gave me a well fit model hovering around 99% accuracy for both training and testing data, and an f1 score of .9.

*The baseline model assumes a 93% accuracy score, based on the majority class.

|Model|Train Accuracy|Test Accuracy|Recall|F1 Score|
|---|---|---|---|---|
|LogisticRegression|94.5%|94.5%|0.24|0.35|
|RandomForest|99.2%|98.9%|0.86|0.90|


Developing effective models was made more challenging by the highly unbalanced classes and the significant amount of missing data for some variables.

Because of the goal of my project, I had to spend some time considering which metric I wanted to prioritize - accuracy, precision, recall, or f1 score. I decided that a balance was key, but with a focus on minimizing false positives. Because I think it is more important to understand reasons for earning under $50k, I want to make sure that I'm not classifying under-earners as over-earners.

[Return to the top of the page](#top)

## <a name="conclusion"></a>Conclusion:
### Limitations

* Significant amount of data missing.


### Recommendations for next steps:
* Bring in more data. For example, bring in data related to country of origin for parents and self country of origin, as well as year of arrival in the United States. We need to build a better understanding of the economic journey taken by new immigrants to the United States.

* Cross compare features.

* Bring in more data to fill 'not in universe' designations.

### Conclusion

Features that were strongest predictors of income included age, veterans benefits, stock dividends, sex, and race and citizenship. I will note that I was heavily focused on societal demographics versus occupation, and that comes out in my results. I do think that further study should be given to a cross examination of demographics with occupation and industry codes, and that would certainly be my next step in this study.

Importantly, this data highlights that strong indicators for income include characteristics that we cannot control for, including race, citizenship, sex, and marital status, among others. The government should take this into consideration and focus on allocating funding in a way that can even out such disparities.

### <a name="sources"></a>Sources

Data for this project was provided by Dataiku.
Original data is from the US Census Bureau: http://www.census.gov/ftp/pub/DES/www/welcome.html

* https://www.forbes.com/sites/marisadellatto/2021/10/05/single-adults-make-less-money-than-partnered-ones-study-says/?sh=360d12ad454f

[Return to the top of the page](#top)
