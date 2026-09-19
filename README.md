# HealthConnect Clinic — Appointment No-Show Analysis

## Project Overview

This project analyses appointment data from **HealthConnect Clinic**, a fictional and anonymised healthcare dataset containing **5,000 appointment records and 18 variables**.

The analysis focuses on identifying patterns associated with **appointment no-shows** and understanding which patient, appointment, booking and clinic-related factors may be associated with missed appointments.

The dataset was cleaned and analysed using Python to identify key patterns, followed by a deeper analysis of the strongest observed finding.

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

## Data Cleaning

The dataset was reviewed for:

* Missing values
* Duplicate records
* Incorrect data types
* Invalid dates
* Inconsistent categorical values
* Implausible numerical values
* Potential outliers

Missing reminder channels were investigated and found to correspond to appointments where no reminder was sent. These were therefore recorded as **No Reminder**.

A small number of records had missing values for **distance to the clinic (90 records)** and **waiting time (60 records)**. These records were removed because these variables were used in the analysis and the missing values could not be reliably determined from the available data.

After cleaning, the final dataset contained **4,850 appointment records**.

---

## Exploratory Data Analysis

The analysis examined appointment outcomes across different patient and appointment characteristics.

### Key Findings

* **No-Show** was the most common outcome at **48.23%**.
* **Booking lead time** showed the largest difference in no-show rates.
* No-show rates increased from **27.14%** for appointments booked 0–7 days ahead to **60.31%** for appointments booked 31–60 days ahead.
* **Distance to the clinic** also showed an increasing pattern in no-show rates.
* Patients with a greater history of **previous no-shows** generally had higher no-show rates.
* Reminder activity showed a smaller difference in no-show rates compared with booking lead time.

---

## Deeper Analysis

Booking lead time was selected for deeper analysis because it showed the largest and most consistent difference in no-show rates.

The analysis focused on appointments booked **31–60 days in advance**, which had a **60.31% no-show rate**.

Within this group, previous no-show history was examined further.

Patients with **two previous no-shows** had a **70.33% no-show rate across 182 appointments**.

This subgroup was selected as the main deeper finding.

---

## Business Impact

The findings suggest that appointments booked further in advance, particularly those involving patients with previous no-show history, may require additional appointment management attention.

Missed appointments can leave appointment capacity unused and may contribute to scheduling inefficiencies.

---

## Recommended Actions

HealthConnect Clinic could consider:

* Reviewing appointments booked further in advance.
* Providing targeted follow-up for patients with previous no-shows.
* Considering travel distance when managing appointment attendance.
* Continuing appointment reminders as part of appointment management.

---

## Tools

* Python
* Pandas
* Matplotlib
* Seaborn
* Jupyter Notebook

---

## Project Workflow

**Data Cleaning → Exploratory Data Analysis → Identify Patterns → Deeper Analysis → Business Impact → Recommendations**

---

## Project Structure

```text
HealthConnect-Appointment-No-Show-Analysis/
├── data/
│   └── HealthConnect_Cleaned.csv
├── HealthConnect_Appointment_No_Show_Analysis.ipynb
└── README.md
```

> **Note:** This project uses a fictional/anonymised dataset for learning and portfolio purposes. Findings describe observed associations and should not be interpreted as causal or clinical conclusions.
