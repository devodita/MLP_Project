#  System Threat Forecaster

**Can You Forewarn a System Before It’s Compromised?**  
Ranked in **Top 15 out of 1700+ participants** during my final viva evaluation.

This project was part of the Machine Learning module of the **IIT Madras Online BS Data Science and Applications (Diploma Level)** course. The task involved predicting the likelihood of a system getting infected by malware based on its telemetry data, helping simulate real-world security threat forecasting scenarios.

---

## Project Structure

```text
System-Threat-Forecaster/
├── dataset/
│   ├── train.csv
│   └── test.csv
├── notebook.ipynb
└── README.md
```

---

## Objective

Predict the **probability of malware infection** on a system using its antivirus and hardware-related telemetry data. Each row in the dataset corresponds to a unique machine, and the goal is to model the target variable that indicates malware detection.

---

## Dataset Overview

- `train.csv`: Training data with feature columns and the `target` label.
- `test.csv`: Test data without labels.
- `target`: Binary value indicating if malware was detected (1) or not (0).

### Key Features (partial list)
- `MachineID`, `ProductName`, `EngineVersion`, `OSVersion`, `CountryID`, `CityID`, `Processor`, `RAM`, `FirewallEnabled`, `IsBetaUser`, `IsSecureBootEnabled`, `DateAS`, `DateOS`, etc.

---

## Methodology

The approach was structured and comprehensive:

1. **Initial Analysis**
   - Statistical summary and null value inspection.
   - Exploratory Data Analysis (EDA) to identify correlations, skewness, outliers, and distributions.

2. **Feature Handling**
   - Dropped:
     - High-cardinality or non-informative columns (IDs, constants).
     - Irrelevant features after correlation analysis.
   - Feature Engineering:
     - Parsed version fields (e.g., `x.y.z.w`) into numerical components.
     - Converted date columns into:
       - Weekday
       - Month
       - Year
       - Quarter of the day

3. **Preprocessing Pipeline**
   - Train-validation split
   - Imputation:
     - **Categorical** → most frequent
     - **Numerical** → median (robust to outliers)
   - Encoding:
     - **Ordinal encoding** for categorical
     - **MinMaxScaler** (more suitable for non-Gaussian distributions)

4. **Feature Selection**
   - Used `SelectKBest` with mutual information for dimensionality reduction.

5. **Model Training & Evaluation**
   - Tried multiple models:
     - Naive Bayes, Logistic Regression, KNN, SGD, Decision Trees, Random Forests, XGBoost, LightGBM
   - Ensemble: Stacking classifier
   - Best models tuned using **RandomizedSearchCV**

6. **Results**
   - **Final Accuracy**: **63.74%** on test set
   - Achieved after extensive comparison and fine-tuning

> **Note**: While outlier handling was attempted, it was excluded from the final pipeline as it degraded performance.

---

## Constraints
- Deep learning models were not permitted for this assignment.
- All steps and models were chosen after careful consideration and may not generalize well to different datasets.

---

## Acknowledgements

This project helped me gain a strong foundation in practical machine learning workflows, from raw data to model deployment decisions.  
A big thanks to the **IITM BS team** for designing such an engaging and enriching course!

---

## Contribute

Feel free to fork, explore, or contribute ideas to enhance this further.

---

## Contact

Devodita Chakravarty  
[LinkedIn](https://www.linkedin.com/in/devodita/) | [Email](mailto:devoditac@gmail.com)

---

Happy Coding!
