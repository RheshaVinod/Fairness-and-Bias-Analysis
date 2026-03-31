
## Fairness and Bias Analysis in Machine Learning 

This assignment investigates potential biases in a dataset of facial annotations by analyzing how perceived traits vary across demographic groups (race and gender). Several statistical tests and fairness metrics were used to identify and interpret these biases.

---

## 1. One-Way ANOVA (Race Analysis)

### Purpose
The one-way ANOVA (Analysis of Variance) test is used to determine whether there are statistically significant differences in the means of a variable across **more than two groups**.



Since there are more than two groups, ANOVA is appropriate.

### What it measures
ANOVA compares:
- **Between-group variance** → how different the group means are
- **Within-group variance** → how much variation exists inside each group

### Interpretation
- A **large F-statistic** suggests that group means are different
- A **small p-value (p < 0.05)** indicates statistically significant differences

### Limitation
ANOVA tells us that at least one group differs, but it does **not specify which groups differ**. To interpret direction, we examine group means.

---

## 2. Independent Two-Sample t-Test (Gender Analysis)

### Purpose
The t-test is used to determine whether the means of **two groups** are significantly different.

### Why it was used
Gender has **two groups**:
- Male
- Female

Thus, a t-test is appropriate.

### What it measures
The t-test compares:
- Difference between group means
- Relative to variability within groups

### Interpretation
- **t-statistic**:
  - Positive → first group (Male) has higher mean
  - Negative → second group (Female) has higher mean
- **p-value**:
  - p < 0.05 → statistically significant difference

### Note
Welch’s t-test (unequal variance version) was used for robustness.

---

## 3. Ranking by p-values (Significance Ranking)

### Purpose
To identify the **strongest biases**, traits were ranked based on their p-values.

### Approach
- Combine results from ANOVA (race) and t-tests (gender)
- Sort traits by ascending p-value
- Select top 5 smallest p-values

### Interpretation
- Smaller p-values → stronger evidence of bias
- This ranking highlights the most statistically significant disparities

---

## 4. Histograms (Distribution Visualization)

### Purpose
To visually examine how trait scores are distributed across groups.

### Why it was used
Statistical tests indicate whether differences exist, but visualizations help:
- Understand distribution shape
- Observe shifts between groups
- Assess overlap

### What was analyzed
For the most significant traits:
- Histograms were plotted for each group (Male vs Female)

### Interpretation
- Right shift → higher trait values
- Left shift → lower trait values
- Less overlap → stronger separation between groups

---

## 5. Four-Fifths Rule (Fairness Evaluation)

### Purpose
To evaluate whether the classifier exhibits **adverse impact** on any demographic group.

### Definition
A group is considered disadvantaged if:

Selection Rate < 0.8 × (Highest Selection Rate)

### Steps
1. Compute selection rate:
   - Proportion of individuals labeled as `Qualified = 1`
2. Identify the group with the highest rate
3. Compute 80% of that rate
4. Compare other groups to this threshold

### Interpretation
- If a group falls below the threshold → potential discrimination
- This is a standard fairness metric used in real-world hiring contexts

---

## Summary

This assignment applies:
- **ANOVA** for multi-group comparison (race)
- **t-test** for two-group comparison (gender)
- **p-value ranking** to identify strongest biases
- **histograms** for visualization
- **four-fifths rule** for fairness evaluation

Together, these methods provide both statistical and practical insights into bias and fairness in machine learning systems.
