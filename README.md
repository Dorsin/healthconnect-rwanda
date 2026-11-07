# HealthConnect Rwanda Healthcare Analytics & Predictive Modeling Project

## Project Overview
HealthConnect Rwanda is a healthcare provider network with patient, clinical, operational, financial, and patient feedback data. This repository contains the HealthConnect Rwanda work developed across Weeks 6, 7 and 8. Week 6 established the integrated analytics workflow; Week 7 tested and refined a provisional admission model; Week 8 records final integration readiness, source-lineage findings, the executed notebook, its HTML and PDF exports, and the final presentation.

The analytical master dataset contains 5,000 appointment records for 4,443 distinct patients. The project uses 30 logical tables sourced from 37 files and workbook sheets.

## Relational Architecture & Dataset Coverage
The master analytical pipeline is built at the appointment grain and connects the available healthcare entities through their identifiers:
- **Patients & Geography:** Patient demographics, recorded chronic conditions, insurance identifiers, and geographic hierarchy from provinces through villages
- **Appointments, Doctors & Departments:** Appointment dates and types, patient links, provider attributes, department identifiers, and facility references
- **Clinical Activity:** Diagnoses, admissions, laboratory tests, prescriptions, and referrals associated with appointments
- **Billing & Payments:** Billing records, payment transactions, and insurance claims linked through appointment and billing identifiers
- **Operations & Experience:** Staff, beds, equipment, services, specialties, and patient feedback records

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
│   ├── Week7_HealthConnect_Rwanda_Testing.html    # HTML export of the Week 7 notebook
│   ├── Week8_HealthConnect_Rwanda_Final_Integration.ipynb  # Week 8 final model and readiness package
│   └── Week8_HealthConnect_Rwanda_Final_Integration.html   # HTML export of the Week 8 notebook
│
├── Presentation/
│   ├── Week6_Executive_Presentation.pptx   # Executive presentation (12 slides)
│   └── Week8_HealthConnect_Final_Model_Review.pptx  # Week 8 final model review (9 slides, ~7 minutes)
│
├── Reports/
│   ├── Week6_Part2_Data_Quality_Report.pdf
│   ├── Week6_Part3_EDA_Report.pdf
│   ├── Week6_Part6_Statistical_Analysis_Report.pdf
│   ├── Week6_Part7_Predictive_Analytics_Report.pdf
│   ├── Week6_Technical_Report.pdf          # Consolidated technical project report
│   ├── Week6_Executive_Summary.pdf
│   ├── Week7_Technical_Report.pdf
│   └── Week8_HealthConnect_Rwanda_Final_Integration.pdf  # PDF export of the Week 8 notebook
│
├── Visualizations/
│   ├── Charts/                              # Numbered chart exports (Visual 1 to Visual 41)
│   │   └── README.md                        # Visualization catalog
│   └── Dashboards/
│
└── README.md
```

The French Week 8 learning notebook and the presentation speaker script are kept outside Git. The English Week 8 notebook is available as an interactive Jupyter notebook and as HTML and PDF exports. The final presentation is included as a project deliverable.

The Week 7 notebook reuses the cleaned master dataset from Week 6 rather than duplicating source data. Week 7 did not show reliable improvement over a prior-rate reference. Week 8 confirms that the source workbook contains an Admissions worksheet and documents 4,414 keys that do not match appointment records. No final admission model is approved until the target lineage is reconciled. The project data do not contain a validated attendance/no-show target.

The cleaned master dataset has one row per appointment and no remaining null cells. The engineered feature dataset intentionally preserves missing values for fields that cannot be inferred safely from the source data, including unknown clinical history and unavailable feedback.
