
# AAF AI Assistant for Child Undernutrition Analysis in Indonesia

The **AAF AI Assistant** is designed to assist in analyzing data related to child undernutrition in Indonesia. This guide outlines the prompts and approaches for various stages of data analysis, from initial data preparation to advanced statistical modeling and interpretation. The categories help identify the right tools and commands for each analysis phase.

## 📊 Data Analysis Categories

1. [Data Cleaning & Preparation](#data-cleaning--preparation)
2. [Descriptive Analysis](#descriptive-analysis)
3. [Bivariate Analysis](#bivariate-analysis)
4. [Multivariate Analysis](#multivariate-analysis)
5. [Survey Design & Stratified Analysis](#survey-design--stratified-analysis)
6. [Visualization](#visualization)
7. [Sensitivity Analysis](#sensitivity-analysis)

---

## 🔄 Data Cleaning & Preparation

Begin by cleaning and preparing the dataset to ensure accurate and reliable analysis results.

### Prompts
- **"Calculate the number of cases where weight or height measurements are missing. Impute the missing values in the dataset."**

### Response
```
Both columns have no missing values according to the dataset summary. Each entry in these columns is fully populated across all 306,281 cases. Consequently, imputation is unnecessary for this dataset as there are no missing values for either weight or height.```

- **"Identify and flag any outliers in the Z-scores for height-for-age (HAZ), weight-for-age (WAZ), and weight-for-height (WHZ). How would you handle these outliers in the analysis?"**
- **"Check for consistency between age_in_days and age_in_months. If inconsistencies are found, correct them."**

### Example
```
Calculate the number of missing values for height and weight measurements and impute them to prepare the data for further analysis.
```

---

## 📈 Descriptive Analysis

Generate summaries to understand the basic characteristics of the dataset and the distribution of undernutrition indicators.

### Prompts
- **"Summarize the distribution of children by Gender, Province, and age_group. What insights can you gather from this summary?"**
- **"Calculate the prevalence of stunting, wasting, and underweight. Break down the prevalence by Province, Gender, and age_group."**

### Example
```
Summarize the distribution of stunting, wasting, and underweight indicators by gender, province, and age group. Highlight key patterns.
```

---

## 📉 Bivariate Analysis

Explore relationships between different variables to understand potential associations or trends in undernutrition indicators.

### Prompts
- **"Investigate whether there is an association between stunting and gender. Are boys more likely to be stunted than girls? Use appropriate statistical tests."**
- **"Compare the prevalence of underweight across different provinces. Test whether there is a significant difference between provinces."**
- **"Analyze how the prevalence of wasting varies across different age groups. Use appropriate methods to explore this relationship."**

### Example
```
Analyze whether there is an association between stunting and gender using statistical tests to check if boys are more likely to be stunted than girls.
```

---

## 🧩 Multivariate Analysis

Dive deeper into the data by building models to determine predictors for various undernutrition conditions.

### Prompts
- **"Build a logistic regression model to determine the predictors of stunting. Include Gender, Province, and age_group as independent variables."**
- **"Conduct a multinomial logistic regression to analyze the co-occurrence of stunting, wasting, and underweight. How do gender and province influence these conditions?"**

### Example
```
Build a logistic regression model to identify significant predictors of stunting, incorporating gender, province, and age group as variables.
```

---

## 📊 Survey Design & Stratified Analysis

Incorporate design variables to account for the survey structure and ensure valid statistical inferences.

### Prompts
- **"Incorporate STRATA and Primary_Sampling_Unit (PSU) into your analysis. Why is it important to account for these variables, and how would you do it?"**

### Example
```
Explain the importance of incorporating STRATA and PSU in the analysis and outline how they would be included in the statistical models.
```

---

## 📊 Visualization

Visualize your findings to enhance interpretation and support evidence-based conclusions.

### Prompts
- **"Create a bar chart or heat map to visualize the provincial distribution of stunting prevalence. What trends do you observe?"**
- **"Plot the distribution of HAZ, WAZ, and WHZ scores. What can you infer from these distributions about the health status of children in the dataset?"**

### Example
```
Generate a heatmap showing stunting prevalence across different provinces in Indonesia and highlight any visible trends.
```

---

## 🔎 Sensitivity Analysis

Test the robustness of your findings by examining how variations in criteria or thresholds impact results.

### Prompts
- **"Perform a sensitivity analysis by changing the Z-score cutoff for stunting from -2 to -3. How does this change impact the prevalence estimates for stunting?"**

### Example
```
Run a sensitivity analysis by adjusting the stunting Z-score threshold from -2 to -3. Compare the impact on prevalence estimates.
```

---

