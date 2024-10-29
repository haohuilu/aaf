
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
> Both columns have no missing values according to the dataset summary. Each entry in these columns is fully populated across all 306,281 cases. Consequently, imputation is unnecessary for this dataset as there are no missing values for either weight or height.

- **"Identify and flag any outliers in the Z-scores for height-for-age (HAZ), weight-for-age (WAZ), and weight-for-height (WHZ). How would you handle these outliers in the analysis?"**

### Response
> The analysis identified the following outliers in Z-scores based on the threshold of |Z| > 3, a standard cutoff for anthropometric measurements:
> 
> - Height-for-Age Z-score (HAZ): 21,395 cases
> - Weight-for-Age Z-score (WAZ): 11,267 cases
> - Weight-for-Height Z-score (WHZ): 12,121 cases
> 
> These cases have been flagged as outliers in the dataset with new columns (`HAZ_outlier`, `WAZ_outlier`, `WHZ_outlier`), where a `True` value indicates an outlier.
> 
> **Handling Outliers in Analysis**
> 
> 1. **Data Cleaning**: Outliers may result from data entry errors, especially if they are extreme. For these, setting them to `NaN` and then imputing or excluding them may be beneficial.
> 2. **Separate Analysis**: Perform analyses with and without outliers to observe their impact on results. For policy or practical insights, it’s often useful to consider the dataset without extreme outliers.
> 3. **Robust Methods**: Use statistical methods less sensitive to outliers (e.g., median, robust regression) to analyze the data.

- **"Check for consistency between age_in_days and age_in_months. If inconsistencies are found, correct them."**

### Response
> No inconsistencies were found between the `age_in_days` and `age_in_months` fields in the dataset. The age values appear consistent when calculated and compared within a tolerance of 0.5 months, likely accounting for minor rounding differences.

---

## 📈 Descriptive Analysis

Generate summaries to understand the basic characteristics of the dataset and the distribution of undernutrition indicators.

### Prompts
- **"Summarize the distribution of children by Gender, Province, and age_group. What insights can you gather from this summary?"**

### Response
> - **Gender Distribution**:
>   - **Laki-Laki (Male)**: 158,098 cases
>   - **Perempuan (Female)**: 148,183 cases  
>     This slight male majority is common in demographic data but should be monitored to ensure balanced representation in targeted interventions.
>
> - **Province Distribution**:
>   - The data covers a broad geographic scope with entries from 514 provinces or districts.
>   - The top five provinces with the highest representation are:
>     - Bogor: 878 cases
>     - Bekasi: 852 cases
>     - Cilacap: 837 cases
>     - Cianjur: 833 cases
>     - Kebumen: 827 cases
>   - Some provinces, especially in more remote regions, such as **Intan Jaya** (12 cases) and **Nduga** (18 cases), have significantly lower representation, which might affect the robustness of analyses for those areas.
>
> - **Age Group Distribution**:
>   - The age groups are fairly evenly represented, with slightly higher numbers in older groups:
>     - 36-47 months: 67,521 cases
>     - 48-59 months: 67,280 cases
>     - 24-35 months: 62,633 cases
>   - The youngest age groups have fewer cases:
>     - 00-05 months: 23,861 cases
>     - 06-11 months: 26,438 cases
>
> **Insights**
>
> - **Balanced Gender Distribution**: There is a near-equal distribution between males and females, which should allow for gender-inclusive insights.
> - **Provincial Representation Variability**: Larger provinces or urban areas are more represented than smaller, remote provinces. This distributional skew suggests the need for caution when generalizing findings to underrepresented areas.
> - **Age Representation**: There is a natural progression with older age groups having slightly higher representation, which may be due to longer follow-up periods or higher data collection feasibility as children grow older.
>
> This distribution insight emphasizes the importance of targeting both well-represented and underrepresented areas in policy recommendations, especially in regions with sparse data where focused data collection efforts could provide more robust insights.

- **"Calculate the prevalence of stunting, wasting, and underweight. Break down the prevalence by Province, Gender, and age_group."**

### Response
> I have displayed the prevalence of stunting, wasting, and underweight by Province, Gender, and Age Group. This summary allows you to observe the percentage prevalence for each nutritional condition across different demographic segments, providing insights into regions and groups where interventions might be prioritized. If you need any specific breakdown or additional analysis, please let me know.


---

## 📉 Bivariate Analysis

Explore relationships between different variables to understand potential associations or trends in undernutrition indicators.

### Prompts
- **"Investigate whether there is an association between stunting and gender. Are boys more likely to be stunted than girls? Use appropriate statistical tests."**

### Response
> The analysis of stunting by gender, using a Chi-square test for independence, reveals the following results:
> 
> - **Contingency Table (Observed Counts)**:
>   - **Laki-Laki (Male)**: 37,577 cases of stunting, 120,521 cases of non-stunting.
>   - **Perempuan (Female)**: 30,940 cases of stunting, 117,243 cases of non-stunting.
> - **Chi-square Statistic**: 367.34
> - **P-value**: \(7.09 \times 10^{-82}\), which is extremely small and indicates a statistically significant association between gender and stunting at any conventional significance level.
>
> **Interpretation**
>
> The very low p-value suggests that there is a statistically significant association between gender and stunting in this dataset. Specifically, boys (Laki-Laki) are more likely to be stunted compared to girls (Perempuan). This finding could be important for tailoring gender-sensitive interventions to address undernutrition.

- **"Compare the prevalence of underweight across different provinces. Test whether there is a significant difference between provinces."**

### Response
> The Chi-square test for independence on the prevalence of underweight across different provinces yielded the following results:
>
> - **Chi-square Statistic**: 9928.07
> - **P-value**: 0.0 (effectively zero), indicating a statistically significant difference.
> - **Degrees of Freedom**: 513
>
> **Interpretation**
>
> The extremely low p-value suggests that there is a significant difference in underweight prevalence across provinces. This indicates that underweight prevalence is not uniformly distributed and varies considerably depending on the province. This finding underscores the need for region-specific strategies to address undernutrition effectively.

- **"Analyze how the prevalence of wasting varies across different age groups. Use appropriate methods to explore this relationship."**

### Response
> The analysis of wasting prevalence across different age groups reveals the following:
>
> - **Wasting Prevalence by Age Group**:
>   - 00-05 months: 8.91%
>   - 06-11 months: 9.53%
>   - 12-23 months: 11.23%
>   - 24-35 months: 9.53%
>   - 36-47 months: 8.44%
>   - 48-59 months: 8.91%
> - **Chi-square Test Results**:
>   - **Chi-square Statistic**: 329.61
>   - **P-value**: \(4.28 \times 10^{-69}\), indicating a highly significant association between age group and wasting prevalence.
>
> **Interpretation**
>
> The statistical results suggest a significant variation in wasting prevalence across age groups. Notably, children aged 12-23 months have the highest prevalence of wasting (11.23%), potentially indicating increased vulnerability at this stage. This pattern may reflect dietary transitions, infection rates, or other age-specific risk factors and could inform age-targeted interventions.


---
## 🧩 Multivariate Analysis

Dive deeper into the data by building models to determine predictors for various undernutrition conditions.

### Prompts
- **"Build a logistic regression model to determine the predictors of stunting. Include Gender, Province, and age_group as independent variables."**

### Response
> The logistic regression model used **Gender**, **Province**, and **age_group** as predictors for stunting. Here are the results:
> 
> **Classification Report**
> 
> - **Accuracy**: 78%
> - **Precision for Stunting**: Low (no predictions for stunting, indicating model issues in correctly identifying stunted cases)
> - **Weighted Avg Precision and Recall**: Moderate, primarily driven by accurate non-stunting predictions.
> 
> **Coefficients for Predictors**
> 
> - **Gender**: -0.165 (suggests that being female may slightly decrease the odds of stunting)
> - **Province**: -0.000013 (very small impact, suggesting province alone may not be a strong predictor without further refinement)
> - **Age Group**: 0.077 (higher age groups might have a slight increase in odds for stunting, but the effect is small)
> 
> **Interpretation**
> 
> This model shows limited predictive power for stunting cases, likely due to complex relationships that logistic regression might not capture well with the given variables alone. Further model tuning or the addition of more features could improve the predictive accuracy for stunting cases.

- **"Conduct a multinomial logistic regression to analyze the co-occurrence of stunting, wasting, and underweight. How do gender and province influence these conditions?"**

### Response
> To explore the influence of **Gender** and **Province** on the combined conditions of **Stunting**, **Wasting**, **Underweight**, and **Normal**, we ran a multinomial logistic regression model. Here are the findings:
> 
> **Classification Report**
> 
> - **Accuracy**: 68%
> - **Normal**: Achieved a high recall, indicating effective identification of cases without stunting, wasting, or underweight.
> - **Stunted, Underweight, and Wasted**: Low precision and recall, suggesting the model struggles to differentiate these conditions effectively based on **Gender** and **Province** alone.
> 
> **Coefficients for Predictors**
> 
> - **Gender**:
>   - Positive coefficient for **Underweight** (0.192), indicating a slightly higher likelihood of underweight associated with one gender (likely male given initial encoding).
>   - Negative associations with **Stunted** and **Wasted**, though these effects are small.
> - **Province**:
>   - Extremely small coefficients, suggesting minimal influence of **Province** alone on these conditions.
> 
> **Interpretation**
> 
> The model reveals that **Gender** shows a slight influence on underweight status, while **Province** has minimal impact on any of the conditions. The low model performance for stunting, wasting, and underweight suggests that other variables are likely needed to effectively predict these conditions. This insight may indicate the need for additional health, socioeconomic, or nutritional variables to improve the model’s predictive capacity for co-occurring undernutrition conditions.
---

## 📊 Survey Design & Stratified Analysis

Incorporate design variables to account for the survey structure and ensure valid statistical inferences.

### Prompts
- **"Incorporate STRATA and Primary_Sampling_Unit (PSU) into your analysis. Why is it important to account for these variables, and how would you do it?"**

### Response
> **STRATA** and **Primary Sampling Unit (PSU)** are critical design variables in survey data, particularly in complex survey designs. Accounting for these variables in the analysis ensures that the sample structure mirrors the population distribution accurately, leading to more valid inferences about the population.
> 
> 1. **STRATA**: Often used to group the sample by characteristics (e.g., geographic or demographic categories) that may affect the outcome. Analyzing by strata helps prevent over- or under-representation of specific groups, ensuring balanced sampling.
> 2. **PSU**: This groups individuals into sampling clusters, which allows for the adjustment of within-cluster correlations. Without accounting for PSUs, the standard errors can be underestimated, leading to overly optimistic (narrow) confidence intervals and a higher likelihood of Type I errors.
> 
> **Approach for Including STRATA and PSU in the Analysis**
> 
> Incorporating **STRATA** and **PSU** can be done in multiple ways:
> 
> 1. **Using Survey Weights**: A complex survey package, such as `statsmodels` in Python or `survey` in R, enables the inclusion of design weights (e.g., strata and PSU) to adjust estimates and standard errors accordingly.
> 2. **Multilevel Modeling**: With a hierarchical model, **PSU** and **STRATA** can be included as random effects to capture the clustering and stratification in the data, which helps control for within-cluster correlations.

---

## 📊 Visualization

Visualize your findings to enhance interpretation and support evidence-based conclusions.

### Prompts
- **"Create a bar chart or heat map to visualize the provincial distribution of stunting prevalence. What trends do you observe?"**

### Response
> The heat map above visualizes the stunting prevalence across provinces. Here are some trends observed:
> 
> 1. **Regional Variability**: There is significant variation in stunting prevalence among provinces, with certain areas showing considerably higher rates.
> 2. **High-Prevalence Clusters**: Provinces with higher stunting prevalence may indicate areas with specific risk factors related to nutrition, healthcare access, or socioeconomic conditions.
> 3. **Low-Prevalence Regions**: Some provinces exhibit relatively low stunting rates, potentially reflecting better healthcare, nutritional programs, or other supportive conditions.
> 
> These patterns emphasize the need for targeted interventions in high-prevalence regions and possibly further investigation into the factors contributing to lower prevalence in other areas.

- **"Plot the distribution of HAZ, WAZ, and WHZ scores. What can you infer from these distributions about the health status of children in the dataset?"**

### Response
> The distributions of **Height-for-Age (HAZ)**, **Weight-for-Age (WAZ)**, and **Weight-for-Height (WHZ)** Z-scores reveal key insights into the health status of children in the dataset:
> 
> 1. **HAZ (Height-for-Age)**: The HAZ distribution is shifted to the left, indicating that a substantial proportion of children are stunted or have low height-for-age scores. This suggests chronic undernutrition or long-term growth issues in the population.
> 2. **WAZ (Weight-for-Age)**: The WAZ distribution is also left-skewed, implying that many children have lower-than-expected weight for their age. This pattern points toward general undernutrition, which may be either chronic or acute depending on other health and environmental factors.
> 3. **WHZ (Weight-for-Height)**: The WHZ distribution, while slightly skewed left, is less extreme than HAZ and WAZ, suggesting that wasting (acute malnutrition) may be less prevalent than stunting and underweight conditions. However, the presence of a leftward shift still indicates a notable proportion of children with low weight-for-height, potentially reflecting recent or episodic undernutrition.
> 
> These distributions highlight prevalent stunting, underweight, and wasting issues in the dataset, emphasizing the need for interventions targeting both chronic and acute undernutrition among children.

---

## 🔎 Sensitivity Analysis

Test the robustness of your findings by examining how variations in criteria or thresholds impact results.

### Prompts
- **"Perform a sensitivity analysis by changing the Z-score cutoff for stunting from -2 to -3. How does this change impact the prevalence estimates for stunting?"**

### Response
> Changing the Z-score cutoff for stunting from -2 to -3 significantly impacts the prevalence estimates:
> 
> - **Original Stunting Prevalence (HAZ < -2)**: 22.37%
> - **Strict Stunting Prevalence (HAZ < -3)**: 6.20%
> 
> This adjustment shows a substantial decrease in stunting prevalence when using the stricter cutoff of -3, indicating that fewer children meet this severe threshold. This sensitivity analysis highlights the importance of defining cutoffs accurately, as the prevalence rates vary markedly based on the criteria, impacting the identification of children in need of interventions.
---

