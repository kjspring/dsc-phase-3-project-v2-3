
# Vaccine Hesitancy Prediction

##  Overview

Moderna, Inc. is a biotechnology company based in Cambridge, Massachusetts focused on RNA therapeutics such as mRNA vaccines. Their use of RNA technology speeds up design and production as compared to traditional vaccines. Moderna’s only current commercial product is Spikevax, a vaccine for SARS-CoV-2, the causative agent of Covid-19. With the success of this Spikevax, Moderna has been developing other RNA-based vaccines for diseases such as influenza, HIV, and various cancer. Moderna currently has 44 vaccines and treatments in their production pipeline, of which 22 are in clinical trials. One of these vaccines in Phase 3 trials is a single-shot SARS-CoV-2 and influenza vaccine, called mRNA-1073, to prevent severe reactions and hospitalization to the seasonal influenza virus and COVID-19.

The RNA technology that Moderna is using to create and deliver their vaccines has shown 90+% efficacy but vaccines work only if a person is willing to take it. This repository uses machine learning to identify the most important variables that lead a person to become vaccinated or not. The model will also predict if someone will get a vaccine with 81% specificity.

## Business Problem

Moderna, Inc. is using mRNA science to createa  new generation of transformative medicines for patients. One of these therapies is a vaccine to prevent serious illness from both the seasonal flu and COVID-19. Currently, in Stage 3 trials, this vaccination will reduce the number of vaccinations a person must get to be protected from the seasonal flu and COVID-19 and also increase the effficacy as the current seasonal flu vaccine is between 40-60% effective.

### Stakeholders

For this combined vaccination to be effective, Moderna's executives and pharmecutical representatives need to understand what variables lead people to become or resist vaccination. The stakeholders of this analysis are Moderna's executives and pharmecutical representatives that liason with doctors and other health care professionals to promote Moderna's vaccines.

## Deliverables

* Presentation to stakeholders
* Jupyter Notebook
* GitHub Respository

## Respository Navigation
* [/data](/data) - CDC 2009 National Health Flu Survey
* [/img](/img) - contains image files
* [/disclaimer](/disclaimer) - contains disclaimer information required by the CDC
* [notebook.ipynb](notebook.ipynb) - Jupyter notebook


## Data
The data used for this analysis was the [2009 National Health Flu Survey (NHFS)](https://www.cdc.gov/nchs/nis/data_files_h1n1.htm) conducted by the CDC. This phone survey asked respondents whether they had received the H1N1 influenza and seasonal influenza vaccines and additional questions covering their social, economic, and demographic background, opinions on risks of illness and vaccine effectiveness, and behaviors towards mitigating transmission. This was in reaction to a novel influenza virus, H1N1 or ‘swine flu’, beggining to circulate in the United States. A vaccine for H1N1 was developed and available to the public by the end of 2009. This vaccine was separate from the traditional influenza vaccine because H1N1 emerged too late to be included in the trivalent seasonal influenza vaccine for 2009.

A partially cleaned version of the 2009 NHFS survey was obtained from [Driven Data](https://www.drivendata.org/competitions/66/flu-shot-learning/page/211/#metric). The final cleaned version used for analysis contains 33 variables and 26,707 observations.

### Suitability of Data
While this data is over 10 years old and targets only part of the potential vaccine cocktail Moderna, Inc. will include with their combined seasonal flu and COVID-19 vaccine, this dataset can be used to build a predictive model in line with Moderna’s needs. Moderna Inc. wants to have a predictive model to identify individuals that will or will not be vaccinated against influenza and COVID-19 in a combined vaccine. The last time there was a serious novel respiratory virus pandemic like COVID-19 was in 2009 during the H1N1 pandemic. This time period accurately reflects our current period of having a regular seasonal flu vaccine and a separate novel respiratory virus circulating. After 2009, H1N1 was included in the seasonal influenza vaccine and the population only had to have a single influenza vaccination.

## Modeling

Moderna's business problem is a classification problem and the solution is to be able to take in a series of variables from a patient and predict if this person is going to get a vaccination or not. The classification solution uses machine learning algorithms such as decision trees, random forests, and XGBoost was used to create predictive models and assess the most important variables from this dataset. 

### Model 1: Baseline Decision Tree
A decision tree is a machine learning algorithm is a collection of if-else statements. It was chosen for this analysis because it is powerful, solves classification problems, and is easy to interpret. The training data is partitioned into two or more groups that satisfy a condition. For example, if a responodent has health insurance or not. The variables chosen to split based on a condition is chosen using the amount of information gained in this split.

This model used the default values and the splitting criterion was Gini-index.

As shown under Evaluation, this was the worst performing model in terms of accuracy, precision, recall, and f1-score. To imporove the model's predictions the hyperparameters must be tuned to prevent overfitting.

### Model 2: Hyperparameter Tuned Decision Tree
To properly tune the hyperparemeters of this decision tree two steps were done. The first was to use a broad random search of possible hyperparemeters to identify the best. This was then fed into a systematic grid search to narrow down the best possible hyperparameters.

As shown in the Evaluation section, Model 2 performed much better than baseline model 1 but was still only in the 70% range for accuracy, precision, recall, F1, specificity, and Negative Predictive Value (NPV).

### Model 3: Baseline Random Forest
A decision tree will maximize the information gain at every branch. This may lead to overfittting. 

Random Forest is a machine learning algorithm that uses a bagging technique. This bagging technique uses various decision trees on subsets of the dataset. So instead of relying on one decision tree, the model from the Random Forest algorithm finds the prediction from each tree and it predicts the final output based on the majority vote of all the decisino trees in the forest. This leads to a reduction of overfitting.

The hyperparameters used were those found during the search in model 2.

As shown in the Evaluation section, there is an increase in all metrics except recall. Most importantly was an increase in specificity which is important for our model as it is more detrimental to predict a false positive (someone who is predicted to get a vaccine but does not) than a false negative (someone that is predicted to not get the vaccine but actually does).

### Model 4: Hyperparameter Tuned Random Forest
The hyperparameters were tuned for the Random Forest algorithm again using a randomized search due to computational complexity. While accuracy and specificity did not increase in comparison to model 3, the metric scores did increase for precision, recall, F1, and NPV.

### Model 5: Hyperparameter Tuned XGBoost
The final algorithm used is Gradient Boosting (XGBoost). In this case, the algoritm uses an ensemble of weak decision trees. It uses gradient descent to minimize the loss function of the model. Once it does, it concentrates on where the model went wrong and create new learners and continuously imporoves. XGBoost has been found to outperform Random Forests in  many instances.

The Evaluation section shows that model 5 outperformed model 4 in accuracy, precision, and specificity, but had a lower score in recall, F1, and NPV.

## Evaluation

While many metrics are shown below, the most important metric is specificity. Specificity, also known as the True Negative Value, refers to the probability that a negative prediction is actually negative. In this case it states the probability that a predicted not vaccinated person is actually not vaccinated. Moderna, Inc. wants to vaccinate people against the seasonal flu and COVID-19. If our model predicted a person as having the vaccine when in fact they will not get vaccinated, then this is very detremental to Moderna's needs. People that are accurately predicted to be not vaccinated will be given more information based on the most important variables as indicated in the model. Those that are predicted to be vaccinated would not receive this extra information and the false positive predictions would not have the extra information to become vaccinated.

### Table 1: Metric Scores for the Machine Learning Models

|            Model           	| Accuracy 	| Precision 	| Recall 	| F1-score 	| Specificity 	| NPV   	|
|:--------------------------:	|----------	|-----------	|--------	|----------	|-------------	|-------	|
| M1: Baseline Decision Tree 	| 67.9%    	| 65.6%     	| 66.5%  	| 66%      	| NA          	| NA    	|
| M2: Tuned Decision Tree    	| 76.1%    	| 72.4%     	| 71.0%  	| 71.7%    	| 77.4%       	| 76.1% 	|
| M3: Random Forest          	| 76.6%    	| 75.7%     	| 70.4%  	| 73.0%    	| 81.1%       	| 76.6% 	|
| M4: Tuned Random Forest    	| 76.6%    	| 77.0%     	| 75.7%  	| 76.3%    	| 81.0%       	| 80.0% 	|
| M5: Tuned XGBoost          	| 79.5%    	| 77.2%     	| 74.8%  	| 76.0%    	| 81.5%       	| 79.5% 	|

While model 4 and model 5 are very similar in scoring I would choose model 5 (XGBoost) as the best model. It has a higher specificity, accuracy, and precision than all of the models.

The top ten important variables as defined by Model 5: XGBoost can be categorized in the following groups:

* opinion of vaccine effectiveness
* Opinion of risk of infection
* Access to healthcare
* Age group

## Conclusion



Just like in Phase 1 and 2, the `README.md` file should be the bridge between your non technical presentation and the Jupyter Notebook. It should not contain the code used to develop your analysis, but should provide a more in-depth explanation of your methodology and analysis than what is described in your presentation slides.

