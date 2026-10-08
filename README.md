# HealthConnect Clinic — Appointment No-Show & Data Quality Analysis

## Project Overview

This project analyses appointment data from **HealthConnect Clinic**, a fictional and anonymised healthcare dataset containing **5,000 appointment records and 18 variables**.

The project places a strong focus on **data quality assessment and cleaning before analysis**. The dataset was systematically reviewed for completeness, consistency, validity, duplicate records, incorrect values and potential outliers.

After establishing that the data was suitable for analysis, the cleaned dataset was used to investigate patterns associated with appointment no-shows and identify areas where appointment management could be improved.

---

## Business Question

**What factors are associated with appointment no-shows, and where can appointment management be improved?**

---

# Data Quality Assessment and Cleaning

Data quality was assessed before conducting the analysis to ensure the dataset was **complete, consistent, valid and suitable for reporting**.

The cleaning process included:

* Assessing missing values across all columns.
* Checking for duplicate records.
* Checking for duplicate appointment IDs.
* Reviewing data types and converting date fields where required.
* Validating booking and appointment dates.
* Checking booking lead time against the difference between booking and appointment dates.
* Reviewing categorical values for consistency.
* Validating age groups against recorded ages.
* Checking numerical fields for plausible ranges.
* Identifying and reviewing potential outliers using the IQR method.
* Reviewing relationships between related fields for inconsistencies.

### Missing-Value Assessment

Three fields contained missing values:

| Field                   | Missing Records | Treatment                   |
| ----------------------- | --------------: | --------------------------- |
| `reminder_channel`      |           1,366 | Recorded as **No Reminder** |
| `distance_to_clinic_km` |              90 | Records removed             |
| `waiting_time_minutes`  |              60 | Records removed             |

The **1,366 missing reminder-channel values** were investigated rather than automatically removed. They corresponded to appointments where **no reminder had been sent**, so the missing values were recorded as **No Reminder**.

The 90 records missing distance information and 60 records missing waiting-time information were removed because these fields were used in the analysis and the missing values could not be reliably determined.

### Duplicate Checks

The dataset was checked for duplicate records and duplicate appointment IDs.

No full duplicate records were identified, and there were no duplicate appointment IDs.

Repeated `patient_id` values were retained because a patient can legitimately have multiple appointments.

### Date Validation

The booking and appointment date fields were converted to the appropriate date format and checked for consistency.

The analysis confirmed that:

* Booking dates occurred before appointment dates.
* Booking lead time was consistent with the difference between booking and appointment dates.
* No booking lead-time discrepancies were identified.

### Categorical Validation

Categorical fields were reviewed for inconsistent or unexpected values.

The `age_group` field was also checked against the recorded `age` values to ensure that patients were assigned to the appropriate age group.

### Numerical Validation

Numerical fields were reviewed for plausible values and unexpected entries.

The following ranges were checked:

* Age: **18–80 years**
* Booking lead time: **0–60 days**
* Previous appointments: **0–11**
* Previous no-shows: **0–5**
* Distance to clinic: **0.5–45 km**
* Waiting time: **2–68 minutes**

No clearly invalid numerical values were identified.

### Outlier Assessment

Potential outliers were reviewed using the **IQR method**.

Distance to the clinic had **147 values above the calculated upper IQR boundary of 25.80 km**.

These records were not automatically removed because the distances were unusual but still considered **plausible values rather than confirmed data-entry errors**.

Age did not contain IQR outliers.

### Final Dataset

After the data quality assessment and cleaning process:

**Original dataset:** 5,000 records × 18 variables
**Final dataset:** 4,850 records × 18 variables

The cleaned dataset was then used for the exploratory and deeper analysis.

---

# Exploratory Analysis

The cleaned dataset was analysed to identify patterns associated with appointment no-shows.

The main findings were:

* **48.23%** of appointments were no-shows.
* Appointments booked **0–7 days in advance** had a no-show rate of **27.14%**.
* Appointments booked **31–60 days in advance** had a no-show rate of **60.31%**.
* Previous no-show history was associated with higher no-show rates.
* Longer travel distances also showed higher no-show rates.
* Reminder activity showed a smaller difference in no-show rates compared with booking lead time.

---

# Main Finding — Booking Lead Time

Booking lead time showed the clearest difference in no-show rates among the factors examined.

Appointments booked **31–60 days in advance** had a no-show rate of **60.31%**, compared with **27.14%** for appointments booked **0–7 days in advance**.

This represents a **33.17 percentage-point difference**, making booking lead time the main factor selected for deeper analysis.

---

# Deeper Analysis

The analysis was narrowed to appointments booked **31–60 days in advance**, as this group had the highest no-show rate.

Within this group, previous no-show history showed a further pattern.

Patients with **two previous no-shows** had a **70.33% no-show rate across 182 appointments**.

The outcomes within this group were:

* **70.33% No-Show**
* **25.27% Attended**
* **4.40% Cancelled**

Further analysis of distance and reminder activity within this group did not show a consistent or substantial additional pattern. Therefore, previous no-show history remained the clearest characteristic within the selected high-risk group.

---

# Cause, Effect, Business Impact and Recommendations

## Cause

A possible reason for the higher no-show rate among appointments booked further in advance is that patients may **forget their appointment or have their plans change** before the appointment date.

Previous no-show history may indicate ongoing attendance difficulties, while longer travel distances may create additional access or transport challenges.

Further information, such as reminder timing, confirmation responses and reasons for missed appointments, could help the clinic better understand these patterns.

## Effect

Of the **2,353 appointments** booked 31–60 days in advance, **1,419 were no-shows**, representing **60.31%**.

Patients with previous no-shows also had higher subsequent no-show rates.

## Business Impact

High levels of non-attendance can reduce the number of appointments the clinic is able to effectively use and make scheduling less predictable.

Missed appointments may also create additional administrative work and reduce the availability of appointment times for other patients.

## Recommendations

Based on the analysis, HealthConnect could consider:

1. **Targeted follow-up:** Review appointments booked 31–60 days in advance and consider confirmation or reminder follow-ups closer to the appointment date.

2. **Previous no-show history:** Consider additional follow-up for patients with previous no-shows, particularly those with two or more previous no-shows.

3. **Distance and access:** Review whether patients travelling longer distances experience access or transport barriers.

4. **Reminder process:** Continue using appointment reminders while reviewing reminder timing and confirmation responses.

5. **Further data collection:** Record reasons for missed appointments and other relevant information to support further investigation of attendance patterns.

---

# SQL Analysis

SQL was used to further explore appointment outcomes and validate key findings from the Python analysis.

The SQL analysis included:

* Overall no-show rate.
* No-show count by appointment type.
* Appointment outcome distribution.

The SQL results were consistent with the Python analysis.

---

# Tools

* **Python**
* **Pandas**
* **Matplotlib**
* **Seaborn**
* **SQL**
* **Jupyter Notebook**

---

# Project Workflow

**Data Quality Assessment → Data Cleaning → Data Validation → Exploratory Analysis → Identify Patterns → Deeper Analysis → Business Impact → Recommendations**

---

# Project Structure

``` 
HealthConnect-Clinic/
│
├── data/
│   └── HealthConnect_Cleaned.csv
│
├── HealthConnect_Appointment_No_Show_Analysis.ipynb
│
├
│
└── README.md
```

---

# GitHub Repository

The complete project, including the analysis notebook, cleaned dataset and supporting SQL analysis, is available here:

**https://github.com/Hajarat-A/HealthConnect-Clinic**
