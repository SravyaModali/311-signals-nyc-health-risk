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

## 🗂️ Step 3: Data Source Identification

This project uses data from multiple publicly available NYC datasets to analyze and predict neighborhood-level health and cost risks:

### 🟢 311 Complaint Data
- **Source**: [311 Service Requests from 2010 to Present](https://data.cityofnewyork.us/Social-Services/311-Service-Requests-from-2010-to-Present/erm2-nwe9)
- **Key Fields**: Complaint Type, Created Date, Borough, Incident Zip, Resolution Time
- **Usage**: Identifying patterns in rodent, sanitation, and air quality complaints

### 🔵 Health Outcome Data
- **Source 1**: [NYC Community Health Profiles](https://www.nyc.gov/site/doh/data/data-publications/profiles.page)
- **Source 2**: [SPARCS Inpatient Hospitalization Data](https://health.data.ny.gov/Health/Hospital-Inpatient-Discharges-SPARCS-De-Identified/nqwf-w8eh)
- **Key Fields**: Asthma ER visits, Chronic disease rates, Zip code identifiers
- **Usage**: Correlating complaint patterns with health outcomes

### 🟣 Cost and Equity Data
- **Sources**:
  - [Checkbook NYC](https://www.checkbooknyc.com/)
  - [ACS Demographics – U.S. Census](https://data.census.gov/)
- **Key Fields**: Neighborhood income, population density, public expenditure by zip
- **Usage**: Estimating financial risk and identifying underserved areas

│   └── 03_modeling.ipynb
│
├── outputs/
│
├── README.md
└── requirements.txt (optional)


