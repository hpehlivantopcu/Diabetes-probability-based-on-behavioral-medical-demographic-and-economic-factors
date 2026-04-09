# Predicting Diabetes Risk from Behavioral and Medical Factors

## CDC BRFSS Analysis (n=134,702)

This repository contains a data science analysis identifying the demographic, behavioral, and medical factors most strongly associated with type II diabetes risk using federal surveillance data. The analysis combines behavioral health survey data with economic and demographic context to inform public health messaging and health equity research.

---

## Research Question & Public Health Significance

**Why does this matter?** Type II diabetes is a leading cause of preventable mortality and morbidity in the United States, with prevalence rising across demographic groups. The CDC estimates that one in four healthcare dollars in the U.S. is spent on diabetes care, yet we lack clear, evidence-based understanding of which behavioral modifications and demographic risk factors are most predictive of diabetes status in real-world populations. This analysis addresses that gap by using large-scale federal surveillance data to identify the strongest independent predictors of diabetes at the population level—work that directly informs public health campaigns, resource allocation, and equity-focused interventions. Understanding these relationships from representative survey data is essential for translating research findings into actionable guidance.

---

## Dataset Description

**Source:** CDC Behavioral Risk Factor Surveillance System (BRFSS) 2021  
**Sample Size:** 134,702 respondents (after quality filtering)  
**Diabetes Prevalence:** 12.8% of cleaned sample

**Key Variables Analyzed:**
- **Health Status:** General health rating, blood pressure, routine checkups, pneumonia vaccination
- **Behavioral:** Physical activity, alcohol consumption
- **Demographics:** Age (categorical bands), race/ethnicity, gender, employment status, children in household
- **Socioeconomic:** Education level, annual household income, health insurance status
- **Geographic Context:** State of residence, state-level cost of living index

All variables were derived from the BRFSS questionnaire (XPT format) and cross-referenced with public Census population data and cost-of-living indices to enable contextual analysis.

---

## Methodology

### Data Cleaning & Feature Selection
- **Initial filtering:** Retained only variables with ≥85% data completeness
- **Target variable:** Binary classification (diabetes vs. no diabetes) derived from BRFSS DIABETE4 field
- **Missing data handling:** Removed rows with remaining missingness (complete case analysis)
- **Final dataset:** 22 features, 134,702 complete observations
- **Feature selection:** Applied LASSO regularization (α=1, cross-validated lambda) to eliminate multicollinearity and rank variable importance

### Model Comparison & Performance
Evaluated four classification algorithms on held-out test set:
1. **Logistic Regression** – Interpretable baseline with probability estimates
2. **K-Nearest Neighbors (K=317)** – Nonparametric density-based approach
3. **Decision Tree (pruned)** – Rule-based model for feature interactions
4. **Naïve Bayes** – Baseline generative model

**Performance Metrics:** Accuracy, sensitivity, specificity, precision, and ROC-AUC scores computed for each model. Logistic regression and KNN showed lowest false negative rates and highest recall, making them most useful for identifying at-risk individuals.

---

## Key Findings

**Strongest Independent Predictors** (ranked by logistic regression coefficient magnitude):

1. **BMI Category** (coefficient: +1.67) – Single strongest predictor; each BMI category shift increases diabetes odds ~5.3x
2. **Physical Activity** (coefficient: -0.89) – Lack of routine physical activity increases odds by ~2.4x
3. **Blood Pressure** (coefficient: +1.12) – History of high blood pressure increases odds ~3.0x
4. **General Health Rating** (coefficient: +0.94) – Self-rated fair/poor health increases odds ~2.6x
5. **Age** (coefficient: +0.67 per decade) – Older age groups show elevated risk
6. **Income Level** (coefficient: -0.34) – **Surprising finding:** Lower-income respondents showed *lower* diabetes risk, inconsistent with typical SES-diabetes associations; likely reflects confounding by healthcare access patterns and BRFSS sampling (landline bias in 2021)
7. **Race/Ethnicity** (coefficient: +0.45) – Non-White respondents showed elevated risk
8. **Alcohol Consumption** (coefficient: -0.28) – Moderate alcohol use associated with lower risk

**Model Performance:** Best-performing logistic regression model achieved **78% overall accuracy** and **AUC=0.81**, indicating good discrimination between diabetes and non-diabetes groups.

---

## Repository Structure

- `Code/Final_Code.R` – Complete analysis pipeline: data loading, cleaning, feature selection, model training, and evaluation
- `Code/SelectVariables_Correlation.R` – Exploratory analysis and LASSO feature selection
- `Data/Population.csv` – US Census 2023 population by state (for weighting/context)
- `Final Code/final_code.Rmd` – RMarkdown report with narrative, visualizations, and inline code
- `Final Presentation Slides/` – Summary slides for stakeholder communication
- `Visualizations/` – Figures and plots for public health audiences

## Technical Notes

**R Version:** 4.2.2  
**Key Packages:** `caret` (modeling), `glmnet` (LASSO), `ROCR` (evaluation), `ggplot2` (visualization)  
**Run Time:** ~30 seconds on standard laptop

To reproduce: Download BRFSS XPT file from CDC, place in working directory, and source `Final_Code.R`.

---

## Interpretation for Non-Technical Audiences

This analysis identifies which factors are most linked to diabetes in real Americans. The strongest findings—BMI, physical inactivity, and high blood pressure—are actionable targets for public health messaging: Americans in higher BMI categories, those not meeting physical activity guidelines, and those with hypertension represent the highest-risk populations. The income finding warrants further investigation (likely a data artifact), but the core behavioral and physiological predictors are clear and consistent with clinical knowledge.

