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
- **Source**: [311 Service Requests from 2010 to Present](https://data.cityofnewyork.us/Social-Services/311-Service-Requests-from-2010-to-Present/erm2-nwe9/about_data)
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

## 🔍 Step 4: Data Collection & Filtering

This step focuses on narrowing down the datasets for meaningful, location-aligned analysis.

- **Timeframe Selected**: 2020–Present (to capture pre/post-COVID trends)
- **Geography**: All five NYC boroughs (ZIP-level filtering)
- **311 Complaints Filtered by Type**:
  - Mold, Rodent, Unsanitary Condition, Plumbing, Air Quality, etc.
- **Downloaded Datasets Organized in `data/` folder** with relevant filenames
- ****🔗 Large Files (External Downloads)**

Due to GitHub's file size limitations, the following large datasets are hosted on Google Drive:

- [311_filtered_complaints_2020_2024.csv](https://drive.google.com/file/d/12UVB9y2OfdQKsW5suYzSDKOebwpvj0HZ/view?usp=sharing)
- [SPARCS_inpatient_NYC_2020_2022.csv](https://drive.google.com/file/d/1QroR-wm8Cmrjg3rnuG6YQ_yhb6TncqpR/view?usp=sharing)

This filtered data will feed into the next phase of the project for cleaning, merging, and analysis.

## 🧹 Step 5: Data Cleaning & Preprocessing

To ensure analysis-ready datasets, each raw file was cleaned by handling missing values, fixing structural inconsistencies, and preparing for merging by location and time. Below is a summary of the preprocessing work completed:

### 🔍 Cleaning Tasks Performed

- **Handled Missing Values**: 
  - Dropped rows missing critical fields like `Zip Code`, `Complaint Type`, `Discharge Year`, etc.
  - Filled non-critical fields with `"Unknown"` to retain structure.
  
- **Standardized Column Names**:
  - Removed leading/trailing spaces and fixed formatting issues.

- **Structured and Saved Clean Versions**:
  - Each cleaned file was saved under a new `/data` directory for downstream use.

### ✅ Cleaned Files

| File Name                                         | Format | Notes                                                                 |
|--------------------------------------------------|--------|-----------------------------------------------------------------------|
| `311_filtered_complaints_2020_2024.csv`          | CSV    | Cleaned missing zip codes, complaint types, and address info         |
| `ACS_B25008_housing_cleaned.xlsx`                | Excel  | Housing estimates cleaned and formatted                              |
| `ACS_DP05_demographics_cleaned.xlsx`             | Excel  | Demographic totals and estimates cleaned                             |
| `NYC_checkbook_2022_cleaned.csv`                 | CSV    | Budget data filtered by agency name and spending type                |
| `NYC_community_health_profiles_cleaned.xlsx`     | Excel  | Extracted `CHP_all_data` sheet and cleaned borough/neighborhood data |
| `SPARCS_inpatient_NYC_2020_2022_cleaned.csv`     | CSV    | Cleaned inpatient diagnosis and discharge data by ZIP                |

---

## 🧠 Step 6: Feature Engineering

This step focuses on transforming and enriching the cleaned 311 complaint data to extract useful signals for predictive analytics and visualization. Key engineered features include complaint frequency, service resolution metrics, lag variables, and population-based normalization.

### 🔧 What Was Done

- **📅 Complaint Frequency Metrics:**  
  Grouped 311 complaints by `Incident Zip` and `YearMonth` to track temporal trends and density of complaints across time.

- **⏳ Resolution Times:**  
  Calculated complaint resolution time (in days) as the difference between `Created Date` and `Closed Date`.

- **🔁 Lag Features:**  
  Created `Lag_Complaint_Count` by shifting previous month's complaint totals per ZIP to model predictive relationships with public health outcomes.

- **📊 Demographic Integration:**  
  Merged cleaned ACS DP05 population data by ZIP, enabling calculation of:
  - `Complaints_per_1000 = (Total Complaints / Population) * 1000`

- **📁 Files Added:**
  - `/notebooks/feature_engineering.ipynb` – The notebook containing all transformations and visual previews.
  - `/data/311_with_population_features.csv` – Final engineered dataset including temporal, resolution, and normalized fields.

### ✅ Outcome
The dataset is now enriched with actionable metrics and ready for Exploratory Data Analysis (EDA) and modeling.

## 🔍 Step 7: Exploratory Data Analysis (EDA)

The goal of this step is to uncover patterns, trends, and relationships in NYC 311 complaints, population demographics, and public health data. EDA helps us understand which complaint types dominate, how they vary across ZIP codes, and whether they correlate with healthcare burdens like emergency room (ER) visits.

### 📌 Sub-Steps Covered:
| Sub-Step | Description |
|----------|-------------|
| **7.1 Complaint Type Distributions** | Identify the most common complaint types affecting NYC neighborhoods. |
| **7.2 Temporal Trends by Neighborhood** | Track how complaint volumes change over time in different ZIP codes. |
| **7.3 Heatmaps & Correlation Analysis** | Explore statistical relationships between complaints, population, and response times. |
| **7.4 Health vs Complaint Rate Visualizations** | Compare normalized complaint rates with SPARCS ER visits to detect public health signals. |
| **7.5 Mapping Complaint Hotspots** | Visualize complaint concentrations on NYC maps using GeoJSON and Folium overlays. |

Each of these steps builds the foundation for predictive modeling and risk analysis in the final stages.

### 📊 7.1 Complaint Type Distributions

This visualization displays the **top health-relevant 311 complaint types** recorded across NYC.

### 🔍 Observations:
- **Noise - Residential** and **Noise - Street/Sidewalk** are the most frequently reported issues, highlighting ongoing environmental stressors.
- **Rodent** and **Indoor Air Quality** complaints, while smaller in count, are directly linked to public health risks (e.g., asthma, food safety).
- These findings helped us identify and isolate complaints that are most likely to impact health outcomes in later analysis steps.

> ✅ This step helps prioritize complaint categories that warrant closer attention when correlating with health and hospitalization data.

### 7.2 Temporal Trends by Neighborhood

In this analysis, we examined how complaint volume changes over time across different ZIP codes in NYC. Monthly complaint counts were aggregated and visualized for the top 5 ZIP codes with the highest total volume.

The resulting line chart provides a clear view of complaint patterns, highlighting seasonal trends or sudden spikes in activity.

**Key Insight:**  
ZIP code **10466** showed a significant surge in complaints during late 2024, potentially indicating a localized issue or disruption. This trend could warrant further investigation into events or conditions that triggered the rise. Tracking these patterns over time helps city agencies allocate resources and respond proactively to emerging concerns.

### 7.3 Heatmaps & Correlation Analysis

This section focuses on examining potential relationships between different numerical variables in the dataset. Using a correlation matrix visualized as a heatmap, we explored how complaint response time, total population, and complaints per 1000 residents relate to each other.

**Key Observations:**

- There is **low or negligible correlation** between **Response Time** and **Total Population** or **Complaint Rate**.
- A **weak positive correlation (0.18)** exists between **Total Population** and **Complaints per 1000 Residents**, suggesting that complaint rates are somewhat higher in more densely populated ZIP codes.
- Response times remain consistent across different complaint volumes, implying good operational response regardless of population or complaint density.

These correlations provide helpful signals for prioritizing which variables matter in predictive modeling or resource allocation.

### 7.4 Health vs Complaint Rate Visualizations

To explore the potential relationship between civic complaints and public health burden, we visualized a scatter plot comparing:

- **311 complaints per 1000 residents** (horizontal axis) and
- **Emergency Room visits** from the SPARCS dataset (vertical axis), aggregated by 3-digit ZIP code.

**Key Observations:**

- ZIP code regions with unusually high complaint rates tend to also show elevated ER visits, suggesting a potential link between unresolved civic issues and adverse health outcomes.
- One notable outlier (ZIP starting with 104 — likely the Bronx) had the highest complaint density and also one of the highest ER visit totals. This aligns with known public health and housing concerns in the area.

This visualization helps identify areas where investments in civic infrastructure and environmental conditions could yield both community and health benefits.

### 7.5 Mapping Complaint Hotspots

This step visualizes the density of health-related 311 complaints (e.g., Rodent, Indoor Air Quality) per 1000 residents across NYC ZIP codes using a choropleth map.

**Key Insights:**

- 🔴 **Hotspot ZIP codes** like `10466` and surrounding Bronx neighborhoods show **high normalized complaint rates**, suggesting potential clusters of poor housing conditions.
- 🟡 In contrast, some densely populated ZIPs in Manhattan show **lower complaint rates**, which may reflect better infrastructure or lower reporting from underrepresented groups.
- 🌍 The visualization reveals **clear spatial disparities** in public health and housing maintenance, aligning with known socioeconomic trends in outer boroughs like the Bronx and Queens.
- ⚠️ These hotspots can be cross-referenced with ER visit data to identify areas where unresolved civic complaints may correlate with elevated health risks.

**Why it’s useful:**

- Supports **targeted interventions** by city health/housing departments.
- Can inform **resource allocation**, especially for vulnerable ZIPs.
- Helps identify **systemic reporting gaps** or under-resourced neighborhoods.

## 🔮 Step 8: Predictive Modeling

In this step, we forecast public health risks by modeling Emergency Room (ER) visits based on civic complaint patterns (from 311 data). This approach helps city agencies preemptively identify neighborhoods at risk and take preventive action.

---

### ✅ Objective:
Build a predictive model to estimate ER visits by ZIP3 using features like:
- Complaint counts (health-related)
- ZIP-level demographics (e.g., population)
- Temporal trends (monthly)

---

### 📊 Dataset Used:
- `zip3_complaints_er_merged.csv` – merged 311 complaints and ER visit data by 3-digit ZIP codes.
- GeoJSON files for spatial visualization (used later).

---

### ⚙️ Process:

#### • Model Selection:
We used a **Poisson Regression** model since ER visits are **count data**. It fits scenarios where target values are non-negative integers and follow a Poisson distribution.

#### • Splitting Training & Test Sets:
Data was split by ZIP3 codes – a portion of ZIPs were used to train the model, and the rest were used for validation.

#### • Features Used:
- Complaint_Count (per ZIP3)
- Demographic (population normalization)
- Complaint types (filtered for health signals like Mold, Rodents, etc.)

#### • Target:
- `ER_Visits` (number of emergency room visits per ZIP3)

---

### 📈 Model Results:

- **Model**: `Poisson Regression`
- **McFadden’s Pseudo R²**: ~0.67 → Indicates good model fit (values between 0.2 - 0.4 are decent; >0.5 is strong).
- **Predicted vs Actual ER Visits** showed strong alignment with some natural variance.

---

### 🔍 Feature Insights:
| Feature          | Coefficient | Interpretation                                |
|------------------|-------------|-----------------------------------------------|
| Complaint_Count  | +ve         | More complaints → higher predicted ER visits  |

---

### 🗺 Visual Output:
- **Risk Map** of top ZIP3 areas with predicted ER visits.
- Regions color-coded into:
  - 🔴 High Priority
  - 🟠 Medium Priority
  - 🟢 Low Priority

👉 Map: [Click here to view the Health Risk Map](https://SravyaModali.github.io/311-signals-nyc-health-risk/zip3_health_risk_map.html
)

---

### ✅ Takeaway:
This model helps:
- Prioritize ZIPs for inspections, public health outreach, or sanitation efforts.
- Allocate resources to prevent reactive healthcare expenses.
- Identify complaint types most associated with hospitalizations.

---

