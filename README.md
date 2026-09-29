# HealthConnect Clinic — Data Quality Assessment & Appointment No-Show Analysis

## Project Overview

This project assesses and analyses appointment data from **HealthConnect Clinic**, a fictional and anonymised healthcare dataset containing **5,000 appointment records and 18 variables**.

The project combines **data quality assessment, data cleaning, validation, exploratory analysis and business interpretation** to investigate factors associated with appointment no-shows.

The dataset was assessed for completeness, consistency, validity and potential data-quality issues before being used for analysis. Cleaning and validation decisions were documented to support a reliable and reproducible analytical dataset.

---

## Business Question

**What factors are associated with appointment no-shows at HealthConnect Clinic, and where can appointment management be improved?**

---

## Dataset

* **Original records:** 5,000
* **Final cleaned records:** 4,850
* **Variables:** 18

Key variables include:

* Age and gender
* Appointment type
* Appointment day and time
* Booking lead time
* Previous appointments
* Previous no-shows
* Distance to clinic
* Waiting time
* Reminder activity
* Appointment outcome

---

## Data Quality Assessment

Before analysing appointment outcomes, the dataset was reviewed across several data-quality areas:

* **Completeness** — identification and assessment of missing values
* **Uniqueness** — duplicate record and appointment ID checks
* **Validity** — data types, numerical ranges and date values
* **Consistency** — categorical values and related fields
* **Cross-field validation** — checking whether related fields agreed with each other
* **Derived-field validation** — validating calculated or grouped fields against their source data
* **Outlier assessment** — identifying unusual numerical observations and reviewing whether they represented potential errors or plausible values

The objective was not simply to remove unusual records, but to assess whether each issue represented a genuine data-quality problem and document the reasoning behind the cleaning decision.

---

## Data Quality Issues Identified

The initial dataset contained missing values in three areas:

| Variable           | Missing Records |
| ------------------ | --------------: |
| Reminder channel   |           1,366 |
| Distance to clinic |              90 |
| Waiting time       |              60 |

### Reminder Channel

The 1,366 missing reminder-channel values were investigated against the reminder-status field.

The records corresponded to appointments where **no reminder had been sent**. Rather than treating these values as unknown, they were standardised as **No Reminder**, providing a meaningful category for analysis.

### Distance and Waiting Time

There were:

* **90 records** with missing distance-to-clinic values
* **60 records** with missing waiting-time values

These **150 records were removed** because both variables were used in the analysis and their missing values could not be reliably determined from the available dataset.

After cleaning, the final dataset contained **4,850 appointment records**.

---

## Data Validation

Several validation checks were performed after cleaning to assess whether important fields were internally consistent.

### Date Validation

Booking dates and appointment dates were converted to appropriate datetime formats.

The analysis confirmed that there were **no appointments with an appointment date earlier than the booking date**.

The existing `booking_lead_days` field was also compared with the difference between `appointment_date` and `booking_date`. The validation identified **no discrepancies**.

### Age Group Validation

The `age_group` field was compared against the recorded patient age.

The validation identified **no mismatches**, confirming that the assigned age groups were consistent with the underlying age values.

### Categorical Validation

Categorical fields were reviewed for unexpected or inconsistent values, including:

* Gender
* Age group
* Appointment type
* Appointment day
* Reminder status
* Reminder channel
* Appointment outcome

No unexpected categorical values were identified during this validation.

### Duplicate Checks

The dataset was reviewed for duplicate records and duplicate appointment identifiers.

### Numerical and Outlier Review

Numerical variables were reviewed using descriptive statistics and IQR-based outlier checks.

For example, **147 distance observations** were identified above the calculated upper IQR boundary.

These observations were reviewed rather than automatically removed. The recorded distances remained within a plausible range, so they were retained as unusual but potentially valid observations.

This demonstrates the distinction between **an unusual value and a confirmed data error**.

---

## Exploratory Data Analysis

After the data quality and validation stage, the final dataset of **4,850 records** was analysed to identify patterns in appointment outcomes.

### Key Findings

* **No-Show** was the most common appointment outcome at **48.23%**.
* **Booking lead time** showed the largest observed difference in no-show rates.
* No-show rates increased from **27.14%** for appointments booked 0–7 days ahead to **60.31%** for appointments booked 31–60 days ahead.
* **Distance to the clinic** showed an overall increasing pattern in no-show rates across longer distance bands.
* Patients with a greater history of **previous no-shows** generally had higher no-show rates.
* Reminder activity showed a smaller difference in no-show rates compared with booking lead time.

---

## Deeper Analysis

Booking lead time was selected for deeper analysis because it showed the largest and most consistent difference in the initial comparisons.

Appointments booked **31–60 days in advance** had a **60.31% no-show rate**.

Within this group, previous no-show history was examined further.

Patients with **two previous no-shows** had a **70.33% no-show rate across 182 appointments**.

This subgroup was examined to determine whether previous attendance history provided additional context within the long-lead-time group.

---

## Business Impact

Of the **2,353 appointments** booked 31–60 days in advance, **1,419 were recorded as no-shows**.

If a similar pattern continues, unused appointment capacity may contribute to scheduling inefficiencies and reduce the number of appointments that can be effectively delivered.

The findings identify an area for further investigation and targeted appointment-management strategies. They describe **observed associations rather than proven causal relationships**.

---

## Recommendations

HealthConnect Clinic could consider:

* Reviewing appointments booked further in advance.
* Providing targeted follow-up for patients with previous no-show history.
* Reviewing reminder timing and confirmation processes for longer-lead appointments.
* Considering travel distance when managing appointment attendance.
* Continuing appointment reminders as part of appointment management.

Further operational data, such as reminder timing, confirmation responses and recorded reasons for non-attendance, could be used to investigate the possible causes of the observed patterns.

---

## Tools

* Python
* Pandas
* Matplotlib
* Seaborn
* SQL
* Jupyter Notebook

---

## Project Workflow

**Data Quality Assessment → Data Cleaning → Data Validation → Exploratory Data Analysis → Pattern Identification → Deeper Analysis → Business Impact → Recommendations**

---

## Project Structure

```text
HealthConnect-Data-Quality-Appointment-Analysis/
├── data/
│   └── HealthConnect_Cleaned.csv
├── HealthConnect_Data_Quality_Appointment_Analysis.ipynb
└── README.md
```

---

## Data Quality Skills Demonstrated

This project demonstrates practical experience with:

* Missing-data assessment
* Data completeness checks
* Duplicate and uniqueness checks
* Data-type validation
* Date validation
* Cross-field validation
* Derived-field validation
* Categorical consistency checks
* Numerical range assessment
* IQR-based outlier identification
* Data-cleaning decision documentation
* Validation before analysis
* Reproducible analysis using Python and SQL
* Translating validated data into business insights

---

## Important Note

This project uses a fictional/anonymised dataset for learning and portfolio purposes.

The findings describe **observed associations within the dataset** and should not be interpreted as causal or clinical conclusions.
