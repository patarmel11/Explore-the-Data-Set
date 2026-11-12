# Explore the Data Set

A hands-on lab from the IBM Data Analyst Capstone Project (Module 1). It loads the 2020 developer survey dataset with pandas and does a first exploration: size, column data types, and a few quick statistics.

## Objectives

- Load the dataset used throughout the capstone project
- Explore its structure
- Get familiar with the data types of each column

## Dataset

[survey_results_public_2020.csv](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DA0321EN-SkillsNetwork/labs/Capstone_edX/Module%201/survey_results_public_2020.csv): public results of a worldwide 2020 developer survey. It covers demographics, pay, technologies used, and work habits.

## Tools & Libraries

- Python 3
- [pandas](https://pypi.org/project/pandas/)
- Jupyter Notebook

## Steps

```python
import pandas as pd

df = pd.read_csv(dataset_url)                      # load the data
df.head()                                          # preview the first 5 rows
print("Number of rows:", df.shape[0])              # row count
print("Number of columns:", df.shape[1])           # column count
df.dtypes                                          # data type of each column
print("Mean age:", df["Age"].mean())               # average participant age
print("Unique countries:", df["Country"].nunique()) # distinct countries
```

## Key Findings

| Metric | Value |
|---|---|
| Rows (respondents) | **64,461** |
| Columns | **61** |
| Mean age of participants | **30.83** |
| Unique countries | **183** |

### Data types

| Type | Columns |
|---|---|
| `int64` | `Respondent` |
| `float64` | `Age`, `CompTotal`, `ConvertedComp`, `WorkWeekHrs` |
| `object` | The other 56 columns (text and multiple-choice answers) |

### Observations

- **Most columns are text (`object`).** Many hold several choices separated by semicolons (e.g. `ASP.NET;ASP.NET Core`), which need splitting before analysis.
- **`Age1stCode`, `YearsCode` and `YearsCodePro` look numeric but are stored as text.** They contain answers like "Younger than 5 years" and "Less than 1 year", so they need cleaning before numeric analysis.
- **Many values are missing.** For example, `Age` and `ConvertedComp` are `NaN` for many respondents, so the mean age covers only the people who answered.

## How to Run

```bash
pip install pandas jupyter
jupyter notebook M1ExploreDataSet-lab.ipynb
```

## Files

- `M1ExploreDataSet-lab.ipynb`: notebook with the exploration code and outputs
