# Predictive Modeling and Optimization in Logistics Systems

## Project Overview

This project was completed as part of the **Yuva Intern – Logistics Data Analyst Internship**.

The objective of the project is to develop a predictive modeling framework for forecasting **shipment delivery time** and demonstrate how predictive analytics can support logistics optimization and operational decision-making.

The project follows an end-to-end machine-learning workflow including data simulation, exploratory data analysis, preprocessing, baseline modeling, multiple regression algorithms, cross-validation, hyperparameter tuning, model diagnostics, feature-importance analysis, and scenario-based logistics optimization.

> **Important:** The dataset used in this project is hypothetical and was created for analytical and educational purposes. The results should not be interpreted as actual performance of a real logistics organization.

---

## Prediction Problem

**Target Variable:** `Delivery_Time_Hours`

The model predicts shipment delivery duration using operational shipment characteristics.

### Numerical Predictors

- Distance_km
- Shipment_Volume_kg
- Warehouse_Processing_Hours

### Categorical Predictors

- Region
- Transport_Mode
- Priority
- Traffic_Level
- Weather_Condition

The dataset contains **2,000 simulated shipments and 11 variables**, with no missing values or duplicate rows in the validated dataset.

---

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- Google Colab
- GitHub

---

## Modeling Workflow

The predictive modeling process included:

1. Logistics problem definition and hypothetical data simulation
2. Data-quality validation
3. Exploratory data analysis
4. Distribution and relationship analysis
5. Train-test splitting
6. Numerical and categorical preprocessing
7. Mean-based baseline model
8. Linear Regression
9. Decision Tree Regression
10. Random Forest Regression
11. Model comparison
12. 5-fold cross-validation
13. Random Forest hyperparameter tuning
14. Final held-out test evaluation
15. Actual vs Predicted analysis
16. Residual diagnostics
17. Feature-importance analysis
18. Transportation-mode what-if analysis
19. Warehouse-processing optimization scenario
20. Evidence-based logistics recommendations

---

## Model Performance

| Model | Test MAE | Test RMSE | Test R² |
|---|---:|---:|---:|
| Baseline Mean | 16.61 h | 19.97 h | ≈ 0.000 |
| Linear Regression | 5.10 h | 7.22 h | 0.869 |
| Decision Tree | 4.18 h | 5.32 h | 0.929 |
| Random Forest | 2.85 h | 3.61 h | 0.967 |
| Tuned Random Forest | **2.83 h** | **3.57 h** | **0.968** |

The tuned Random Forest was selected as the final predictive model after considering test-set performance, cross-validation stability, and hyperparameter tuning.

---

## Cross-Validation and Hyperparameter Tuning

Five-fold cross-validation was used to evaluate model stability.

The Random Forest achieved a mean cross-validation MAE of approximately **3.10 hours**, with a standard deviation of **0.11 hours**.

Hyperparameter tuning using `GridSearchCV` reduced cross-validation MAE to approximately **3.04 hours**, representing a **1.99% improvement**.

The selected Random Forest configuration used:

- `n_estimators = 250`
- `max_depth = None`
- `min_samples_leaf = 1`
- `max_features = 0.8`

The improvement from tuning was measurable but modest, so it is reported without overstating its operational impact.

---

## Key Analytical Findings

Shipment distance was the strongest individual predictive feature, accounting for **56.61%** of the Random Forest's impurity-based feature importance.

Transportation mode also contributed substantial predictive information. The Air indicator accounted for **23.23%** and the Sea indicator for **13.16%** of model importance.

Earlier exploratory analysis showed a Pearson correlation of approximately **0.712** between shipment distance and delivery time.

Transport-mode analysis also showed substantial differences in simulated average delivery duration:

- Air: **15.36 hours**
- Rail: **32.58 hours**
- Road: **37.90 hours**
- Sea: **54.54 hours**

Feature importance is interpreted as predictive contribution within the fitted model and **not as evidence of causation**.

---

## Model Diagnostics

The final tuned Random Forest achieved:

- **MAE:** 2.83 hours
- **RMSE:** 3.57 hours
- **R²:** 0.968
- **Mean residual:** 0.21 hours
- **Minimum residual:** −9.84 hours
- **Maximum residual:** 12.91 hours

The residual analysis indicates relatively small overall directional bias, while also showing that meaningful individual prediction errors remain.

Therefore, predictions should support logistics decisions rather than be interpreted as guaranteed delivery times.

---

## Transportation Mode What-If Analysis

A controlled 1,500 km shipment scenario was evaluated while holding other shipment characteristics constant.

| Transport Mode | Predicted Delivery Time |
|---|---:|
| Air | 13.87 h |
| Rail | 28.81 h |
| Road | 34.36 h |
| Sea | 54.08 h |

The scenario demonstrates how model predictions can support transportation-mode evaluation.

However, the fastest predicted mode is not automatically the optimal business decision. Real mode selection would also require transportation cost, capacity, availability, route feasibility, service requirements, and other operational constraints.

---

## Warehouse Processing Optimization Scenario

A controlled Road-shipment scenario was evaluated using different warehouse processing times.

Predicted delivery time increased from **34.07 hours at 2 hours of warehouse processing** to **37.70 hours at 10 hours of processing**, a difference of **3.63 hours**.

The relationship was nonlinear, demonstrating how a Random Forest can represent patterns that are not captured by a constant linear coefficient.

The result supports targeted warehouse-process improvement, particularly for shipments with tight service deadlines or high predicted delivery durations.

---

## Logistics Optimization Recommendations

The analysis supports several decision-oriented recommendations:

- Use predicted delivery time as a pre-shipment planning KPI.
- Flag shipments with unusually high predicted delivery durations for operational review.
- Evaluate transportation modes against service deadlines before considering cost and capacity constraints.
- Give additional planning attention to long-distance shipments.
- Target warehouse-processing improvements where expected service benefits justify additional resources.
- Combine point predictions with operational risk monitoring.
- Monitor MAE, RMSE, residual patterns, and performance drift after deployment.
- Retrain and revalidate models as operating conditions change.
- Extend future work toward multi-objective optimization using cost, capacity, routing, service-level, and environmental constraints.

---

## Visualization Strategy

Different visualization methods were selected according to the analytical question rather than using one chart type repeatedly.

- **Histogram:** Used to examine the distribution of delivery time.
- **Box plot:** Used to compare delivery-time distributions and variability across transportation modes.
- **Scatter plot:** Used for Actual vs Predicted analysis and residual diagnostics.
- **Horizontal bar chart:** Used for feature importance because transformed feature names require readable categorical comparison.
- **Line chart:** Used for the ordered warehouse-processing what-if scenario.

Each visualization complements numerical metrics and provides information that summary statistics alone cannot show.

---

## Repository Contents

```text
predictive-logistics-modeling/
│
├── Task_4_Hypothetical_Logistics_Dataset.csv
├── Yuva_Intern_Task_4_Predictive_Logistics_Modeling.ipynb
├── Task_4_Predictive_Modeling_and_Optimization_Report.docx
├── README.md
│
└── Charts/
    ├── Task_4_Delivery_Time_Distribution.png
    ├── Task_4_Delivery_Time_by_Transport_Mode.png
    ├── Task_4_Actual_vs_Predicted_Delivery_Time.png
    ├── Task_4_Random_Forest_Residual_Plot.png
    ├── Task_4_Random_Forest_Feature_Importance.png
    └── Task_4_Warehouse_Processing_Optimization.png
```

---

## Limitations

The project uses **simulated data**, so the strong predictive performance partly reflects relationships intentionally incorporated into the data-generation process.

Cross-validation and test evaluation provide internal validation within this simulated environment but do not constitute external validation on real logistics data.

The dataset also does not contain several variables required for complete logistics optimization, including transportation cost, vehicle capacity, route availability, fuel consumption, labor constraints, and service penalties.

A real implementation would therefore require validation using actual operational data and integration with business-specific constraints.

---

## Conclusion

This project demonstrates an end-to-end approach to applying predictive analytics to logistics delivery-time forecasting.

The analysis goes beyond model training by incorporating baseline comparison, multiple predictive algorithms, cross-validation, hyperparameter tuning, diagnostic analysis, model interpretation, and controlled optimization scenarios.

The final tuned Random Forest achieved strong internal predictive performance within the hypothetical dataset, while the scenario analyses demonstrate how delivery-time predictions can contribute to transportation planning, warehouse improvement, shipment prioritization, and broader logistics optimization.

The final model is best understood as a **predictive decision-support component** that could be integrated into a broader logistics optimization framework rather than as an autonomous decision-making system.

---

**Prepared by:** Japkirat Kaur  
**Role:** Logistics Data Analyst Intern  
**Organization:** Yuva Intern  
**Project:** Week 4 – Predictive Modeling and Optimization in Logistics Systems
