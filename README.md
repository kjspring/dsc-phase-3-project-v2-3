
# Vaccine Hesitancy Prediction

##  Overview

Moderna, Inc. is a biotechnology company based in Cambridge, Massachusetts focused on RNA therapeutics such as mRNA vaccines. Their use of RNA technology speeds up design and production as compared to traditional vaccines. Moderna’s only current commercial product is Spikevax, a vaccine for SARS-CoV-2, the causative agent of Covid-19. With the success of this Spikevax, Moderna has been developing other RNA-based vaccines for diseases such as influenza, HIV, and various cancer. Moderna currently has 44 vaccines and treatments in their production pipeline, of which 22 are in clinical trials. One of these vaccines in Phase 3 trials is a single-shot SARS-CoV-2 and influenza vaccine, called mRNA-1073, to prevent severe reactions and hospitalization to the seasonal influenza virus and COVID-19.

The RNA technology that Moderna is using to create and deliver their vaccines has shown 90+% efficacy but vaccines work only if a person is willing to take it. This repository uses machine learning to identify the most important variables that lead a person to become vaccinated or not. The model will also predict if someone will get a vaccine with 81% specificity.

## Business and Data Understanding

Moderna, Inc. is using mRNA science to createa  new generation of transformative medicines for patients. One of these therapies is a vaccine to prevent serious illness from both the seasonal flu and COVID-19. Currently, in Stage 3 trials, this vaccination will reduce the number of vaccinations a person must get to be protected from the seasonal flu and COVID-19 and also increase the effficacy as the current seasonal flu vaccine is between 40-60% effective.

### Stakeholders

For this combined vaccination to be effective, Moderna's executives and pharmecutical representatives need to understand what variables lead people to become or resist vaccination. The stakeholders of this analysis are Moderna's executives and pharmecutical representatives that liason with doctors and other health care professionals to promote Moderna's vaccines.

### Data
The data used for this analysis was the [National 2009 H1N1 Flu Survey (NHFS)](https://www.cdc.gov/nchs/nis/data_files_h1n1.htm) conducted by the CDC. This phone survey asked respondents whether they had received the H1N1 influenza and seasonal influenza vaccines and additional questions covering their social, economic, and demographic background, opinions on risks of illness and vaccine effectiveness, and behaviors towards mitigating transmission. This was in reaction to a novel influenza virus, H1N1 or ‘swine flu’, beggining to circulate in the United States. A vaccine for H1N1 was developed and available to the public by the end of 2009. This vaccine was separate from the traditional influenza vaccine because H1N1 emerged too late to be included in the trivalent seasonal influenza vaccine for 2009.

A partially cleaned version of the 2009 NHFS survey was obtained from [Driven Data](https://www.drivendata.org/competitions/66/flu-shot-learning/page/211/#metric). The final cleaned version used for analysis contains 33 variables and 26,707 observations.

### Suitability of Data
While this data is over 10 years old and targets only part of the potential vaccine cocktail Moderna, Inc. will include with their combined seasonal flu and COVID-19 vaccine, this dataset can be used to build a predictive model in line with Moderna’s needs. Moderna Inc. wants to have a predictive model to identify individuals that will or will not be vaccinated against influenza and COVID-19 in a combined vaccine. The last time there was a serious novel respiratory virus pandemic like COVID-19 was in 2009 during the H1N1 pandemic. This time period accurately reflects our current period of having a regular seasonal flu vaccine and a separate novel respiratory virus circulating. After 2009, H1N1 was included in the seasonal influenza vaccine and the population only had to have a single influenza vaccination. 

## Modeling

Moderna's business problem is a classification problem and the solution is to be able to take in a series of variables from a patient and predict if this person is going to get a vaccination or not. The classification solution uses machine learning algorithms such as decision trees, random forests, and XGBoost was used to create predictive models and assess the most important variables from this dataset. 

## Evaluation

## Conclusion

Just like in Phase 1 and 2, the `README.md` file should be the bridge between your non technical presentation and the Jupyter Notebook. It should not contain the code used to develop your analysis, but should provide a more in-depth explanation of your methodology and analysis than what is described in your presentation slides.

