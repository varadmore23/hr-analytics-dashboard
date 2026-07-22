# HR Analytics Dashboard 📊

An end-to-end Data Analytics project analyzing employee attrition patterns using Python for EDA and Microsoft Power BI for interactive dashboard development.

---

## 📌 Problem Statement

Employee attrition is a critical challenge for organizations, leading to high recruitment costs and loss of institutional knowledge. This project analyzes the IBM HR Attrition dataset to identify key drivers of employee churn and presents actionable insights through an interactive Power BI dashboard to support data-driven HR decision-making.

---

## 📁 Project Structure

```
hr-analytics-dashboard/
├── data/
│   ├── WA_Fn-UseC_-HR-Employee-Attrition.csv   # Raw dataset
│   └── hr_analytics_clean.csv                   # Cleaned & enriched dataset
├── notebooks/
│   └── eda_analysis.ipynb                       # Full EDA notebook (Google Colab)
├── visuals/
│   ├── attrition_dept.png                       # Attrition by Department
│   ├── income_attrition.png                     # Monthly Income vs Attrition
│   ├── age_attrition.png                        # Attrition Rate by Age Group
│   └── heatmap.png                              # Feature Correlation Heatmap
├── powerbi/
│   └── HR_Dashboard.pbix                        # Power BI Dashboard file
└── README.md
```

---

## 🛠️ Tools & Technologies

| Category | Tools |
|---|---|
| Language | Python |
| Libraries | pandas, NumPy, Matplotlib, Seaborn |
| BI Tool | Microsoft Power BI |
| DAX | Custom KPI measures |
| Environment | Google Colab |
| Version Control | Git, GitHub |

---

## 📊 Dataset

- **Source:** [IBM HR Analytics Employee Attrition & Performance — Kaggle](https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset)
- **Size:** 1,470 rows × 35 columns
- **Key Features:** Age, Attrition, Department, MonthlyIncome, JobRole, YearsAtCompany, JobSatisfaction, OverTime, SalaryBand

---

## 🔍 EDA Highlights

- Dropped columns with zero variance: `EmployeeCount`, `Over18`, `StandardHours`
- Engineered new features: `Attrition_Flag`, `AgeGroup`, `SalaryBand`
- Analyzed attrition across departments, age groups, salary bands, and job roles
- Generated correlation heatmap to identify relationships between numeric features

---

## 📈 Key Findings

- **Overall attrition rate: 16.12%**
- **Sales department** has the highest attrition rate at ~20.6%
- Employees earning **below $3,000/month** have nearly **3x higher attrition** than higher earners
- Employees in the **18–25 age group** show the highest churn rate
- **Overtime workers** are significantly more likely to leave the organization
- Employees with **low job satisfaction scores** show a strong correlation with attrition

---

## 📋 Power BI Dashboard

The dashboard consists of 3 pages with a drill-through detail page:

**Page 1 — Overview**
- KPI Cards: Total Employees, Attrition Rate %, Active Employees, Avg Age
- Donut chart: Attrition distribution
- Bar chart: Attrition count by Department
- Slicers: Department, Gender

**Page 2 — Demographics**
- Attrition by Age Group
- Attrition by Salary Band
- Attrition by Job Role
- Slicer: Department

**Page 3 — Workforce Performance**
- Matrix: Department vs Avg Income, Avg Tenure, Avg Job Satisfaction
- Line chart: Years at Company vs Attrition Rate
- Slicers: Job Level, Education Field

**Page 4 — Employee Drill-Through**
- Detailed table view per department showing EmployeeNumber, JobRole, MonthlyIncome, Attrition, YearsAtCompany

---

## 📐 DAX Measures

```DAX
Attrition Rate =
DIVIDE(
    CALCULATE(COUNT('hr_analytics_clean'[Attrition]),
    'hr_analytics_clean'[Attrition] = "Yes"),
    COUNT('hr_analytics_clean'[Attrition]),
    0
) * 100

Active Employees =
CALCULATE(COUNT('hr_analytics_clean'[EmployeeNumber]),
'hr_analytics_clean'[Attrition] = "No")

Avg Monthly Income = AVERAGE('hr_analytics_clean'[MonthlyIncome])

Avg Tenure = AVERAGE('hr_analytics_clean'[YearsAtCompany])
```

---

## 🚀 How to Run

1. Clone the repository
```bash
git clone https://github.com/varadmore23/hr-analytics-dashboard.git
cd hr-analytics-dashboard
```

2. Open `notebooks/eda_analysis.ipynb` in Google Colab or Jupyter Notebook

3. Run all cells sequentially — the notebook will generate cleaned data and all visuals

4. Open `powerbi/HR_Dashboard.pbix` in Microsoft Power BI Desktop

---

## 👤 Author

**Varad More**
- 📧 varad.more23@spit.ac.in
- 🔗 [LinkedIn](https://www.linkedin.com/in/varad-more-450777398/)
- 🐙 [GitHub](https://github.com/varadmore23)
