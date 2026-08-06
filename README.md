# 🛒 E-Commerce Conversion Funnel & Drop-Off Analysis

## 📌 Project Overview

This project analyzes **E-Commerce user behavior and conversion funnel performance** to identify where users drop off during their shopping journey and what factors influence conversion.

The analysis tracks the customer journey across four major stages:

**Browse → Add to Cart → Checkout → Purchase**

The goal is to identify funnel bottlenecks, understand user behavior across devices, regions, product categories, and acquisition channels, and develop a predictive model to estimate the likelihood of session conversion.

The project combines **Exploratory Data Analysis, Funnel Analysis, Predictive Analytics, SQL-based analysis, and Power BI dashboarding**.

---

## 🎯 Objectives

* Perform comprehensive **Exploratory Data Analysis (EDA)** on E-Commerce user behavior.
* Clean and preprocess event-level user session data.
* Reconstruct chronological user journeys from event logs.
* Analyze conversion and drop-off at each funnel stage.
* Identify behavioral patterns across:

  * Devices
  * Regions
  * Acquisition channels
  * Product categories
* Perform cohort and multivariate analysis.
* Develop a **Random Forest classification model** to predict session conversion.
* Build an interactive **Power BI dashboard** for monitoring funnel performance.
* Generate actionable business recommendations for improving conversion.

---

## 📊 Dataset

**Dataset:** `funnel_analysis_data.csv`

| Attribute       | Details                           |
| --------------- | --------------------------------- |
| Records         | 21,663                            |
| Features        | 10                                |
| Missing Values  | 0                                 |
| Duplicate Rows  | 0                                 |
| Target Variable | Conversion                        |
| Data Type       | Event-level E-Commerce data       |
| Geography       | North, South, East & West regions |

The dataset contains event-level tracking information for distinct user sessions.

### Dataset Features

| Column             | Description                                              |
| ------------------ | -------------------------------------------------------- |
| `User_ID`          | Unique platform user identifier                          |
| `Session_ID`       | Unique browsing session identifier                       |
| `Event`            | User action: Browse, Add to Cart, Checkout, Purchase     |
| `Timestamp`        | Date and time of the event                               |
| `Device`           | Desktop, Mobile, or Tablet                               |
| `Region`           | Geographical region                                      |
| `Channel`          | Marketing acquisition channel                            |
| `Product_Category` | Product category interacted with                         |
| `Revenue`          | Revenue generated from the event                         |
| `Bounce_Flag`      | Indicates whether the user abandoned meaningful activity |

---

## 🔄 Project Workflow

```text
Raw E-Commerce Data
        ↓
Data Ingestion
        ↓
Data Cleaning & Validation
        ↓
Feature Engineering
        ↓
DuckDB SQL Analysis
        ↓
Exploratory Data Analysis
        ↓
Funnel & Drop-Off Analysis
        ↓
Predictive Modeling
        ↓
Power BI Dashboard
        ↓
Business Insights & Recommendations
```

---

## 🧹 Data Preprocessing

The preprocessing pipeline includes:

1. Loading the dataset using Pandas.
2. Checking for missing values and duplicates.
3. Converting `Timestamp` into datetime format.
4. Sorting events by `User_ID` and `Timestamp`.
5. Reconstructing chronological session behavior.
6. Creating additional behavioral features:

   * `Hour_of_Day`
   * `Day_of_Week`
   * `Time_Since_Last_Action`
7. Exporting the refined dataset as:

```text
cleaned_funnel_data.csv
```

The original document reports **0 missing values and 0 duplicate rows** in the dataset.

---

## 📈 Exploratory Data Analysis

The analysis focuses on understanding:

* Funnel stage conversion
* User drop-off behavior
* Device performance
* Acquisition channel performance
* Regional differences
* Product category revenue
* Shopping time patterns
* Bounce behavior
* Revenue and Average Order Value (AOV)

### 🔻 Funnel Performance

The documented baseline funnel analysis reports:

* **Browse → Add to Cart:** 70.59%
* **Checkout → Purchase:** 30.65%
* **Overall session conversion:** 10.8%

The largest bottleneck occurs between **Checkout and Purchase**, where approximately **69.35% of users drop off**.

---

## 💰 Revenue Analysis

According to the project analysis:

* **Electronics** is the leading revenue-generating category.
* Electronics generated approximately **$256,035.81** across **229 purchases**.
* Reported Electronics AOV is approximately **$1,118.06**.

---

## 📱 Device Analysis

The analysis compares conversion and purchase behavior across:

* Desktop
* Mobile
* Tablet

The documented purchase volumes are:

| Device  | Purchases |
| ------- | --------: |
| Tablet  |       383 |
| Mobile  |       369 |
| Desktop |       328 |

Tablet users therefore recorded the highest purchase volume in the analyzed dataset.

---

## 🤖 Predictive Modeling

A **Random Forest Classifier** was designed to predict whether a session would eventually result in a purchase.

### Model Objective

Predict:

```text
Conversion = 1 → Purchase
Conversion = 0 → No Purchase
```

The model uses early-stage session behavior, with the documented objective being to predict conversion based on the **first five minutes of a session**.

### Documented Model Setup

* Algorithm: **Random Forest Classifier**
* Train/Test Split: **80% / 20%**
* Reported Accuracy: **87.4%**
* Reported Positive-Class F1 Score: **0.82**

The design document explicitly labels these modelling values as **hypothetical estimates**, so they should be treated as illustrative until reproduced from the actual implementation.

### Reported Conversion Drivers

**Positive drivers**

1. `Channel_Email`
2. `Device_Tablet`

**Negative drivers**

1. `Time_Since_Last_Action > 300s`
2. `Bounce_Flag_Yes`

These feature-importance findings are also part of the document's hypothetical modelling section.

---

## 🗄️ SQL Analysis with DuckDB

DuckDB is used for analytical SQL queries on the processed data.

The architecture uses:

```text
Pandas DataFrame
      ↓
DuckDB
      ↓
Aggregated Funnel Tables
      ↓
Business Analysis
```

This allows analytical SQL operations to be performed efficiently on the dataset before visualization and reporting.

---

## 📊 Power BI Dashboard

An interactive **Power BI dashboard** was designed to monitor funnel performance and identify conversion bottlenecks.

### Dashboard Components

| Visualization | Purpose                                           |
| ------------- | ------------------------------------------------- |
| Funnel Chart  | Shows user drop-off across funnel stages          |
| Bar Chart     | Compares device performance and revenue/purchases |
| Matrix/Table  | Analyzes product category performance and AOV     |
| Line Chart    | Examines conversion patterns by hour              |

The dashboard can be filtered by dimensions such as:

* Device
* Channel
* Product Category

---

## 🔎 Key Findings

### 1. Checkout is the biggest bottleneck

Approximately **69.35% drop-off** is reported between Checkout and Purchase.

### 2. Cart abandonment is significant

The documented analysis reports approximately **50.08% drop-off from Cart to Checkout**.

### 3. Tablet recorded the highest purchase volume

Tablet users recorded **383 purchases**, compared with 369 Mobile and 328 Desktop purchases.

### 4. Electronics is the leading revenue category

Electronics generated approximately **$256K** in reported revenue.

### 5. Overall conversion rate

The baseline conversion rate is reported as approximately **10.8%**.

---

## ⚠️ Important Note on Hypothetical Insights

Some insights in the Model Design Document are explicitly marked as **hypothetical/domain-based estimates**, including:

* Time-to-conversion relationships
* Acquisition-channel performance comparisons
* Correlation values
* Certain device/channel combinations
* Model performance
* Estimated conversion improvements

These figures should **not be interpreted as experimentally validated results** unless reproduced and validated using the underlying dataset and analysis code.

This distinction is important when presenting the project in a professional or interview setting.

---

## 💡 Business Recommendations

Based on the documented analysis, the project recommends:

### 🛒 Improve Checkout Flow

Address the high Checkout → Purchase drop-off by considering:

* One-click checkout
* Guest checkout
* Simplified payment experience

### 📱 Improve Mobile Experience

Conduct a dedicated UI/UX audit of:

* Mobile cart experience
* Checkout pages
* Payment flow

### 📧 Optimize Marketing

Increase focus on **Email retargeting campaigns** where appropriate and evaluate acquisition-channel ROI.

### 🛍️ Improve Merchandising

Use high-performing categories such as **Electronics and Fashion** to support lower-performing categories through bundling and merchandising strategies.

---

## 🛠️ Technologies Used

### Programming & Data Analysis

* Python 3.x
* Pandas
* NumPy
* Scikit-learn

### SQL & Analytics

* DuckDB
* SQL

### Visualization

* Matplotlib
* Seaborn
* Plotly

### Business Intelligence

* Microsoft Power BI

The project document identifies these tools as the core technologies used across ingestion, processing, visualization, modelling, and BI reporting.

---

## 📁 Project Deliverables

The documented project deliverables include:

```text
funnel_analysis_data.csv
cleaned_funnel_data.csv
Python data-processing scripts
DuckDB SQL analysis
Predictive model documentation
Power BI dashboard
```

---

## ⚠️ Limitations

The current project has several limitations:

* No demographic information such as age, gender, or income.
* Product categories are broad and do not contain SKU-level information.
* The predictive model assumes historical behavior remains relatively stable.
* Seasonality is not incorporated into the current modelling approach.

---

## 🚀 Future Improvements

Potential improvements include:

### 1. Demographic Enrichment

Integrate additional demographic data to develop more detailed customer personas.

### 2. Real-Time Analytics

Move from batch CSV processing toward a streaming architecture for real-time cart-abandonment detection.

### 3. A/B Testing

Implement controlled A/B tests to validate proposed checkout and UI/UX improvements.

---

## 📌 Conclusion

This project demonstrates an end-to-end **E-Commerce conversion analytics workflow**, starting from raw event-level data and progressing through data cleaning, feature engineering, SQL analysis, exploratory analysis, predictive modelling, and interactive Power BI reporting.

The primary documented bottleneck is the **Checkout → Purchase stage**, while device type, product category, and acquisition channel provide important dimensions for understanding conversion behavior.

The project combines technical data-analysis skills with business-oriented insights to identify potential opportunities for improving **conversion rate, customer experience, and revenue performance**.

---

## 👨‍💻 Author

**Ankush Saini**
Data Analyst Intern — SYNTECXHUB
