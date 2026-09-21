# 💳 Credit Card Fraud Detection Analysis

Exploratory Data Analysis (EDA) of credit card transactions in India using **Python, Pandas and Matplotlib**. The project explores how fraud is spread across fraud types, risk levels, states, banks, merchants, card types and time, to understand where and how fraud happens.

---

## 📌 Project Overview

| Item | Details |
|------|---------|
| **Goal** | Understand fraud patterns in credit card transactions |
| **Type** | Exploratory Data Analysis (no ML model) |
| **Dataset** | `credit.csv` (1,000 transactions, 14 columns) |
| **Period** | 16 Dec 2023 – 15 Dec 2024 |
| **Currency** | INR (₹) |
| **Tools** | Python, Pandas, Matplotlib, Jupyter Notebook |

## 📂 Dataset Description

| Column | Description |
|--------|-------------|
| `Transaction ID` | Unique transaction identifier |
| `Customer Name` | Name of the customer |
| `Merchant Name` | Merchant where the transaction happened (Zomato, Flipkart, Uber, etc.) |
| `Transaction Date` | Date of transaction |
| `Transaction Amount (INR)` | Transaction value in rupees |
| `Fraud Risk` | Risk label: Low / Medium / High / Critical |
| `Fraud Type` | Card Not Present, Card Skimming, Identity Theft, Account Takeover, Phishing |
| `State` | State of the customer |
| `Card Type` | Visa, Mastercard, Amex, Rupay |
| `Bank` | Issuing bank |
| `IsFraud` | Target flag: `1` = fraud, `0` = genuine |
| `Fraud Score` | Score from 10 to 95 |
| `Transaction Category` | E-commerce, Electronics, Food Delivery, Transportation, Apparel, Groceries |
| `Merchant Location` | City of the merchant |

## 🔍 Analysis Steps

1. **Data loading**: read `credit.csv` with Pandas
2. **Data inspection**: `head()`, `shape`, `columns`, `dtypes`, `describe()`
3. **Data quality check**: null values and duplicate records
4. **Data preparation**: converted `Transaction Date` to datetime
5. **Fraud metrics**: total fraud count, fraud rate, fraud by risk level, fraud by type
6. **Amount analysis**: total and average fraud amount per fraud type
7. **Visualisation**: 12 charts (bar charts, line chart, scatter plot)

## 📊 Key Findings

### Overall numbers
- **Total transactions:** 1,000
- **Fraud transactions:** 286
- **Fraud rate:** 28.6%
- **Total fraud amount:** ₹33,06,813 (average ≈ ₹11,562 per fraud transaction)
- **Data quality:** no missing values and no duplicate rows

### Fraud type
| Fraud Type | Fraud Count | Share | Total Amount (₹) | Avg Amount (₹) |
|------------|:-----------:|:-----:|-----------------:|---------------:|
| Card Not Present | 72 | 25.2% | 8,79,713 | 12,218 |
| Identity Theft | 64 | 22.4% | 8,04,353 | 12,568 |
| Card Skimming | 54 | 18.9% | 6,27,465 | 11,620 |
| Phishing | 50 | 17.5% | 4,85,658 | 9,713 |
| Account Takeover | 46 | 16.1% | 5,09,624 | 11,079 |

- **Card Not Present** fraud is the most common and has the highest total loss.
- **Identity Theft** has the highest average ticket size.
- **Phishing** has the lowest average amount.

### Fraud risk label vs actual fraud
| Fraud Risk | Transactions | Actual Fraud | Fraud Rate |
|------------|:------------:|:------------:|:----------:|
| Low | 400 | 113 | 28.25% |
| Medium | 297 | 83 | 27.95% |
| High | 196 | 62 | 31.63% |
| Critical | 107 | 28 | 26.17% |

The `Fraud Risk` label does **not** separate fraud from genuine transactions: "Critical" has the *lowest* fraud rate. The `Fraud Score` vs amount scatter plot also shows no visible pattern.

### Where fraud is concentrated (from charts)
- **States:** Maharashtra (~36), Karnataka (~34), Rajasthan (~34), West Bengal (~33)
- **Banks:** Andhra Bank (~41), ICICI Bank (~36), HDFC Bank (~33)
- **Merchants:** Zomato (~37), Big Bazaar (~35), Myntra (~31)
- **Categories:** E-commerce (54) and Electronics (54), then Food Delivery (48)
- **Card type:** Visa (~88) leads, followed by Amex (~71), Mastercard (~66) and Rupay (~61)
- **Monthly trend:** fraud rises from Dec 2023 (~15), peaks in **Aug 2024 (~29)**, then declines to ~19 by Dec 2024

> Chart values marked with `~` are read from the plots.

## ⚠️ Limitations

- The dataset is small (1,000 rows) and looks **synthetic**: a 28.6% fraud rate is far higher than real-world card fraud, which is usually well below 1%.
- Dec 2023 and Dec 2024 are **partial months** (data starts 16 Dec and ends 15 Dec), so their counts are not directly comparable to full months.
- Counts are absolute, not rates, so top states, banks or merchants may simply have more transactions overall.
- This is descriptive analysis only. No predictive model has been built.

## 🚀 How to Run

```bash
# 1. Install dependencies
pip install pandas matplotlib jupyter

# 2. Keep credit.csv in the same folder as the notebook

# 3. Launch the notebook
jupyter notebook credit_card_analysis.ipynb
```

## 📁 Project Structure

```
├── credit_card_analysis.ipynb   # Main analysis notebook
├── credit.csv                   # Dataset
└── README.md                    # Project documentation
```

## 🔧 Small Fixes Needed in the Notebook

- `df.info` should be `df.info()` (with brackets) to print the summary.
- `Plt.xlabel("Bank")` in the Bank-wise chart should be `plt.xlabel("Bank")` (lowercase `p`); it currently raises a `NameError`.

## 🔮 Future Improvements

- Calculate **fraud rate per state / bank / merchant / card type** instead of raw counts
- Add a **correlation heatmap** and analysis by transaction amount bands
- Build a classification model (Logistic Regression, Random Forest, XGBoost) with precision, recall and ROC-AUC
- Handle class imbalance (SMOTE / class weights) if real data is used
- Build an interactive dashboard (Power BI / Streamlit)

## 👤 Author

**Your Name**
GitHub: [your-username](https://github.com/your-username) · LinkedIn: [your-profile](https://linkedin.com/in/your-profile)
