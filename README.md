
#                              Diabetes probability based on behavioral, medical, demographic, and economic factors 
##                                           Team 29- MGT 6203 Group Project Final Report


## Table of Contents
- [Description](#Description)
- [Installing](#installing)
- [Usage](#Usage)
- [Directory Structure](#directory-structure)
- [Contributing](#contributing)

### Description
Nearly 10% of Americans have type II diabetes (CDC), costing each nearly 10 years of their life, and the U.S. over $325 billion dollars, annually. The American Diabetes Association (ADA) states that “Care for people with diagnosed diabetes accounts for one in four health care dollars in the U.S.” We seek to identify behavioral and societal diabetes risk factors to improve health care programs, lower the U.S.’s healthcare burden, improve the private sector’s productivity, and improve U.S. citizens’ wellbeing.

## Installing
We are using R version 4.2.2 in this project. 
To run this project, please install and run the libary of the following packages: foreign, DataExplorer, glmnet , Hmisc, pastecs
, ggplot2, car, class, grid, tidyr, tidyverse, gridExtra, corrplot, caret, performance, "readxl", RColorBrewer, dplyr, ROCR, e1071 , rpart, kknn, imbalance, caTools,rpart.plot


## Usage
A step by step series that tell you how to get the code running:

**1. Data**

* [CDC - 2021 BRFSS Survey Data](https://www.dropbox.com/s/t4e5cypfbe63jxf/LLCP2021.XPT%20.zip?dl=0)
* [Cost of Living Dataset](https://www.dropbox.com/scl/fi/3sm9u74ijs60o1b94v2sl/Cost_of_living.xlsx?dl=0&rlkey=nim2iy5x30qwyjiuqfow4l9fe )
* [Population](https://www.dropbox.com/s/3ux4nyuqj4tuj3o/Population.csv?dl=0 )

After cleaning, the BRFSS dataset has 22 columns and 134702 rows. The final variables include state, race, gender, general health, physical activity, employment, children at home, alcohol consumption, health insurance, BMI, age, blood pressure, education, income, among others. 12.8% of respondents in our cleaned dataset have diabetes. We also added the state code in the cost-of-living dataset and merged it with our cleaned BRFSS data and the US Population data to form our final dataset.

**2. Code in R**

* [Code to implement machine learning models and data visualization](https://github.gatech.edu/MGT-6203-Spring-2023-Canvas/Team-29/tree/main/Final%20Code)

In this project, we will compare different machine learning models across the dataset including Logistic Regression, KNN, Naïve Bayes and Tree Classifications. We are also checking their confusion matrices and AUC scores. 

Data Visualization charts could be found [HERE](https://github.gatech.edu/MGT-6203-Spring-2023-Canvas/Team-29/tree/main/Visualizations).

Overall, KNN and Logistic regression have the smallest False Negatives and higher Recall compared to the Decision Tree and Naive Bayes. Therefore, we chose KNN as the best model. With Logistic regression we also found out that General Health, Age, BMI, Blood Pressure, BMI, Pneumonia, Routine Checkup, Race, Alcohol and Income have more importance to predict diabetes compared to the other variables.  

## Directory Structure
The folder's naming is straightforward. Below, we aggregate the folders by subject to make it easier to link them to their function:

**1. Final Deliverables**

Material produced for _Phase 4: Final Project Submission_.

* [Final Report](https://github.gatech.edu/MGT-6203-Spring-2023-Canvas/Team-29/tree/main/Final%20Report)
* [Final Presentation Slides](https://github.gatech.edu/MGT-6203-Spring-2023-Canvas/Team-29/tree/main/Final%20Presentation%20Slides)
* [Final Code](https://github.gatech.edu/MGT-6203-Spring-2023-Canvas/Team-29/tree/main/Final%20Code)
* [Visualizations](https://github.gatech.edu/MGT-6203-Spring-2023-Canvas/Team-29/tree/main/Visualizations)

**2. Previous Deliverables**

Material produced for _Phase 2: Project Proposal and Proposal Video Presentation_ and _Phase 3: Progress Report_.

* [Progress Report](https://github.gatech.edu/MGT-6203-Spring-2023-Canvas/Team-29/tree/main/Progress%20Report)
* [Proposal Presentation](https://github.gatech.edu/MGT-6203-Spring-2023-Canvas/Team-29/tree/main/Proposal%20Presentation)
* [Project Proposal](https://github.gatech.edu/MGT-6203-Spring-2023-Canvas/Team-29/tree/main/Project%20Proposal)

**3. Support Material**

Exploratory codes and files used during the project development.

* [Code](https://github.gatech.edu/MGT-6203-Spring-2023-Canvas/Team-29/tree/main/Code)
* [Data](https://github.gatech.edu/MGT-6203-Spring-2023-Canvas/Team-29/tree/main/Data)
* [.idea](https://github.gatech.edu/MGT-6203-Spring-2023-Canvas/Team-29/tree/main/.idea)
* [Other Resouces](https://github.gatech.edu/MGT-6203-Spring-2023-Canvas/Team-29/tree/main/Other%20Resources)

## Contributing
Olivia Watson, Selda Kocaman, Kelly Cristina Ribeiro Yogui, Thu Thi Diem Le, Hande Pehlivan

