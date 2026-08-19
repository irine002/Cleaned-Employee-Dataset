# Cleaned Company Employee Dataset

## 📌 Project Overview

This project focuses on cleaning and preprocessing a messy company employee dataset using **Python and Pandas**.

The dataset contains employee information with issues such as missing values, duplicate records, inconsistent categorical entries, and incorrect data types. The goal is to clean the dataset and produce a reliable dataset suitable for further analysis.

## 📂 Dataset

The dataset contains **12 columns** related to company employees, including:

* Employee ID
* Employee Name
* Department
* Job Title
* Age
* Gender
* Annual Salary
* Experience Years
* Joining Date
* City
* Performance Score
* Work Mode

## 🛠️ Technologies Used

* Python
* Pandas
* Google Colab
* CSV

## 🔍 Data Inspection

The dataset was loaded using Pandas and inspected using:

* `head()`
* `info()`
* `describe()`
* `isnull()`
* `duplicated()`
* `value_counts()`

### Initial Dataset Condition

| Metric         | Before Cleaning |
| -------------- | --------------: |
| Rows           |             157 |
| Columns        |              12 |
| Missing Values |              32 |
| Duplicate Rows |               7 |

## 🧹 Data Cleaning Steps

### 1. Removed Duplicate Records

Duplicate employee records were identified using `duplicated()` and removed using:

```python
df.drop_duplicates()
```

This reduced the dataset from **157 rows to 150 rows**.

### 2. Handled Missing Numerical Values

Missing values in numerical columns such as:

* Age
* Annual Salary
* Experience Years
* Performance Score

were replaced using **median imputation**.

```python
df[column] = df[column].fillna(df[column].median())
```

Median was selected because it is less affected by extreme values.

### 3. Handled Missing Categorical Values

Missing values in categorical columns such as:

* Department
* Gender
* City
* Work Mode

were replaced using the **mode**.

```python
df[column] = df[column].fillna(df[column].mode()[0])
```

### 4. Standardized Inconsistent Entries

Categorical values were cleaned by removing unnecessary spaces and standardizing capitalization.

```python
df["Department"] = df["Department"].str.strip().str.title()
```

The same process was applied to Gender, City, and Work Mode.

### 5. Corrected Data Types

The `Joining_Date` column was converted to datetime:

```python
df["Joining_Date"] = pd.to_datetime(
    df["Joining_Date"],
    errors="coerce"
)
```

Numerical columns were also converted to appropriate numeric data types using `pd.to_numeric()`.

### 6. Handled Essential Fields

`Employee_ID`, `Employee_Name`, and `Job_Title` were treated as essential fields. Rows with missing values in these columns were removed using `dropna()` if necessary.

### 7. Forward Filling

Forward filling was **not used** because each employee record is independent. Copying the previous employee's information could result in incorrect employee data.

## ✅ Final Dataset Condition

| Metric         | Before Cleaning | After Cleaning |
| -------------- | --------------: | -------------: |
| Rows           |             157 |            150 |
| Columns        |              12 |             12 |
| Missing Values |              32 |              0 |
| Duplicate Rows |               7 |              0 |

The final dataset contains **150 clean employee records and 12 columns**.

## 📊 Verification

After cleaning, the dataset was verified using:

```python
df.isnull().sum()
```

```python
df.duplicated().sum()
```

```python
df.dtypes
```

The final verification confirmed:

* No missing values
* No duplicate records
* Appropriate data types
* Standardized categorical values

## 📁 Output

The cleaned dataset was exported as:

```text
Cleaned_Company_Employee_Dataset.csv
```

## 🎯 Learning Outcomes

Through this assignment, the following Pandas techniques were practiced:

* Loading CSV files
* Inspecting DataFrames
* Detecting missing values
* Detecting duplicate records
* Using `drop_duplicates()`
* Using `dropna()`
* Using `fillna()`
* Mean/median/mode imputation
* Data type conversion
* String cleaning
* DateTime conversion
* Dataset validation
* Exporting DataFrames to CSV

## 👩‍💻 Author

**Irine Vincent**

B.Tech Artificial Intelligence and Data Science
