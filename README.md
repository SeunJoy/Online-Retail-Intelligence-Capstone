
# Online Retail Intelligence Capstone

**A Data Analytics, Statistical Hypothesis Testing and Customer Segmentation Project Using Python and Tableau**

This capstone examines historical transactions from a UK-based online retailer to understand sales performance, geographical markets and customer purchasing behaviour.

It combines data cleaning, exploratory data analysis (EDA), statistical hypothesis testing, Recency–Frequency–Monetary (RFM) analysis and K-Means clustering to generate actionable retail insights.

**Project Status:** The Python analysis and exploratory customer segmentation have been completed. An initial Tableau Public story has been published. Further dashboard development, usability testing and final reproducibility checks remain outstanding.

---

## 1. Project Overview

The Online Retail Intelligence Capstone investigates how retail businesses can use transactional data to understand revenue patterns, compare geographical markets, identify differences in customer purchasing behaviour and explore meaningful customer groups.

The project uses historical retail data from 2010–2011 and is intended for educational analysis rather than live commercial decision-making.

### Business Objectives

1. Analyse overall sales performance, revenue and order trends.
2. Compare UK and international sales performance.
3. Examine customer spending, purchase frequency and average order values.
4. Test statistical hypotheses about customer behaviour.
5. Develop customer segments using RFM analysis and K-Means clustering.
6. Communicate findings and recommend potential strategies for marketing, customer retention and business growth.

### Target Audience

| Audience | Expected Value |
|---|---|
| Retail business managers | Understand historical revenue performance and market differences |
| Marketing teams | Explore customer groups and potential engagement strategies |
| Customer retention teams | Investigate purchasing behaviour and customer inactivity |
| Business stakeholders | Understand findings through accessible explanations and visualisations |
| Data analysts and assessors | Review analytical methods, code, statistical evidence and machine learning |

---

## 2. Dataset Description and Source

### Dataset Source

The dataset was obtained from Kaggle:

**[Online Retail Transactions Dataset: Kaggle](https://www.kaggle.com/datasets/abhishekrp1517/online-retail-transactions-dataset)**

**Kaggle contributor:** abhishekrp1517

The dataset contains historical transaction records associated with a UK-based online retailer during 2010–2011.

The Kaggle page is the source used for this project. Users should consult that page for the dataset's provenance and applicable reuse conditions.

### Key Variables

| Variable | Description |
|---|---|
| InvoiceNo | Transaction or invoice identifier |
| StockCode | Product identifier |
| Description | Product description |
| Quantity | Number of units purchased |
| InvoiceDate | Date and time of transaction |
| UnitPrice | Price per product unit |
| CustomerID | Customer identifier, where available |
| Country | Customer's recorded geographical market |

### Units of Analysis

The project distinguishes between:

- **Transaction-level analysis:** Individual sales transaction rows.
- **Invoice-level analysis:** Orders aggregated by invoice number.
- **Customer-level analysis:** Purchasing behaviour associated with identified customers.

Customer-level analysis excludes records without usable customer identifiers. Consequently, revenue totals for all valid transactions and revenue totals for identified customers may differ.

### Processed Datasets

The analytical workflow generates three principal datasets for downstream analysis and visualisation:

- `retail_sales_tableau.csv`: Prepared sales transaction data.
- `retail_customer_intelligence.csv`: Customer-level purchasing metrics.
- `retail_customer_segments.csv`: Customer intelligence data enriched with K-Means cluster assignments and segment labels.

These files are generated within the project's analytical workflow. Their availability in a fresh repository clone depends on the project's Git tracking and data distribution settings.

---

## 3. Data Analytics Methodology

The project follows a structured analytical workflow consisting of five Jupyter notebooks.

### 3.1 Data Collection

**Notebook:** `01_data_collection.ipynb`

The original retail dataset is imported into Python for inspection.

Initial activities include:

- Reviewing dataset dimensions and column types.
- Identifying missing values and duplicate records.
- Examining numerical and categorical variables.
- Investigating invalid transaction values.
- Assessing data suitability for further analysis.

### 3.2 Data Cleaning and Preparation

**Notebook:** `02_data_cleaning.ipynb`

Data cleaning is performed to improve analytical reliability.

Activities include:

- Handling missing values.
- Reviewing duplicate records.
- Identifying cancelled or invalid transactions.
- Filtering invalid quantities and prices where appropriate.
- Converting date columns into suitable data types.
- Calculating transaction revenue.
- Preparing customer-level analytical datasets.

Cleaning decisions are documented in the notebook.

### 3.3 Exploratory Data Analysis

**Notebook:** `03_exploratory_data_analysis.ipynb`

Exploratory analysis investigates:

- Total revenue and sales trends.
- Revenue across geographical markets.
- Customer purchasing patterns.
- Order values and spending distributions.
- Repeat and one-time customers.
- Relationships between purchase frequency and spending.

Visualisations support the identification of patterns, unusual observations and potential business opportunities.

### 3.4 Statistical Hypothesis Testing

**Notebook:** `04_statistical_hypothesis_testing.ipynb`

Three statistical investigations examine differences and associations in customer purchasing behaviour.

Statistical significance is interpreted alongside effect magnitude, assumptions and practical business relevance.

### 3.5 Customer Segmentation

**Notebook:** `05_customer_segmentation.ipynb`

RFM analysis and K-Means clustering are used to identify groups of customers with different historical purchasing characteristics.

The workflow includes feature preparation, transformation, standardisation, cluster evaluation and interpretation.

---

## 4. Statistical Hypotheses and Findings

### Hypothesis 1: Repeat Customers vs One-Time Customers

**Research Question:** Do repeat customers and one-time customers differ in historical spending behaviour?

**Null Hypothesis (H₀):** The two customer groups do not differ in the spending measure being tested.

**Alternative Hypothesis (H₁):** A difference exists between the two groups.

**Methods:**

- Welch's independent-samples t-test.
- Mann–Whitney U test.

The numerical results and interpretations are documented in `04_statistical_hypothesis_testing.ipynb`.

The tests investigate historical spending differences rather than establishing that repeat purchasing causes higher spending.

### Hypothesis 2: Purchase Frequency and Average Order Value

**Research Question:** Is purchase frequency associated with average order value?

**Null Hypothesis (H₀):** No monotonic association exists between purchase frequency and average order value.

**Alternative Hypothesis (H₁):** A monotonic association exists.

**Method:** Spearman's rank correlation.

**Results:**

- Spearman correlation coefficient: **0.1563**
- p-value: **approximately 4.07 × 10⁻²⁵**

**Interpretation:**

A statistically significant but weak positive association was observed.

Customers who purchased more frequently tended to have slightly higher average order values.

However, the relationship was weak, meaning purchase frequency alone is not a reliable indicator of how much a customer spends per order.

### Hypothesis 3: UK vs International Order Values

**Research Question:** Do UK and international customers differ in invoice-level order values?

**Null Hypothesis (H₀):** No difference exists in the order-value measure assessed by each test.

**Alternative Hypothesis (H₁):** A difference exists.

**Methods:**

- Welch's independent-samples t-test.
- Mann–Whitney U test.

### Results

| Metric | UK | International |
|---|---:|---:|
| Orders included | 18,019 | 1,924 |
| Mean order value | £499.57 | £849.44 |
| Median order value | £299.95 | £427.53 |

Seventeen orders with ambiguous geographical classification were excluded from this comparison.

Both tests indicated statistically significant differences.

**Interpretation:**

International orders had higher average and median values than UK orders in the historical dataset.

However, product mix, quantities and customer composition may contribute to these differences.

The analysis does not establish that geographical location causes higher order values.

---

## 5. Machine Learning: Customer Segmentation

### 5.1 RFM Analysis

Customer segmentation uses three purchasing behaviour indicators:

- **Recency (R):** How recently a customer made a purchase relative to the dataset's reference date.
- **Frequency (F):** How frequently a customer purchased.
- **Monetary (M):** How much a customer spent.

RFM analysis helps identify differences in historical customer purchasing behaviour and commercial value.

### 5.2 Feature Preparation

The machine learning workflow includes:

1. Selecting RFM features.
2. Examining distributions and outliers.
3. Applying logarithmic transformations where appropriate.
4. Standardising the features.
5. Evaluating candidate cluster counts.
6. Applying K-Means clustering.
7. Interpreting and labelling customer segments.

### 5.3 Model Selection and Evaluation

The Elbow Method and sampled Silhouette Scores were used to assess alternative cluster counts.

| Number of Clusters | Sampled Silhouette Score |
|---|---:|
| 2 | 0.4285 |
| 4 | 0.3295 |

The two-cluster solution achieved the higher sampled Silhouette Score.

However, four clusters were selected provisionally because they offered more differentiated and potentially actionable customer profiles.

This decision represents a trade-off between statistical cluster separation and business interpretability.

The four-cluster solution remains exploratory and requires further validation.

### 5.4 Identified Customer Segments

| Segment | Customers | Customer Share | Revenue Share |
|---|---:|---:|---:|
| Champions | 704 | 16.23% | 64.32% |
| At-Risk / Inactive | 1,564 | 36.06% | 6.41% |
| Established Customers | 1,174 | 27.07% | 24.36% |
| Recent Occasional Buyers | 895 | 20.64% | 4.92% |
| **Total** | **4,337** | **100%** | **≈100%** |

Revenue shares refer to revenue associated with identified customers in the segmentation dataset, not necessarily all cleaned retail transactions.

Percentages may differ slightly from 100% because of rounding.

These segments describe historical purchasing patterns. They are not verified predictions of future customer behaviour.

In particular, the label **At-Risk / Inactive** does not establish that a customer will stop purchasing.

---

## 6. Key Findings

### 6.1 Sales Performance

The cleaned sales dataset contains **524,878 valid transaction rows**.

| Metric | Value |
|---|---:|
| Total revenue | £10,642,110.80 |
| Unique orders | 19,960 |
| UK revenue | £9,001,744.09 |
| International revenue | £1,640,366.71 |

The UK contributed the majority of recorded revenue, highlighting its importance to the retailer's historical sales performance.

### 6.2 Customer Behaviour

The customer intelligence dataset contains **4,337 identified customers**.

These comprise:

- **2,844 repeat customers**
- **1,493 one-time customers**

The analysis also identified a weak positive association between purchase frequency and average order value.

### 6.3 Geographical Differences

International orders had higher average and median invoice values than UK orders in the analysed dataset.

Further investigation would be required to understand whether product mix, order quantities or customer characteristics explain the differences.

### 6.4 Revenue Concentration

Champions represented approximately **16.23% of identified customers** but contributed **64.32% of identified-customer revenue**.

This indicates substantial historical revenue concentration within a relatively small customer group.

However, historical revenue contribution does not guarantee future customer value.

---

## 7. Business Recommendations

| Customer Group or Finding | Recommended Strategy |
|---|---|
| Champions | Explore loyalty, recognition and personalised retention initiatives |
| At-Risk / Inactive | Investigate inactivity and test targeted re-engagement campaigns |
| Established Customers | Encourage repeat purchasing through relevant offers and loyalty initiatives |
| Recent Occasional Buyers | Develop onboarding, follow-up and second-purchase engagement strategies |
| International orders | Investigate product mix, basket size and market economics |
| Purchase frequency | Avoid using frequency alone to estimate average order value |

These recommendations are exploratory.

Their effectiveness should be validated through customer research, controlled experiments and business performance monitoring before large-scale implementation.

Any commercial use should also consider applicable privacy and marketing requirements.

---

## 8. Communicating Insights to Different Audiences

The project communicates analytical findings to both technical and non-technical audiences.

Technical audiences require information about methodology, statistical tests, model evaluation and analytical limitations.

Non-technical audiences require clear explanations of business performance, customer behaviour and recommended actions.

### Example 1: Customer Segmentation

**Technical Interpretation:**

K-Means clustering was applied to transformed and standardised RFM features.

Four customer segments were selected provisionally, despite the two-cluster solution achieving a higher sampled Silhouette Score.

The Champions segment contains 704 customers, representing 16.23% of identified customers and 64.32% of identified-customer revenue.

**Business Interpretation:**

Approximately 16% of identified customers generated 64% of revenue associated with identified customers.

This suggests that a relatively small customer group was particularly important to historical sales.

The business could investigate loyalty initiatives to maintain engagement with these customers.

### Example 2: Purchase Frequency and Order Value

**Technical Interpretation:**

Spearman's rank correlation identified a statistically significant but weak positive association between purchase frequency and average order value (ρ = 0.1563, p < 0.001).

**Business Interpretation:**

Customers who purchased more frequently tended to have slightly higher average order values.

However, the relationship was weak, meaning purchase frequency alone is not a reliable indicator of average order value.

### Example 3: UK and International Sales

**Technical Interpretation:**

Welch's t-test and the Mann–Whitney U test identified statistically significant differences between UK and international invoice-level order values.

The average UK order value was £499.57, compared with £849.44 for international orders.

**Business Interpretation:**

International orders had a higher average value than UK orders in the historical dataset.

The business could investigate whether product mix, order quantities or customer composition explain these differences before making commercial decisions.

### Communication Strategy

The project uses:

- Jupyter notebooks for technical explanations, code and model evaluation.
- Charts to communicate trends, distributions and comparisons.
- The README to summarise findings and business implications.
- Tableau to present business intelligence visualisations.

Technical results are accompanied by plain-language interpretations to support understanding across different audiences.

---

## 9. Data Visualisation and Storytelling

### Purpose

Data visualisation helps simplify complex retail information and communicate findings to business stakeholders.

Visualisations are selected according to the analytical question, data characteristics and intended audience.

### Visualisation Methods

| Visualisation | Purpose | Business Value |
|---|---|---|
| Line charts | Examine sales trends over time | Identify changes in revenue performance |
| Bar charts | Compare geographical markets and customer groups | Highlight differences in business performance |
| Histograms | Examine spending distributions | Understand variation and unusual values |
| Box plots | Compare distributions and identify outliers | Support statistical interpretation |
| Scatter plots | Explore relationships between numerical variables | Investigate customer behaviour |
| Customer segment charts | Compare customer counts and revenue contributions | Support customer engagement strategies |

These visualisation types are used or considered within the analytical workflow. Not every chart type is claimed to be present in the published Tableau story.

### Data Storytelling Approach

The project follows a structured narrative:

1. **Business Context:** Explain the retail problem and objectives.
2. **Sales Performance:** Present revenue and geographical purchasing patterns.
3. **Customer Behaviour:** Investigate spending, frequency and order values.
4. **Statistical Evidence:** Explain hypothesis testing results.
5. **Customer Segmentation:** Present the four RFM-based customer groups.
6. **Business Recommendations:** Translate findings into potential actions.

### Accessibility and Clarity

The visualisation approach aims to use:

- Descriptive chart titles.
- Clearly labelled axes.
- Readable legends and number formats.
- Appropriate chart types.
- Plain-language explanations.
- Consistent terminology.
- Clear distinctions between observations and recommendations.

The published dashboard still requires a final accessibility and usability review.

---

## 10. Tableau Business Intelligence Dashboard

A Tableau Public visualisation has been published as part of the project.

**[View the Online Retail Intelligence — Business Insights Story](https://public.tableau.com/app/profile/oluwaseun.olasupo/viz/OnlineRetailIntelligenceSalesCustomerAnalytics/OnlineRetailIntelligence-BusinessInsightsStory)**

The published visualisation provides an initial platform for communicating retail analytics findings.

### Future Dashboard Development

Planned enhancements include:

- Integrating the four K-Means customer segments.
- Expanding customer intelligence visualisations.
- Improving interactive filtering and navigation.
- Refining chart titles, legends and tooltips.
- Improving dashboard layout and accessibility.
- Testing usability with intended users.

Before final assessment, the dashboard should be checked for:

- At least two distinct and relevant chart types.
- Accurate metrics.
- Clear chart titles and labels.
- Intuitive navigation.
- Functional interactions.
- Readability on common screen sizes.

The current published version is treated as an existing visualisation rather than a fully tested final dashboard.

---

## 11. Technologies and Tools

| Technology | Purpose |
|---|---|
| Python | Data preparation, analysis and machine learning |
| Pandas | Data manipulation and aggregation |
| NumPy | Numerical operations |
| Matplotlib | Data visualisation |
| Seaborn | Statistical visualisation |
| SciPy | Statistical hypothesis testing |
| Scikit-learn | Feature transformation, K-Means clustering and model evaluation |
| Jupyter Notebook | Documenting and executing analytical workflows |
| Tableau Public | Business intelligence and visual storytelling |
| Git and GitHub | Version control and project sharing |
| Visual Studio Code | Development environment |

---

## 12. Project Structure and Documentation

### Repository Structure

```text
Online-Retail-Intelligence-Capstone/
├── .github/
├── data/
│   └── tableau/
│       ├── retail_sales_tableau.csv
│       ├── retail_customer_intelligence.csv
│       └── retail_customer_segments.csv
├── jupyter_notebooks/
│   ├── 01_data_collection.ipynb
│   ├── 02_data_cleaning.ipynb
│   ├── 03_exploratory_data_analysis.ipynb
│   ├── 04_statistical_hypothesis_testing.ipynb
│   └── 05_customer_segmentation.ipynb
├── .gitignore
├── LICENSE
├── README.md
└── requirements.txt
```

The structure describes the intended working layout. Generated data files may be excluded from Git depending on the repository configuration.

### Documentation Approach

The README explains the project's objectives, methodology, findings, limitations and development status.

Jupyter notebooks document the technical workflow, including Python code, analytical explanations, statistical methods and machine learning.

### Notebook Guide

| Notebook | Purpose |
|---|---|
| 01_data_collection.ipynb | Import and inspect the original retail dataset |
| 02_data_cleaning.ipynb | Clean, validate and prepare transaction data |
| 03_exploratory_data_analysis.ipynb | Explore sales and customer purchasing patterns |
| 04_statistical_hypothesis_testing.ipynb | Test hypotheses and interpret statistical findings |
| 05_customer_segmentation.ipynb | Perform RFM analysis and K-Means customer segmentation |

The notebooks are numbered to indicate the recommended execution order.

### Documentation Standards

The project aims to use:

- Descriptive variable and function names.
- Markdown headings to organise analytical stages.
- Explanations of statistical and machine learning methods.
- Comments where additional explanation is needed.
- Visualisations and outputs to support interpretation.
- Documented assumptions and limitations.

Code readability, notebook execution and documentation consistency will be reviewed during final validation.

---

## 13. Running the Project Locally

### Prerequisites

- Python 3.12 or a compatible Python version.
- Git.
- Visual Studio Code or Jupyter Notebook.

### Clone the Repository

```bash
git clone https://github.com/SeunJoy/Online-Retail-Intelligence-Capstone.git
cd Online-Retail-Intelligence-Capstone
```

### Create a Virtual Environment

```bash
python -m venv .venv
```

Activate the environment on Windows PowerShell:

```powershell
.venv\Scripts\Activate.ps1
```

For macOS or Linux:

```bash
source .venv/bin/activate
```

### Install Dependencies

```bash
python -m pip install -r requirements.txt
```

### Obtain the Dataset

Download the dataset from:

https://www.kaggle.com/datasets/abhishekrp1517/online-retail-transactions-dataset

Place the dataset at the input location expected by `01_data_collection.ipynb`.

Check the notebook's file paths and filenames before execution.

### Run the Notebooks

Open the project in Visual Studio Code or Jupyter Notebook.

Select the project's Python environment and execute the notebooks in numerical order.

### Reproducibility Note

A fresh repository clone may not include the original dataset or generated CSV outputs.

A complete end-to-end execution check is still required to confirm that the installation instructions and analytical workflow work correctly in a clean environment.

---

## 14. Data Ethics, Privacy and Governance

### 14.1 Ethical Considerations

This project analyses historical retail transactions to understand purchasing behaviour and identify customer segments.

Customer-level data requires responsible handling because purchasing patterns may reveal information about individuals.

The project considers privacy, fairness, bias, transparency and responsible interpretation.

### 14.2 Customer Privacy

The dataset includes `CustomerID` values that allow transactions to be associated with individual customers.

Although these identifiers do not directly provide names, they may still create privacy risks when combined with other information.

The project uses customer identifiers for analytical aggregation and segmentation.

It does not attempt to identify individuals or combine the dataset with external personal information.

### 14.3 Bias and Fairness

The dataset represents historical transactions from a UK-based retailer and may not reflect current retail behaviour.

Missing customer identifiers may introduce selection bias because some transactions cannot be included in customer-level analysis.

K-Means clustering also depends on feature selection, scaling and the number of clusters.

Customer segment labels are analytical descriptions rather than definitive judgements about individuals.

Businesses should avoid using these labels to unfairly exclude customers or make consequential decisions without further investigation.

### 14.4 Legal and Regulatory Considerations

The project considers the UK General Data Protection Regulation (UK GDPR) and the Data Protection Act 2018.

Customer identifiers may constitute personal data where individuals can be identified using other reasonably available information.

Pseudonymised data is not automatically anonymous.

For real-world deployment, important data protection principles include:

- Lawfulness, fairness and transparency.
- Purpose limitation.
- Data minimisation.
- Accuracy.
- Storage limitation.
- Integrity and confidentiality.
- Accountability.

A business implementing this analysis would need to establish an appropriate lawful basis and assess its applicable legal obligations.

This educational project does not independently establish compliance for commercial deployment.

### 14.5 Customer Profiling

RFM analysis and K-Means clustering classify customers according to historical purchasing behaviour.

In a real business environment, this may constitute profiling where personal data is processed to evaluate individual behaviour.

Responsible use should include:

- Treating segment labels as exploratory indicators.
- Avoiding consequential decisions based solely on cluster labels.
- Providing appropriate transparency.
- Considering applicable customer rights.
- Assessing whether a Data Protection Impact Assessment is required.
- Applying additional safeguards where legally significant automated decisions are involved.

### 14.6 Social Implications

Customer analytics can improve shopping experiences through relevant recommendations and more effective customer service.

However, prioritising high-spending customers may cause businesses to overlook customers with lower purchasing power.

Historical data may also reinforce existing inequalities if customer segments are treated as permanent classifications.

Responsible analytics requires fairness, transparency and consideration of customer trust.

### 14.7 Data Governance

The project supports data governance through:

- Organised analytical notebooks.
- Documented data cleaning.
- Consistent analytical methods.
- Data validation.
- Git version control.
- Separation of transaction-level and customer-level analysis.
- Documentation of assumptions and limitations.

Production deployment would require additional access controls, secure storage, retention policies and organisational responsibilities.

### 14.8 Responsible Interpretation

Statistical significance does not establish causation.

Customer segments describe historical patterns rather than verified future outcomes.

Business recommendations should be tested before implementation.

The project aims to communicate uncertainty, acknowledge limitations and avoid overstating analytical findings.

---

## 15. Project Lifecycle and Implementation Plan

### Project Management Approach

The project follows a phased development approach.

Each phase has defined objectives, deliverables and evaluation activities.

Git and GitHub support version control, Jupyter notebooks document analytical development, and Tableau supports business intelligence visualisation.

### Project Phases and Milestones

| Phase | Deliverable | Status |
|---|---|---|
| 1. Planning | Business problem, objectives and audience | Completed |
| 2. Data Collection | Initial dataset assessment | Completed |
| 3. Data Preparation | Cleaned analytical data | Completed |
| 4. Exploratory Analysis | EDA notebook and charts | Completed |
| 5. Statistical Analysis | Hypothesis testing results | Completed |
| 6. Machine Learning | RFM-based customer segmentation | Completed |
| 7. Visualisation | Initial Tableau story | Published |
| 8. Documentation | README and notebook explanations | Updated; final audit pending |
| 9. Technical Testing | Notebook execution and metric validation | Pending final verification |
| 10. Dashboard Testing | Usability, accessibility and interactions | Pending |
| 11. Deployment Review | Repository and published output checks | Pending |
| 12. Maintenance and Evaluation | Future updates and business validation | Planned |

### Implementation Strategy

The analytical workflow begins with data collection and cleaning, followed by exploratory analysis, hypothesis testing and customer segmentation.

Each stage should be validated before its outputs are used in subsequent stages.

Processed datasets support downstream reporting and visualisation.

### Testing and Quality Assurance

The project will undergo final validation to confirm that:

- Notebooks execute without unresolved errors.
- Data cleaning produces consistent results.
- Revenue and customer metrics are accurate.
- Statistical methods and assumptions are appropriate.
- Machine learning outputs are reproducible.
- Charts display correct values and labels.
- Dashboard links and interactions function.
- Documentation matches the implemented project.
- Assessment requirements have supporting evidence.

### Quality Assurance Checklist

- [ ] Run all notebooks in a clean environment.
- [ ] Verify sales totals and customer counts.
- [ ] Confirm statistical test results.
- [ ] Recheck segmentation counts and model metrics.
- [ ] Verify required files in GitHub.
- [ ] Test the Tableau dashboard.
- [ ] Review accessibility and usability.
- [ ] Confirm that README statements match the final implementation.

### Deployment Plan

The project is hosted in a GitHub repository.

A Tableau Public story has also been published.

Before final submission, the repository structure, required files, installation instructions, dashboard link and documentation should be checked.

### Maintenance and Update Plan

Future maintenance will focus on:

- Reviewing Python package compatibility.
- Updating documentation when code changes.
- Checking external links.
- Monitoring data quality.
- Reviewing analytical assumptions.
- Reassessing customer segments when appropriate.
- Recording improvements through Git commits.

### Evaluation Strategy

**Technical Evaluation:**

- Successful notebook execution.
- Accuracy of analytical outputs.
- Appropriate statistical methods.
- Machine learning evaluation metrics.
- Reproducibility.

**Business Evaluation:**

- Relevance of findings.
- Clarity of customer segmentation.
- Usefulness of recommendations.
- Accessibility of explanations.

**User Experience Evaluation:**

- Dashboard navigation.
- Chart readability.
- Interactivity.
- Accessibility.
- Feedback from intended users.

### Risks and Mitigation

| Risk | Mitigation |
|---|---|
| Missing or invalid data | Apply documented cleaning and validation |
| Statistical misinterpretation | Report assumptions, effect sizes and limitations |
| Unstable customer segments | Compare models and evaluate stability |
| Dashboard usability issues | Conduct usability and accessibility testing |
| Dependency problems | Document and test the Python environment |
| Privacy risks | Apply data minimisation and appropriate safeguards |
| Incomplete documentation | Conduct a final README and notebook audit |

---

## 16. Limitations and Future Improvements

### Project Limitations

**Historical Data:** The dataset covers 2010–2011 and may not reflect current consumer behaviour.

**Missing Customer Identifiers:** Some transactions cannot be attributed to individual customers.

**Outliers and Skewness:** Retail spending data contains extreme values that may affect statistical summaries and clustering.

**Observational Analysis:** Statistical associations do not establish causality.

**Clustering Assumptions:** K-Means is sensitive to feature selection, scaling and the number of clusters.

**Model Selection:** The four-cluster solution did not achieve the highest sampled Silhouette Score.

**Business Validation:** Recommended marketing interventions have not been evaluated through controlled experiments.

**Dashboard Development:** Additional Tableau improvements and usability testing remain outstanding.

### Future Improvements

Future work could include:

1. Comparing K-Means with alternative clustering methods.
2. Evaluating customer segment stability.
3. Incorporating additional behavioural variables.
4. Exploring predictive models using appropriate labelled data.
5. Testing marketing strategies through controlled experiments.
6. Integrating customer segments into Tableau.
7. Improving dashboard accessibility and navigation.
8. Strengthening automated validation and reproducibility.

These are proposed improvements rather than completed project features.

---

## 17. Learning Reflection

Developing this capstone strengthened my practical understanding of data analytics, statistical analysis, machine learning and business intelligence.

One of the main challenges was cleaning the retail dataset and ensuring that the analytical results were based on reliable records. This required careful examination of missing values, invalid transactions and unusual observations.

Selecting and applying appropriate Python code was another challenge. Working through errors and validating analytical outputs improved my debugging, problem-solving and programming skills.

Statistical hypothesis testing helped me understand the importance of distinguishing statistical significance from practical business relevance.

Customer segmentation demonstrated that statistical performance and business interpretability do not always lead to the same modelling decision.

Developing the initial Tableau story also reinforced the importance of clear visual communication and highlighted areas for future improvement.

Overall, the project improved my technical confidence, critical thinking and ability to connect analytical methods with practical business questions.

One of my most important lessons is that useful analysis must be accurate, explainable, reproducible and transparent about its limitations.

---

## 18. Acknowledgements

I would like to express my sincere appreciation to **Idir** and **Vasi** for their guidance, encouragement and patience throughout my learning journey at **Code Institute**.

Their willingness to share their knowledge, explain difficult concepts and provide support has contributed significantly to my development in data analytics.

I am **especially grateful to Emma, our course facilitator at Code Institute**, for her exceptional patience, encouragement and consistent support.

Her willingness to take time to explain concepts, help me work through challenges and support my learning has made a meaningful difference to my confidence and understanding.

I deeply appreciate her dedication and the positive contribution she has made to my growth in data analytics and artificial intelligence.

I am grateful to all three for their support and for helping me develop the knowledge and confidence to undertake this capstone project.

---

## 19. AI Assistance Disclosure

Artificial intelligence tools were used as learning and problem-solving aids during the development of this project.

AI assistance helped me:

- Clarify unfamiliar data analytics and programming concepts.
- Understand Python errors and explore troubleshooting approaches.
- Interpret statistical and machine learning concepts.
- Explore possible solutions when I encountered technical challenges.
- Improve the clarity and organisation of project documentation.
- Review explanations and communicate analytical findings more effectively.

AI-generated suggestions were treated as guidance rather than unquestioned answers.

The analytical methods, interpretations and project outputs remain subject to my own review and verification against the dataset and executable notebooks.

The use of AI supported my learning and problem-solving process; it does not replace evidence of working code, correct calculations, reproducibility or independent understanding.

---

## 20. Project Links, Author and Licence

### Project Links

**GitHub Repository:**

[Online Retail Intelligence Capstone](https://github.com/SeunJoy/Online-Retail-Intelligence-Capstone)

**Tableau Public Dashboard:**

[Online Retail Intelligence — Business Insights Story](https://public.tableau.com/app/profile/oluwaseun.olasupo/viz/OnlineRetailIntelligenceSalesCustomerAnalytics/OnlineRetailIntelligence-BusinessInsightsStory)

**Dataset Source:**

[Online Retail Transactions Dataset — Kaggle](https://www.kaggle.com/datasets/abhishekrp1517/online-retail-transactions-dataset)

### Author

**Oluwaseun Olasupo**

Data Analytics and Artificial Intelligence Capstone Project

**Code Institute**

### Licence

Refer to the repository's `LICENSE` file for the applicable project licence terms.

Dataset reuse is governed separately by the terms associated with its original source.

### Final Project Status

Core Python analytics, statistical hypothesis testing and exploratory customer segmentation have been completed.

An initial Tableau Public story has been published.

Final technical validation, dashboard usability evaluation and planned visualisation enhancements remain outstanding.
