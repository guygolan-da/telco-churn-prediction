# 🎯 Customer Retention Intelligence System
## ML-Powered Churn Prediction & Retention Strategy for Telecom

![Python](https://img.shields.io/badge/Python-3.8+-blue)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-ML-orange)
![Accuracy](https://img.shields.io/badge/Accuracy-79%25-success)

---

## 📊 Executive Summary

Built a **Random Forest model** to predict customer churn with **79% accuracy**, identifying that **48.3% of new customers churn in their first year**. The model prioritizes high-risk customers with **73% precision** in the top decile, enabling targeted retention campaigns that could save **~$54K annually** by reducing false negatives.

**Key Achievement:** Created custom features (`Is_First_Year`, `Services_Count`) that ranked in the **top 7 most important** predictors, validating business insights through ML.

---

## 🎯 Business Problem

**Challenge:**  
A telecom company has **26% of its customer base** in churned status, losing **$139K** in monthly revenue. Customers who churn pay **21% more** on average ($74 vs $61), indicating we're losing our most valuable customers.

**Questions Answered:**
1. What are the top 3 drivers of customer churn?
2. Is there a critical time window when churn risk peaks?
3. Which high-value customers should we prioritize for retention?

---

## 📁 Dataset

- **Source:** [Telco Customer Churn - Kaggle](https://www.kaggle.com/blastchar/telco-customer-churn)
- **Size:** 7,043 customers
- **Features:** 21 (demographics, services, billing)
- **Target:** Churn (Yes/No)

---

## 🔬 Methodology

### 1. **Data Preparation (SQL + Python)**
- Loaded data into SQLite for querying
- Identified and handled 11 missing values in `TotalCharges`
- Calculated business metrics (ARPU, Churn Rate)

### 2. **Exploratory Data Analysis**
- Analyzed demographics, service usage, and contract types
- Discovered 48.3% first-year churn rate
- Found 831 churners had **zero additional services**

### 3. **Feature Engineering**
- `Is_First_Year`: Binary flag for tenure ≤ 12 months
- `Services_Count`: Sum of security, backup, and support services
- One-hot encoding for categorical variables

### 4. **Model Training**
- Algorithm: **Random Forest** (100 trees)
- Train/Test Split: 80/20
- Performance: 79% accuracy, 65% precision on churners

### 5. **Business Analysis**
- Feature Importance analysis
- Decile segmentation for ROI optimization
- Top 10 at-risk customer profiling

---

## 📈 Key Results

### 🎯 Model Performance
- **Accuracy:** 79%
- **Churn Detection (Recall):** 50% (186 of 373 churners identified)
- **Precision (Top Decile):** 73% - nearly 3 in 4 flagged customers churn

![Confusion Matrix](images/confusion_matrix.png)
*Model evaluation: 942 true negatives, 186 true positives, 187 false negatives*

![Feature Importance](images/feature_importance.png)
*Top 15 features driving churn predictions*

### 🔍 Top 3 Churn Drivers
1. **TotalCharges (19.2%)** - New customers (low lifetime spend) at highest risk
2. **MonthlyCharges (18.7%)** - High-paying customers churn more
3. **Tenure (16.2%)** - First year is critical window

### 📊 Demographic & Service Patterns

![Demographics Analysis](images/demographics_churn.png)
*Churn distribution by gender, age, partner status, and dependents*

![Services & Contract Analysis](images/services_churn.png)
*Churn patterns by internet service, contract type, and payment method*

**Key Observations:**
- Seniors, customers without partners, and without dependents show higher churn
- Fiber Optic users have elevated churn rates
- Month-to-Month contracts strongly correlate with churn
- Electronic Check payment method indicates higher risk

### 📊 Critical Insights

![Advanced Analysis](images/advanced_analysis.png)
*Comprehensive view: Tenure analysis, service engagement, and pricing patterns*

**Finding 1: First-Year Crisis**
- 48.3% churn rate in year 0-1
- Drops to 30% in year 1-2
- Stabilizes at 8% after 5 years

**Finding 2: Service Engagement Matters**
- 831 churners had **0 additional services**
- Clear inverse relationship: more services = less churn

**Finding 3: Value Perception Gap**
- Churners pay **$74/month** on average
- Stayers pay **$61/month** on average
- We're losing high-value customers who don't see ROI

---

## 💡 Business Recommendations

### 🚨 1. Early Warning System
- **Trigger:** Customers with tenure < 12 months + MonthlyCharges > $70 + Services_Count = 0
- **Action:** Proactive outreach at months 1, 3, 6, 12

### 📦 2. Bundle Strategy
- Offer **service bundles** at discounted rates for new customers
- Goal: Increase `Services_Count` from 0 to 2+ in first 90 days
- Example: "Sign up for Fiber + get Online Security free for 3 months"

### 🎯 3. Targeted Retention
- Focus retention budget on **top 20%** risk customers (Deciles 8-9)
- Expected hit rate: **66%** vs 26% random outreach
- **ROI:** 2.5x improvement in retention efficiency

### 💳 4. Payment Friction Reduction
- Migrate customers from Electronic Check to auto-pay
- Offer $5/month discount for switching
- Reduces churn risk by simplifying billing

---

## 🛠️ Technologies Used

**Languages & Libraries:**
- Python 3.8+
- Pandas, NumPy
- Scikit-learn (Random Forest)
- Matplotlib, Seaborn

**Database:**
- SQLite

**Tools:**
- Google Colab

---

## 🚀 How to Run

### Prerequisites
```bash
pip install pandas numpy scikit-learn matplotlib seaborn
```

### Steps
1. Clone the repository
```bash
git clone https://github.com/guygolan-da/telco-churn-prediction.git
cd telco-churn-prediction
```

2. Run the Jupyter Notebook
```bash
jupyter notebook Customer_Churn_Analysis.ipynb
```

3. Or run in Google Colab:
   - Upload the notebook to Google Drive
   - Open with Google Colab

---

## 📂 Project Structure
```
telco-churn-prediction/
├── Customer_Churn_Analysis.ipynb    # Main analysis notebook (9 cells)
├── WA_Fn-UseC_-Telco-Customer-Churn.csv
├── images/                           # Generated visualizations
│   ├── demographics_churn.png
│   ├── services_churn.png
│   ├── confusion_matrix.png
│   ├── feature_importance.png
│   └── advanced_analysis.png
├── telecom_churn.db                  # SQLite database (auto-generated)
├── requirements.txt
└── README.md
```

---

## 📧 Contact

**Guy Golan**  
📧 Email: guygolan39@gmail.com  
💼 LinkedIn: [linkedin.com/in/guy-golan-a077b8157/](https://linkedin.com/in/guy-golan-a077b8157/)

---

## 📜 License

This project is for portfolio purposes. Dataset source: [Kaggle](https://www.kaggle.com/blastchar/telco-customer-churn)

---

*Built with ❤️ as part of my transition to Data Analytics*