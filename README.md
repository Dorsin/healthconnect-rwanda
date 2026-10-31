# HealthConnect Rwanda Healthcare Analytics & Predictive Modeling Project

## Project Overview
HealthConnect Rwanda is a healthcare provider network with patient, clinical, operational, financial, and patient feedback data. This repository contains the HealthConnect Rwanda work developed across Weeks 6 and 7. Week 6 established the integrated analytics workflow; Week 7 tests and refines the admission model, documents errors and limitations, and records the cross-track validation work.

The analytical master dataset contains 5,000 appointment records for 4,443 distinct patients. The project uses 30 logical tables sourced from 37 files and workbook sheets.

## Relational Architecture & Dataset Coverage
The master analytical pipeline is built at the appointment grain and connects the available healthcare entities through their identifiers:
- **Patients & Geography:** Patient demographics, recorded chronic conditions, insurance identifiers, and geographic hierarchy from provinces through villages.
- **Appointments, Doctors & Departments:** Appointment dates and types, patient links, provider attributes, department identifiers, and facility references.
- **Clinical Activity:** Diagnoses, admissions, laboratory tests, prescriptions, and referrals associated with appointments.
- **Billing & Payments:** Billing records, payment transactions, and insurance claims linked through appointment and billing identifiers.
- **Operations & Experience:** Staff, beds, equipment, services, specialties, and patient feedback records.

*Note: `HC_Revenue_Summary.csv` is retained as a standalone source because it has no reliable key for allocation to appointments, departments, or facilities. Financial analysis therefore uses appointment-linked billing and payment transactions. Insurance identifiers do not establish active coverage, and roster records do not measure time-based staffing or facility utilization.*

## Repository Directory Structure
```text
HealthConnect_Rwanda_Project/
│
├── Data/
│   ├── Cleaned_Datasets/
│   │   ├── healthconnect_master_clean.csv  # Clean appointment-level master dataset
│   │   └── healthconnect_features.csv      # Appointment-level dataset with engineered features
│   └── Original_Datasets/                  # Supplied source CSV and Excel files
│
├── Notebook/
│   ├── Week6_HealthConnect_Rwanda.ipynb    # Main notebook with the complete analysis workflow
│   ├── Week6_HealthConnect_Rwanda.html     # HTML export of the Week 6 notebook
│   ├── Week7_HealthConnect_Rwanda_Testing.ipynb  # Week 7 model testing and validation
│   └── Week7_HealthConnect_Rwanda_Testing.html    # HTML export of the Week 7 notebook
│
├── Presentation/
│   └── Week6_Executive_Presentation.pptx   # Executive presentation (12 slides)
│
├── Reports/
│   ├── Week6_Part2_Data_Quality_Report.pdf
│   ├── Week6_Part3_EDA_Report.pdf
│   ├── Week6_Part6_Statistical_Analysis_Report.pdf
│   ├── Week6_Part7_Predictive_Analytics_Report.pdf
│   ├── Week6_Technical_Report.pdf          # Consolidated technical project report
│   ├── Week6_Executive_Summary.pdf
│   ├── Week7_Technical_Report.pdf
│   └── Week7_Social_Media_Posts.md
│
├── Visualizations/
│   ├── Charts/                              # Numbered chart exports (Visual 1 to Visual 41)
│   │   └── README.md                        # Visualization catalog
│   └── Dashboards/
│
└── README.md
```

The Week 7 notebook reuses the cleaned master dataset from Week 6 rather than duplicating source data. Its final temporal evaluation found no reliable improvement over the prior-rate reference, so the admission model is not approved for operational use. The dataset does not contain a validated attendance/no-show target.

The cleaned master dataset has one row per appointment and no remaining null cells. The engineered feature dataset intentionally preserves missing values for fields that cannot be inferred safely from the source data, including unknown clinical history and unavailable feedback.
