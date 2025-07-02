# 311 Signals: Predicting Health & Cost Risks in NYC Neighborhoods

## 📍 Problem Statement
New York City has made major strides in collecting civic and health-related data, but a real-time, unified system that connects 311 complaints with public health outcomes and financial impact still does not exist. Data systems like EpiQuery, HHS-Connect, and NYC Open Data remain fragmented, limiting early detection of health risks and cost inefficiencies.

311 service requests—covering issues like rodents, air quality, and housing conditions—contain valuable signals that often precede public health challenges. Yet this data is rarely used to inform timely interventions. As a result, many issues escalate into crises, especially in underserved neighborhoods, increasing both human and economic costs.

This project aims to bridge that gap by analyzing 311 trends to predict neighborhood-level health and cost risks, empowering smarter, data-driven decisions by city planners and health departments.

## 🎯 Research Objectives
- Analyze patterns in 311 complaints across NYC neighborhoods over time
- Identify correlations between complaint types and public health outcomes
- Predict neighborhood-level health and cost risks using complaint data
- Build an interactive dashboard to visualize high-risk areas and support early intervention

## 🌍 Real-World Relevance
This project helps city departments and public health agencies leverage 311 complaint data as an early warning system for health and cost-related risks. By identifying patterns and predicting where issues are likely to escalate, the model supports timely, data-driven interventions that can prevent avoidable health crises and reduce public spending. It also promotes greater transparency and ensures resources are allocated more equitably—especially in underserved neighborhoods that often face delayed responses.

## ❓ Research Questions & Hypotheses

### 🔍 Research Questions
1. Do certain types of 311 complaints (e.g., rodent, sanitation, air quality) correlate with poor public health outcomes in specific NYC neighborhoods?
2. Can patterns in complaint frequency predict future spikes in health-related issues such as asthma or emergency visits?
3. Are there neighborhoods where unresolved 311 complaints are consistently followed by higher healthcare-related costs?
4. Does complaint response time differ by neighborhood income level or demographic profile?

### 💡 Hypotheses
- **H1**: Neighborhoods with high volumes of rodent and sanitation complaints will also show higher asthma or respiratory illness rates.
- **H2**: A time lag exists between complaint spikes and increased emergency room visits or health costs.
- **H3**: Underserved or low-income neighborhoods have longer complaint resolution times, contributing to worse health outcomes.
- **H4**: Predictive models built on 311 trends can identify at-risk areas before official health data flags them.

## 📂 Data Sources & Files

This project uses open public datasets from NYC agencies and federal census sources to analyze 311 complaints, health outcomes, demographics, and government spending.

| Filename                                 | Description                                                                                 | Source            |
|------------------------------------------|---------------------------------------------------------------------------------------------|-------------------|
| `311_filtered_complaints_2024_2025.xlsx` | NYC 311 service requests related to health signals (e.g., rodents, air quality, mold)       | NYC Open Data     |
| `ACS_NYC_Data_DP05.xlsx`                 | Demographic profile (age, race, sex) by ZIP code                                            | U.S. Census ACS   |
| `ACS_NYC_Data_B25008.xlsx`               | Housing condition data: population in occupied housing units by tenure                     | U.S. Census ACS   |
| `Community Health Profiles.xlsx`         | Public health indicators by NYC neighborhood (e.g., asthma rates, chronic conditions)       | NYC Health Dept.  |
| `Hospital Inpatient Discharges.xlsx`     | SPARCS hospital discharge data with top diagnoses by county                                | NY State Health   |
| `NYC_Checkbook.csv`                      | Spending by NYC agencies — budget, contract, and payroll details by department              | NYC Checkbook     |

## 🗂️ Folder Structure

Here’s how the files and scripts are organized:

311-signals-health-costs-nyc/
├── data/
│   ├── 311_filtered_complaints_2024_2025.xlsx
│   ├── ACS_NYC_Data_DP05.xlsx
│   ├── ACS_NYC_Data_B25008.xlsx
│   ├── Community_Health_Profiles.xlsx
│   ├── Hospital_Inpatient_Discharges.xlsx
│   └── NYC_Checkbook.csv
│
├── notebooks/
│   ├── 01_cleaning.ipynb
│   ├── 02_exploration.ipynb
│   └── 03_modeling.ipynb
│
├── outputs/
│
├── README.md
└── requirements.txt (optional)


