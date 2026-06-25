🚚 Supply Chain Delivery Performance Analysis


Identified $2.1M in profit lost to delays from a 54.71% late delivery rate across 172,765 global orders — and built a machine learning model to predict delays before they happen.



📌 Business Problem

A global e-commerce company managing end-to-end order fulfilment across multiple regions was experiencing persistent delivery failures — actual shipping times were consistently exceeding scheduled timelines, leading to late deliveries, unpredictable profitability, and eroding customer trust.

This project analyses the full order fulfilment pipeline, identifies the root causes of delay, and builds a predictive system to flag high-risk orders before dispatch — shifting the operation from reactive complaint management to proactive delay prevention.



📊 Key Findings


📦 172,765 orders analysed across global regions after data cleaning
⚠️ 54.71% of orders are delayed — just over half of all orders miss the scheduled window
💸 $2.1M in profit lost to delays — across 94,523 late deliveries
📈 80.66% of orders are profitable — yet 18.69% generate a loss
🌍 Central Africa, East Africa and West Africa are the highest-delay regions
🚀 First Class shipping significantly underperforms vs. its premium positioning
🏪 Health & Beauty, Fan Shop and Apparel departments show the highest delay rates
📅 Time-based patterns reveal specific months, days and hours with elevated delays
🤖 Random Forest model achieves ~74% accuracy in predicting delayed orders



🗂️ Project Workflow

Raw Data (180,519 records)
        │
        ▼
1️⃣  Data Cleaning & Feature Engineering
    • Dropped 33 redundant, PII, and low-information columns
    • Removed cancelled orders → 172,765 clean records remain
    • Confirmed Benefit per Order = Order Profit Per Order (duplicate dropped)
    • Engineered: Order Processing Time, Delay, Is_Delayed,
      Profitability Flag, order_month, order_day, order_hour
        │
        ▼
2️⃣  Business KPI Creation
    • Total orders, on-time %, late %, 90th percentile delay
    • Total profit, financial loss due to delays
        │
        ▼
3️⃣  Profitability Analysis
    • Profitability distribution (Profit 80.66% / Loss 18.69% / Break-even 0.65%)
    • Profit vs. delay days (dual-axis bar + line chart)
        │
        ▼
4️⃣  Bottleneck Detection
    • Delay % computed across 6 dimensions:
      Region, Shipping Mode, Department, Customer Segment, Payment Type, Order Status
        │
        ▼
5️⃣  Root Cause Analysis
    • Drilled into highest-delay region (East Africa)
    • Top 10 driver combinations ranked by delay %
        │
        ▼
6️⃣  Time-Based Delay Patterns
    • Delay trends by month, day of week, and hour of day
        │
        ▼
7️⃣  Machine Learning — Delay Prediction
    • Frequency encoding → SMOTE balancing → Random Forest Classifier
    • ~74% accuracy | balanced precision/recall on both classes
    • Feature importance: Region > Shipping Mode > Department



🔍 Visualisations Produced

No	Chart	Purpose
1	KPI Summary Cards	Headline business metrics at a glance
2	Profitability Distribution Pie	Order-level profit/loss/break-even breakdown
3	Delay Distribution Bar Chart	Spread of delay days across all orders
4	Profit vs. Delay Days (dual-axis)	Financial impact of each delay day
5	Bottleneck Detection (2×3 grid)	Delay % across all 6 operational dimensions
6	Root Cause — East Africa	Top 10 driver combinations by delay %
7	Time Series (Month / Day / Hour)	When delays are most likely to occur
8	ML Model Performance	Precision, Recall, F1 by class
9	Feature Importance	Which variables drive delay prediction most




🛠️ Tech Stack

Tool	Purpose
Python 3	Core analysis language
pandas	Data cleaning, feature engineering, aggregation
NumPy	Numerical operations
Matplotlib & Seaborn	All data visualisations (viridis palette)
scikit-learn	Random Forest Classifier, train/test split, evaluation metrics
imbalanced-learn	SMOTE for class imbalance handling


📁 Repository Structure

supply-chain-delivery-analysis/
│
├── Supply_Chain_Analysis.ipynb          # Full analysis notebook (end-to-end)
└── README.md                            # You are here


Dataset: The dataset is publicly available on Kaggle — download it and place it in the root folder as SupplyChainDataset.csv

🔗 DataCo Supply Chain Dataset - https://www.kaggle.com/datasets/saicharankomati/dataco-supply-chain-dataset/data — Kaggle



▶️ How to Run

1. Clone the repository
git clone https://github.com/RushikeshTemghare/supply-chain-delivery-analysis.git
cd supply-chain-delivery-analysis

2. Install required libraries
pip install pandas numpy matplotlib seaborn scikit-learn imbalanced-learn

3. Download the dataset from Kaggle (link - https://www.kaggle.com/datasets/saicharankomati/dataco-supply-chain-dataset/data)
Place it in the root folder as: SupplyChainDataset.csv

4. Open the notebook
jupyter notebook Supply_Chain_Analysis.ipynb


💡 Strategic Recommendations

Based on the analysis, the top actions identified for the business are:


Audit First Class Shipping — Geo-restrict availability in regions where delay rate is highest; renegotiate carrier SLAs
Fix high-delay African regions — Engage regional 3PL partners with last-mile capability; consider regional warehousing hubs
Inventory overhaul in Health & Beauty — Dedicated pick zones, faster restocking cycles, parallelise compliance checks
Identify seasonal surge patterns — Pre-negotiate carrier burst capacity and warehouse staffing based on time-series findings
Adjust order cut-off times — Address day-of-week and hour-of-day delay spikes identified in the time analysis
Deploy the ML model as a live scoring API — Flag high-risk orders at point of creation for priority warehouse handling



👤 Author

Rushikesh Temghare — MSc Data Science & Artificial Intelligence
