# Online Retail Intelligence Capstone

**A Data Analytics, Statistical Analysis and Machine Learning Project Using Python and Tableau**

This project analyses historical UK online retail transactions to investigate sales performance, customer purchasing behaviour and customer segmentation. It combines data cleaning, exploratory data analysis, statistical hypothesis testing, machine learning and business intelligence to generate actionable retail insights.

## 1. Project Overview

The Online Retail Intelligence Capstone aims to help retail businesses understand their customers, evaluate sales performance and identify opportunities for revenue growth and customer retention.

The project uses Python to process and analyse transactional data, statistical techniques to investigate purchasing patterns, and K-Means clustering to identify distinct customer segments.

A published Tableau visualisation presents business insights. Further dashboard development is planned for a future phase.

## 2. Business Objectives

The project addresses six main objectives:

1. Analyse overall retail sales performance and revenue trends.
2. Identify important geographical markets and purchasing patterns.
3. Examine customer spending, purchase frequency and order behaviour.
4. Test statistical hypotheses about customer behaviour and geographical differences.
5. Apply Recency, Frequency and Monetary (RFM) analysis and K-Means clustering to segment customers.
6. Communicate findings and recommend data-driven strategies for marketing, customer retention and business growth.

## 3. Target Audience

| Audience | Expected Value |
|---|---|
| Retail business managers | Understand sales performance and revenue opportunities |
| Marketing teams | Develop targeted campaigns based on customer segments |
| Customer retention teams | Identify historical purchasing patterns that may inform engagement strategies |
| Business analysts | Explore statistical findings and commercial insights |
| Data analysts | Review the data preparation, analytical methods and machine learning workflow |

## 4. Dataset Description

The project uses historical transactional data from a UK-based online retailer, covering transactions from 2010 to 2011.

The dataset includes information about transactions, products, quantities, prices, customers and geographical markets.

### Key Variables

| Variable | Description |
|---|---|
| InvoiceNo | Transaction or invoice identifier |
| StockCode | Product identifier |
| Description | Product description |
| Quantity | Number of units purchased |
| InvoiceDate | Date and time of transaction |
| UnitPrice | Price per product unit |
| CustomerID | Customer identifier |
| Country | Customer's geographical market |

### Processed Datasets

The project produces three principal datasets for analysis and visualisation:

- `retail_sales_tableau.csv`: Cleaned sales transaction data.
- `retail_customer_intelligence.csv`: Customer-level purchasing metrics.
- `retail_customer_segments.csv`: Customer intelligence data enriched with K-Means cluster assignments and segment labels.

These files are generated through the project's analytical workflow.

**Data source:** Historical Online Retail dataset. The original dataset provider and download URL should be documented here before final submission.

## 5. Data Analytics Methodology

The project follows a structured analytical workflow.

### 5.1 Data Collection

The original retail dataset is imported into Python for examination and processing.

Initial checks include:

- Reviewing dataset dimensions and column types.
- Identifying missing and duplicate records.
- Examining numerical and categorical variables.
- Investigating invalid transaction values.
- Assessing data suitability for analysis.

### 5.2 Data Cleaning and Preparation

Data cleaning is performed to improve the reliability of the analysis.

The process includes:

- Handling missing values.
- Reviewing duplicate records.
- Identifying cancelled or invalid transactions.
- Filtering invalid quantities and prices where appropriate.
- Converting date columns to appropriate data types.
- Creating calculated revenue fields.
- Preparing customer-level analytical datasets.

Cleaning decisions are documented in the relevant Jupyter notebooks.

### 5.3 Exploratory Data Analysis

Exploratory data analysis investigates:

- Total revenue and transaction patterns.
- Sales performance across geographical markets.
- Customer purchasing behaviour.
- Order values and spending distributions.
- Differences between one-time and repeat customers.
- Relationships between purchase frequency and spending.

Visualisations are used to identify patterns, distributions, outliers and potential business opportunities.

### 5.4 Statistical Hypothesis Testing

Three statistical investigations are conducted.

**Hypothesis 1: Repeat Customers vs One-Time Customers**

Investigates whether repeat and one-time customers differ in their spending behaviour.

Methods:

- Welch's independent-samples t-test.
- Mann–Whitney U test.

**Hypothesis 2: Purchase Frequency and Average Order Value**

Examines whether customers who purchase more frequently tend to have higher average order values.

Method:

- Spearman's rank correlation.

**Hypothesis 3: UK vs International Order Values**

Investigates whether invoice-level order values differ between UK and international customers.

Methods:

- Welch's independent-samples t-test.
- Mann–Whitney U test.

The statistical methods were selected with consideration for data distribution, independence, unequal variances and the nature of the variables.

Statistical significance is interpreted alongside effect magnitude and practical business relevance. Observed associations are not treated as evidence of causation.

## 6. Machine Learning: Customer Segmentation

### 6.1 RFM Analysis

Customer segmentation uses three purchasing behaviour indicators:

- **Recency (R):** How recently a customer made a purchase relative to the dataset's reference date.
- **Frequency (F):** How frequently a customer purchased.
- **Monetary (M):** How much a customer spent.

RFM analysis helps identify differences in customer purchasing behaviour and commercial value.

### 6.2 Feature Preparation

The machine learning workflow includes:

1. Selecting RFM features.
2. Examining feature distributions and outliers.
3. Applying logarithmic transformations to reduce skewness.
4. Standardising the features.
5. Evaluating candidate cluster counts.
6. Applying K-Means clustering.
7. Interpreting and labelling customer segments.

### 6.3 Model Selection and Evaluation

The Elbow Method and sampled Silhouette Scores were used to assess different cluster counts.

The highest sampled Silhouette Score was approximately **0.4285 for two clusters**, compared with **0.3295 for four clusters**.

Four clusters were selected provisionally because they offered more detailed and potentially actionable customer profiles.

This represents a trade-off between statistical cluster separation and business interpretability.

### 6.4 Identified Customer Segments

| Segment | Customers | Customer Share | Revenue Share |
|---|---:|---:|---:|
| Champions | 704 | 16.23% | 64.32% |
| At-Risk / Inactive | 1,564 | 36.06% | 6.41% |
| Established Customers | 1,174 | 27.07% | 24.36% |
| Recent Occasional Buyers | 895 | 20.64% | 4.92% |

*Revenue shares refer to revenue associated with identified customers in the segmentation dataset, not necessarily all retail transactions.*

These segments provide an exploratory understanding of customer purchasing patterns. They do not represent verified current customer statuses or predictions of future churn.

## 7. Key Findings

### 7.1 Sales Performance

The cleaned sales dataset contains approximately **524,878 valid transaction rows**, representing:

- **Total revenue:** £10,642,110.80
- **Unique orders:** 19,960
- **UK revenue:** £9,001,744.09
- **International revenue:** £1,640,366.71

The UK accounts for the majority of recorded revenue, highlighting its importance to the retailer's historical business performance.

### 7.2 Customer Behaviour

The customer intelligence dataset contains **4,337 identified customers**:

- **2,844 repeat customers**
- **1,493 one-time customers**

The analysis examines how purchasing frequency relates to spending and average order values.

### 7.3 Statistical Findings

The analysis found a statistically significant but weak positive association between purchase frequency and average order value:

- **Spearman correlation:** approximately 0.1563.
- **p-value:** approximately 4.07 × 10⁻²⁵.

This indicates that more frequent purchasing is associated with slightly higher average order values, although the relationship is weak.

International orders also had higher average invoice values than UK orders in the analysed dataset:

| Metric | UK | International |
|---|---:|---:|
| Mean order value | £499.57 | £849.44 |
| Median order value | £299.95 | £427.53 |

Both Welch's t-test and the Mann–Whitney U test indicated statistically significant differences.

These findings are observational and should not be interpreted as causal relationships.

### 7.4 Customer Segmentation Findings

Champions represent approximately **16.23% of identified customers** but contribute **64.32% of identified-customer revenue**.

This suggests that a relatively small proportion of customers accounts for a substantial share of revenue.

The segmentation also identifies a large group of historically inactive customers, providing a potential starting point for retention and re-engagement research.

## 8. Business Recommendations

| Customer Segment | Recommended Strategy |
|---|---|
| Champions | Prioritise loyalty, recognition and personalised retention initiatives |
| At-Risk / Inactive | Investigate inactivity and test targeted re-engagement campaigns |
| Established Customers | Encourage repeat purchasing through relevant offers and loyalty initiatives |
| Recent Occasional Buyers | Develop onboarding, follow-up and second-purchase engagement strategies |

These recommendations are exploratory and should be validated through customer research, controlled experiments and business performance monitoring before large-scale implementation.

## 9. Tableau Business Intelligence Dashboard

A Tableau Public visualisation has been published as part of the project.

**[View the Online Retail Intelligence – Business Insights Story](https://public.tableau.com/app/profile/oluwaseun.olasupo/viz/OnlineRetailIntelligenceSalesCustomerAnalytics/OnlineRetailIntelligence-BusinessInsightsStory)**

The Tableau visualisation supports the communication of retail analytics findings through business intelligence.

### Future Dashboard Development

The published dashboard will be developed further in a future project phase.

Planned enhancements include:

- Integrating the four K-Means customer segments.
- Expanding customer intelligence visualisations.
- Improving interactive filtering and navigation.
- Strengthening business storytelling and insight presentation.
- Refining dashboard layout, accessibility and user experience.

The current published version should be treated as an existing visualisation rather than the final dashboard implementation.

## 10. Technologies and Tools

| Technology | Purpose |
|---|---|
| Python | Data preparation, statistical analysis and machine learning |
| Pandas | Data manipulation and aggregation |
| NumPy | Numerical operations |
| Matplotlib | Data visualisation |
| Seaborn | Statistical visualisation |
| SciPy | Statistical hypothesis testing |
| Scikit-learn | Data transformation, K-Means clustering and model evaluation |
| Jupyter Notebook | Documenting and executing the analytical workflow |
| Tableau | Business intelligence and interactive visualisation |
| Git and GitHub | Version control and project management |
| Visual Studio Code | Development environment |

## 11. Project Structure

```text
Online-Retail-Intelligence-Capstone/
│
├── .github/
│
├── data/
│   └── tableau/
│       ├── retail_sales_tableau.csv
│       ├── retail_customer_intelligence.csv
│       └── retail_customer_segments.csv
│
├── jupyter_notebooks/
│   ├── 01_data_collection.ipynb
│   ├── 02_data_cleaning.ipynb
│   ├── 03_exploratory_data_analysis.ipynb
│   ├── 04_statistical_hypothesis_testing.ipynb
│   └── 05_customer_segmentation.ipynb
│
├── .gitignore
├── LICENSE
├── README.md
└── requirements.txt
```

The processed data files are shown in their working locations. Their availability in a fresh repository clone depends on the project's Git tracking and data distribution settings.

## 12. Running the Project Locally

### Prerequisites

- Python 3.12 or a compatible Python version.
- Git.
- Visual Studio Code or Jupyter Notebook.

### Clone the Repository

```bash
git clone https://github.com/SeunJoy/Online-Retail-Intelligence-Capstone.git
```

```bash
cd Online-Retail-Intelligence-Capstone
```

### Create a Virtual Environment

```bash
python -m venv .venv
```

Activate the environment on Windows:

```bash
.venv\Scripts\activate
```

### Install Dependencies

```bash
pip install -r requirements.txt
```

### Open the Notebooks

Open the project in Visual Studio Code, select the Python environment and run the notebooks in numerical order.

The original dataset must be available at the input location expected by the data collection notebook. Check notebook file paths before execution.

## 13. Data Ethics and Responsible Analysis

The project considers responsible data handling and interpretation.

Key considerations include:

- Using customer identifiers for analysis rather than personal identification.
- Avoiding unnecessary exposure of customer-level information.
- Maintaining awareness of privacy and data protection obligations.
- Documenting data cleaning and transformation decisions.
- Avoiding unsupported causal claims.
- Recognising that historical customer behaviour does not establish future intentions.
- Treating customer segment labels as analytical interpretations rather than definitive characteristics.

Where the analysis is adapted for real-world business use, appropriate data protection, access controls and governance procedures should be implemented.

## 14. Limitations

The project has several limitations.

**Historical data:** The dataset covers transactions from 2010–2011. Findings may not represent current consumer behaviour or retail market conditions.

**Missing customer identifiers:** Some transaction records cannot be attributed to individual customers, limiting customer-level analysis.

**Outliers and skewed distributions:** Retail spending data contains extreme values that may affect statistical summaries and machine learning.

**Observational analysis:** Statistical associations do not establish causal relationships.

**Clustering assumptions:** K-Means requires a predefined number of clusters and is sensitive to scaling, feature selection and extreme observations.

**Model selection:** The four-cluster solution did not achieve the highest sampled Silhouette Score and requires further validation.

**Business validation:** Customer segment recommendations have not been evaluated through controlled marketing experiments.

**Dashboard development:** Additional Tableau interactivity, customer segmentation integration and user-experience improvements remain planned.

## 15. Alternative Approaches and Future Improvements

Future work could include:

1. Comparing K-Means with hierarchical clustering, DBSCAN and Gaussian Mixture Models.
2. Evaluating the stability of customer segments over different time periods.
3. Incorporating additional customer behaviour variables.
4. Exploring predictive models for repeat purchasing or customer churn, using appropriate labelled data.
5. Testing targeted marketing strategies through controlled experiments.
6. Expanding the Tableau dashboard and integrating machine learning outputs.
7. Improving documentation, automated validation and reproducibility.

These are proposed improvements rather than completed project features.

## 16. Learning Reflection

Developing this capstone strengthened my practical understanding of data analytics, statistical analysis, machine learning and business intelligence.

One of the main challenges was cleaning the retail dataset and ensuring that the analytical results were based on reliable records. This required careful examination of missing values, invalid transactions and unusual observations.

Selecting and applying appropriate Python code was another challenge. Working through errors and validating analytical outputs helped improve my debugging, problem-solving and programming skills.

Applying machine learning principles required an understanding of feature preparation, standardisation, clustering and model evaluation. The project demonstrated that statistical performance and business interpretability do not always lead to the same modelling decision.

Dashboard development also presented challenges, particularly around interactivity, visual organisation and communicating insights effectively. Further refinement is planned.

Overall, the project improved my technical confidence, critical thinking and ability to connect analytical methods with practical business questions.

## 17. Project Status

| Component | Status |
|---|---|
| Data collection | Completed |
| Data cleaning | Completed |
| Exploratory data analysis | Completed |
| Statistical hypothesis testing | Completed |
| RFM customer analysis | Completed |
| K-Means customer segmentation | Completed |
| Tableau visualisation | Published; further development planned |
| Project documentation | In progress |
| Final assessment and validation | Pending |

## 18. Repository and Project Links

**GitHub Repository:**  
https://github.com/SeunJoy/Online-Retail-Intelligence-Capstone

**Tableau Public Dashboard:**  
https://public.tableau.com/app/profile/oluwaseun.olasupo/viz/OnlineRetailIntelligenceSalesCustomerAnalytics/OnlineRetailIntelligence-BusinessInsightsStory

## 19. Author

**Oluwaseun Olasupo**

Data Analytics and Artificial Intelligence Capstone Project

## 20. Licence

Refer to the `LICENSE` file in this repository for the applicable licence terms.
