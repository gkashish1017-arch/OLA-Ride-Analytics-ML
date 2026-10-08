# 🚕 OLA Ride Analytics — Machine Learning Project

An end-to-end Machine Learning project analyzing **150,000 OLA ride-booking records** to understand booking outcomes and predict `Booking Status` using classification models.

The project covers data cleaning, exploratory data analysis, feature engineering, preprocessing, class-imbalance handling, model comparison, evaluation, feature importance, and business insights.

---

## 📌 Project Overview

Ride-hailing platforms generate large volumes of booking data containing information about customers, vehicles, locations, booking timings, ratings, payment methods, vehicle arrival time, and booking outcomes.

This project analyzes OLA ride-booking data to:

* Understand booking and cancellation patterns
* Identify factors associated with different booking outcomes
* Engineer useful time-based and operational features
* Prepare data for Machine Learning
* Compare multiple classification models
* Handle class imbalance
* Select the most suitable final model
* Translate Machine Learning results into business insights

---

## ⭐ Project Highlights

* Built a multi-class machine learning classification system to predict OLA ride booking outcomes.
* Analyzed **150,000+ ride-booking records** and engineered temporal, behavioral, and categorical features.
* Developed a feature set containing **377 engineered features** for model training.
* Compared multiple classification approaches including Random Forest, Balanced Random Forest, SGD Logistic Regression, and tuned ensemble models.
* Addressed **class imbalance** using a Balanced Random Forest approach.
* Achieved **58.05% accuracy**, **0.5103 Macro F1-score**, and **49.72% balanced accuracy** with the final selected model.
* Evaluated model performance using accuracy, Macro F1, balanced accuracy, classification reports, and confusion matrices.
* Generated business-oriented insights to identify factors associated with successful and unsuccessful ride bookings.

---

## 📊 Project Results & Visualizations

### 🔍 Booking Status Distribution

"C:\Users\gdhru\Downloads\kashish\PROJECTS\OLA-Ride-Analytics-ML\screenshots\01_Booking_Status_Distribution.png"

### 📊 EDA Summary

"C:\Users\gdhru\Downloads\kashish\PROJECTS\OLA-Ride-Analytics-ML\screenshots\02_EDA_Summary.png")

### 🤖 Model Comparison

![Model Comparison](ola_ride_analytics_ml/03_Model_Comparison.png)

### 🏆 Confusion Matrix

![Confusion Matrix](ola_ride_analytics_ml/04_Confusion_Matrix.png)

### 💡 Feature Importance

![Feature Importance](ola_ride_analytics_ml/05_Feature_Importance.png)

---

## 🎯 Business Problem

The objective is to predict the **booking status** of an OLA ride using historical booking information.

The target variable contains five booking outcomes:

* Completed
* Cancelled by Customer
* Cancelled by Driver
* Incomplete
* No Driver Found

Accurate identification of these outcomes can help a ride-hailing business understand operational issues, cancellation behavior, driver availability, and customer experience.

---

## 📊 Dataset

The project uses **150,000 OLA booking records**.

The dataset contains information related to:

* Booking ID
* Booking Date & Time
* Booking Status
* Customer ID
* Vehicle Type
* Pickup Location
* Drop Location
* Average Vehicle Arrival Time (VTAT)
* Average Customer Arrival Time (CTAT)
* Driver Ratings
* Customer Ratings
* Payment Method
* Ride-related attributes

### Dataset Files

| File                   | Description                                     |
| ---------------------- | ----------------------------------------------- |
| `rideBookings.csv`     | Original/raw OLA booking dataset                |
| `ola_ml_processed.csv` | Processed dataset prepared for Machine Learning |

---

## 🧹 Data Preprocessing

The dataset was prepared through a structured preprocessing workflow.

Key steps included:

* Data quality assessment
* Missing-value analysis
* Duplicate checks
* Data type conversion
* Date and time processing
* Removal of outcome-dependent/post-ride variables
* Categorical feature encoding
* Numerical feature preprocessing
* Feature engineering
* Train-test splitting
* Validation of processed feature matrices

The final preprocessing pipeline generated **377 processed features** after one-hot encoding.

The training and testing datasets were validated to ensure:

* Same number of processed features
* Matching feature names
* No missing values after preprocessing

---

## 🕒 Feature Engineering

Date and time information was transformed into useful predictive features.

Important engineered features include:

* `Year`
* `Month`
* `Day`
* `Hour`
* `Day_of_Week`
* `Day_Period`
* `Is_Weekend`

A `VTAT_Missing` indicator was also created to capture missing vehicle-arrival-time information.

---

## 🔍 Exploratory Data Analysis

The analysis examined:

* Booking status distribution
* Vehicle types
* Pickup and drop locations
* Booking trends over time
* Driver ratings
* Customer ratings
* Payment methods
* Cancellation behavior
* Driver availability
* Temporal booking patterns

### Booking Outcome Distribution

Approximately:

* **62%** of bookings were completed
* **18%** were cancelled by drivers
* **7%** were cancelled by customers

The remaining bookings were primarily associated with incomplete rides and no-driver-found outcomes.

---

## 🤖 Machine Learning Approach

Multiple classification models were evaluated on the same test dataset.

### Models Evaluated

1. Random Forest — Baseline
2. Random Forest — Without VTAT
3. Balanced Random Forest
4. SGD Logistic Regression
5. Tuned Balanced Random Forest
6. XGBoost

The dataset contains imbalanced booking-status classes, so model selection was not based on Accuracy alone.

### Primary Evaluation Metric

**Macro F1-score** was selected as the primary metric because it gives equal importance to all booking-status classes, including minority classes.

Additional metrics used:

* Accuracy
* Balanced Accuracy
* Precision
* Recall
* F1-score

---

## 📈 Model Comparison

| Model                        |   Accuracy |   Macro F1 | Balanced Accuracy |
| ---------------------------- | ---------: | ---------: | ----------------: |
| Random Forest — Baseline     |     71.33% |     0.4637 |            0.4676 |
| Random Forest — Without VTAT |     61.95% |     0.1536 |            0.2001 |
| **Balanced Random Forest**   | **58.05%** | **0.5103** |        **0.4972** |
| SGD Logistic Regression      |     58.90% |     0.4746 |            0.4575 |
| Tuned Balanced Random Forest |     23.18% |     0.3610 |        **0.5440** |
| XGBoost                      |     71.37% |     0.4637 |            0.4677 |

### Model Selection

The **Balanced Random Forest** was selected as the final model because it achieved the highest **Macro F1-score of 0.5103**.

Although the Tuned Balanced Random Forest achieved the highest Balanced Accuracy of 54.40%, its Accuracy and Macro F1-score were substantially lower.

The Baseline Random Forest and XGBoost achieved approximately 71% Accuracy, but their lower Macro F1-scores indicate that their performance was strongly influenced by the majority `Completed` class.

---

## 🏆 Final Model Performance

### Balanced Random Forest

The final model was evaluated on **30,000 unseen test records**.

| Metric            |     Result |
| ----------------- | ---------: |
| Accuracy          | **58.05%** |
| Macro F1-score    | **0.5103** |
| Balanced Accuracy | **49.72%** |

The final model provides a better balance across the five booking-status classes than the other evaluated models.

---

## 📋 Classification Report

| Booking Status        | Precision | Recall | F1-score |
| --------------------- | --------: | -----: | -------: |
| Cancelled by Customer |      0.93 |   0.34 |     0.50 |
| Cancelled by Driver   |      0.26 |   0.48 |     0.33 |
| Completed             |      0.72 |   0.64 |     0.68 |
| Incomplete            |      0.09 |   0.03 |     0.04 |
| No Driver Found       |      1.00 |   1.00 |     1.00 |

### Interpretation

The model performs particularly well for:

* `No Driver Found`
* `Completed`

However, it struggles with:

* `Incomplete`
* `Cancelled by Driver`

This shows that different booking outcomes have significantly different levels of predictability.

---

## ⭐ Feature Importance

Feature importance from the final Balanced Random Forest provides useful insight into the operational factors driving predictions.

### Top Features

| Feature      | Importance |
| ------------ | ---------: |
| Avg VTAT     | **21.09%** |
| VTAT_Missing | **20.13%** |
| Day          |  **4.43%** |
| Hour         |  **3.91%** |
| Month        |  **3.76%** |

`Avg VTAT` and `VTAT_Missing` together contribute approximately **41.22%** of the model's total feature importance.

This indicates that vehicle arrival-time information and its availability are highly influential in predicting booking outcomes.

---

## 💡 Business Insights

### 1. Completed bookings are the majority outcome

Approximately 62% of bookings were completed.

**Business implication:** Increasing the conversion of unsuccessful bookings into completed rides could improve customer experience and operational efficiency.

### 2. Driver cancellations are a major unsuccessful outcome

Driver cancellations account for approximately 18% of all bookings.

**Business implication:** OLA could investigate recurring driver-cancellation reasons and identify operational conditions associated with higher cancellation rates.

### 3. Vehicle arrival information is highly influential

`Avg VTAT` is the most important feature, contributing approximately 21.09% of total feature importance.

**Business implication:** Improving dispatch and vehicle-arrival performance may have a meaningful relationship with booking outcomes.

### 4. No-driver-found bookings are highly predictable

The model achieves 100% precision, recall, and F1-score for `No Driver Found`.

This is strongly influenced by the `VTAT_Missing` feature.

**Business implication:** Missing vehicle-arrival information can act as a strong operational signal for identifying driver-availability issues.

### 5. Incomplete rides are difficult to identify

The `Incomplete` class has an F1-score of only 0.04.

**Business implication:** Additional operational or behavioral features may be required to better identify incomplete rides.

---

## ⚠️ Leakage & Operational-Stage Caveat

The final model includes:

* `Avg VTAT`
* `VTAT_Missing`

These variables contain information from the operational/dispatch stage of a booking.

Therefore, this project should **not** be interpreted as a pure pre-booking prediction model.

Instead, the model represents an **operational-stage booking-outcome prediction scenario**.

The strong importance of `Avg VTAT` and `VTAT_Missing` also means that the model's performance is highly dependent on operational-stage information.

In particular, `VTAT_Missing` perfectly identifies the `No Driver Found` category in this dataset.

---

## 🛠️ Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-learn
* XGBoost
* Jupyter Notebook
* Git
* GitHub

---

## 📁 Project Structure

```text
OLA-Ride-Analytics-ML/
│
├── OLA_Ride_Analytics_ML.ipynb
│
├── rideBookings.csv
├── ola_ml_processed.csv
│
├── ola_preprocessor.pkl
├── ola_feature_names.pkl
│
├── ola_model_comparison.csv
├── ola_final_metrics.json
│
├── .gitignore
└── README.md
```

> The trained `ola_balanced_random_forest.pkl` file is intentionally excluded from GitHub because its size is approximately 1.4 GB.

---

## ▶️ How to Run

### 1. Clone the repository

```bash
git clone https://github.com/gkashish1017-arch/OLA-Ride-Analytics-ML.git
```

### 2. Open the project

```bash
cd OLA-Ride-Analytics-ML
```

### 3. Install dependencies

```bash
pip install pandas numpy matplotlib seaborn scikit-learn xgboost jupyter
```

### 4. Open the notebook

```bash
jupyter notebook OLA_Ride_Analytics_ML.ipynb
```

### 5. Run the notebook

Execute the notebook cells sequentially to reproduce the data-preparation, analysis, Machine Learning, evaluation, and feature-importance workflow.

---

## 🚀 Future Improvements

Potential improvements include:

* Hyperparameter optimization
* Additional operational features
* Better handling of minority classes
* Model explainability using SHAP
* More robust validation strategies
* Streamlit deployment
* Real-time prediction pipeline
* Interactive analytics dashboard
* Model monitoring and retraining

---

## 👨‍💻 Author

**Kashish**

Data Analytics & Machine Learning Portfolio Project

---

## ⭐ Project Highlights

* **150,000** OLA booking records analyzed
* **377** processed Machine Learning features
* **6** classification approaches evaluated
* **Balanced Random Forest** selected as the final model
* **58.05% Accuracy**
* **0.5103 Macro F1-score**
* **49.72% Balanced Accuracy**
* Class-imbalance-aware model selection
* Feature importance analysis
* Operational-stage prediction caveat documented
* End-to-end Python Machine Learning workflow

