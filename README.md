# Supply Chain Delivery Performance Analysis

Identified **$2.1M in profit lost to delays** from a **54.71% late delivery rate** across **172,765 global orders** — and built a machine learning model to predict delays before they happen.

The project combines business analytics, root-cause investigation, and machine learning to uncover operational bottlenecks and proactively predict delivery risk.

---

## 📌 Business Problem

A global e-commerce company managing end-to-end order fulfilment across multiple regions was experiencing persistent delivery failures — actual shipping times were consistently exceeding scheduled timelines, leading to late deliveries, unpredictable profitability, and eroding customer trust.

This project analyses the full order fulfilment pipeline, identifies the root causes of delay, and builds a predictive system to flag high-risk orders before dispatch — shifting the operation from reactive complaint management to proactive delay prevention.

---

## 📊 Key Findings

* 📦 **172,765 orders analysed** across global regions after data cleaning
* ⚠️ **54.71% of orders are delayed** — more than half of all orders miss the scheduled delivery window
* 💸 **$2.1M in profit lost to delays** across 94,523 late deliveries
* 📈 **80.66% of orders are profitable**, while 18.69% generate a loss
* 🌍 **Central Africa, East Africa, and West Africa** are the highest-delay regions
* 🚀 **First Class shipping** significantly underperforms relative to its premium positioning
* 🏪 **Health & Beauty, Fan Shop, and Apparel** departments exhibit the highest delay rates
* 📅 Time-based patterns reveal specific months, days, and hours with elevated delivery risk
* 🤖 **Random Forest Classifier achieves 79% accuracy, 83% precision, and 78% recall** in predicting delayed orders

---

## 🗂️ Project Workflow

```text
Raw Data (180,519 Records)

        │
        ▼

1️⃣ Data Cleaning & Feature Engineering
• Dropped 33 redundant, PII, and low-information columns
• Removed cancelled orders → 172,765 clean records remain
• Confirmed Benefit per Order = Order Profit Per Order (duplicate dropped)
• Engineered:
  - Order Processing Time
  - Delay
  - Is_Delayed
  - Profitability Flag
  - order_month
  - order_day
  - order_hour

        │
        ▼

2️⃣ Business KPI Creation
• Total orders
• On-time delivery %
• Late delivery %
• 90th percentile delay
• Total profit
• Financial loss due to delays

        │
        ▼

3️⃣ Profitability Analysis
• Profitability distribution
  - Profit: 80.66%
  - Loss: 18.69%
  - Break-even: 0.65%
• Profit vs Delay Days analysis

        │
        ▼

4️⃣ Bottleneck Detection
• Delay % computed across:
  - Region
  - Shipping Mode
  - Department
  - Customer Segment
  - Payment Type
  - Order Status

        │
        ▼

5️⃣ Root Cause Analysis
• Drilled into highest-delay region (Central Africa)
• Ranked top 10 operational driver combinations by delay %

        │
        ▼

6️⃣ Time-Based Delay Patterns
• Delay trends by:
  - Month
  - Day of Week
  - Hour of Day

        │
        ▼

7️⃣ Machine Learning — Delay Prediction
• Frequency Encoding for categorical variables
• SMOTE balancing applied to training data
• Random Forest Classifier
• Accuracy: 79%
• Precision: 83%
• Recall: 78%
• F1-Score: 80%
• Feature importance analysis
```

---

## 🔍 Visualisations Produced

| No. | Visualisation                        | Purpose                                      |
| --- | ------------------------------------ | -------------------------------------------- |
| 1   | KPI Summary Cards                    | Headline business metrics                    |
| 2   | Profitability Distribution Pie Chart | Profit/Loss/Break-even breakdown             |
| 3   | Delay Distribution Bar Chart         | Distribution of delay days                   |
| 4   | Profit vs Delay Days (Dual Axis)     | Financial impact of delays                   |
| 5   | Bottleneck Detection Dashboard       | Delay % across operational dimensions        |
| 6   | Root Cause Analysis                  | Top delay drivers within highest-risk region |
| 7   | Time Trend Analysis                  | Delay patterns by month/day/hour             |
| 8   | ML Model Performance                 | Precision, Recall, F1-score                  |
| 9   | Feature Importance Analysis          | Most influential delay predictors            |

---

## 🤖 Machine Learning Results

### Model

Random Forest Classifier

### Training Approach

* Frequency Encoding for categorical variables
* Train/Test Split (80/20)
* SMOTE applied to training data only
* Random Forest trained on balanced data

### Performance

| Metric    | Score |
| --------- | ----- |
| Accuracy  | 79%   |
| Precision | 83%   |
| Recall    | 78%   |
| F1-Score  | 80%   |

### Classification Report

| Class   | Precision | Recall | F1-Score |
| ------- | --------- | ------ | -------- |
| On Time | 0.75      | 0.81   | 0.78     |
| Delayed | 0.83      | 0.78   | 0.80     |

The model demonstrates strong and balanced predictive performance across both classes, making it suitable for proactively identifying high-risk orders before shipment.

---

## 🛠️ Tech Stack

| Tool             | Purpose                                         |
| ---------------- | ----------------------------------------------- |
| Python 3         | Core analysis language                          |
| pandas           | Data cleaning, feature engineering, aggregation |
| NumPy            | Numerical operations                            |
| Matplotlib       | Data visualisation                              |
| Seaborn          | Statistical visualisation                       |
| scikit-learn     | Machine learning and evaluation                 |
| imbalanced-learn | SMOTE class balancing                           |

---

## 📁 Repository Structure

```text
supply-chain-delivery-analysis/
│
├── Supply_Chain_Analysis.ipynb
│   └── Full end-to-end analysis notebook
│
└── README.md
    └── Project documentation
```

### Dataset

The dataset is publicly available on Kaggle.

Download the dataset and place it in the project root folder as:

```text
SupplyChainDataset.csv
```

Data Source:

https://www.kaggle.com/datasets/saicharankomati/dataco-supply-chain-dataset/data

---

## ▶️ How to Run

### Clone the Repository

```bash
git clone https://github.com/RushikeshTemghare/supply-chain-delivery-analysis.git

cd supply-chain-delivery-analysis
```

### Install Dependencies

```bash
pip install pandas numpy matplotlib seaborn scikit-learn imbalanced-learn
```

### Download Dataset

Download from Kaggle:

https://www.kaggle.com/datasets/saicharankomati/dataco-supply-chain-dataset/data

Place the file in the project root directory:

```text
SupplyChainDataset.csv
```

### Run the Notebook

```bash
jupyter notebook Supply_Chain_Analysis.ipynb
```

---

## 💡 Strategic Recommendations

Based on the analysis, the highest-impact business actions are:

### 1. Audit First Class Shipping

* Geo-restrict availability in regions with persistent delays
* Renegotiate carrier SLAs where premium service is underperforming

### 2. Improve African Regional Logistics

* Partner with stronger last-mile delivery providers
* Evaluate regional warehousing hubs to reduce transit times

### 3. Optimise Health & Beauty Operations

* Introduce dedicated picking zones
* Accelerate replenishment cycles
* Streamline compliance-related fulfilment processes

### 4. Prepare for Seasonal Demand Peaks

* Forecast delay-prone periods using historical trends
* Secure additional carrier and warehouse capacity in advance

### 5. Optimise Order Cut-Off Times

* Adjust operational schedules based on day-of-week and hour-of-day delay patterns

### 6. Deploy Predictive Delay Scoring

* Integrate the model into order creation workflows
* Prioritise high-risk orders for proactive intervention

---

## 👤 Author

**Rushikesh Temghare**

MSc Data Science & Artificial Intelligence

Focused on applying analytics and machine learning to solve real-world business and supply chain problems.
