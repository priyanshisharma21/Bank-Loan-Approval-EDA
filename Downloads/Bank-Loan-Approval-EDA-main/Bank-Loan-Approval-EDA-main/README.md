# Bank Loan Approval: Data Exploration

An exploratory data analysis (EDA) of 614 bank loan applications, with an interactive dashboard.
The project asks one question: **which applicant details are actually associated with a loan being approved?**

**Live dashboard:** https://bank-loan-approval-eda-a7shj9ji7j4yufqer3min7.streamlit.app/

> EDA shows associations, not causes. Nothing here is a lending decision tool.

---

## Key findings

| Finding | Result |
|---|---|
| Overall approval rate | **68.7%** (422 approved, 192 rejected) |
| Credit history = 1 (good) | **79.0%** approved |
| Credit history = 0 (poor) | **7.9%** approved |
| Correlation of credit history with approval | **0.54**, the only strong link |
| Property area | Semiurban 76.8%, Urban 65.8%, Rural 61.5% |
| Education | Graduate 70.8%, Not Graduate 61.2% |
| Married | Yes 71.8%, No 62.9% |
| Applicant income, loan amount, loan term | Correlation close to 0 with approval |

**In short:** credit history separates approved from rejected applications far more clearly than income or loan amount does.

## Project objectives

- Understand the structure and quality of the loan application data
- Find missing values, duplicates and outliers, and handle them
- Compare approved and rejected applications across income, credit history, loan amount and customer groups
- Present the patterns as clear charts and an interactive dashboard
- Lay a foundation for a future prediction model

## Dataset

Loan Prediction Problem dataset (`train.csv`), 614 rows and 13 columns.

| Column | Description |
|---|---|
| Loan_ID | Unique application ID |
| Gender, Married, Dependents, Education, Self_Employed | Applicant details |
| ApplicantIncome, CoapplicantIncome | Monthly incomes |
| LoanAmount, Loan_Amount_Term | Requested amount and repayment term |
| Credit_History | 1 if the credit history meets guidelines, 0 if not |
| Property_Area | Urban, Semiurban or Rural |
| Loan_Status | Y (approved) or N (rejected) |

## Method

1. **Understand the data:** shape, types, summary statistics, missing values, duplicates.
2. **Clean the data:**
   - Seven columns had missing values (Credit_History 50, Self_Employed 32, LoanAmount 22, Dependents 15, Loan_Amount_Term 14, Gender 13, Married 3).
   - Categorical columns were filled with the most common value, and `LoanAmount` with the median because it is skewed.
   - Added `TotalIncome` (applicant plus co-applicant income).
3. **Explore:** approval rate by group, income and loan amount distributions, outliers, correlation.
4. **Report:** findings, limitations and next steps.

## Tools

Python, Pandas, NumPy, Matplotlib, Seaborn, Jupyter Notebook, Streamlit.

## Project structure

```
bank-loan-eda/
├── app.py                         # Dashboard entry point (navigation and filters)
├── utils/
│   ├── data.py                    # Loading and cleaning
│   └── style.py                   # Colors, CSS and chart styling
├── sections/
│   ├── overview.py                # Headline finding, summary, loan status
│   ├── credit_history.py          # Credit history analysis
│   ├── income_loan.py             # Income and loan amount
│   ├── demographics.py            # Property area, education, married, ...
│   └── correlation.py             # Correlation charts
├── .streamlit/config.toml         # Streamlit theme
├── Bank_Loan_Approval_EDA.ipynb   # Full analysis notebook
├── train.csv                      # Dataset
└── requirements.txt
```

## Run it locally

```bash
git clone https://github.com/<username>/<repo>.git
cd <repo>
pip install -r requirements.txt
python -m streamlit run app.py
```

Then open `http://localhost:8501`.

To explore the analysis step by step, open `Bank_Loan_Approval_EDA.ipynb` in Jupyter or VS Code and choose **Run All**.

## Dashboard pages

- **Overview:** the headline finding, key numbers, loan status and missing values
- **Credit history:** approval rate and counts for good and poor credit history
- **Income and loan amount:** distributions and comparisons by outcome
- **Customer groups:** approval rate by property area, education, marital status and more
- **Correlation:** which numeric columns move together

The sidebar filters (property area and education) apply to every page.

## Limitations

- EDA shows association only, so no finding here proves a cause.
- The data comes from one lender and has only 614 rows, so patterns may not hold elsewhere.
- About 50 missing credit history values were filled with the most common value, which may slightly overstate the approval rate for good credit.
- Differences by gender or marital status are not a reason to use those attributes in lending decisions. They raise fairness, privacy and regulatory concerns.

## Next steps

- Check whether gaps by gender, marital status and education remain once credit history is accounted for
- Study applications with missing credit history separately
- Build a classification model (for example Logistic Regression) and test it with a train/test split


## Resume summary

Performed exploratory data analysis on 614 bank loan applications using Python, Pandas, NumPy, Matplotlib and Seaborn. Cleaned missing values, analysed income, loan amount, credit history and customer groups, and found that credit history is the strongest factor associated with approval (79.0% approved with good credit history against 7.9% without). Built and deployed an interactive Streamlit dashboard as a team project.
