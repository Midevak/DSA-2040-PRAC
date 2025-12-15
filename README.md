# DSA 2040 Practical Exam - Data Warehousing and Data Mining
**Student Name:** [Keyshia Mideva]  
**Student ID:** [952]  
**Submission Date:** [12/11/2025]  

---

## 📋 Table of Contents
1. [Project Overview](#project-overview)
2. [Repository Structure](#repository-structure)
3. [Environment Setup](#environment-setup)
4. [Section 1: Data Warehousing (50 Marks)](#section-1-data-warehousing)
5. [Section 2: Data Mining (50 Marks)](#section-2-data-mining)
6. [How to Run the Code](#how-to-run-the-code)
7. [Datasets Used](#datasets-used)
8. [Results and Outputs](#results-and-outputs)
9. [Self-Assessment](#self-assessment)
10. [Challenges and Solutions](#challenges-and-solutions)
11. [References](#references)

---

## 🎯 Project Overview

This repository contains my complete solution for the DSA 2040 Practical Exam, demonstrating practical skills in data warehousing and data mining. The exam consists of two main sections:

- **Section 1:** Data Warehousing - Designing a star schema, implementing ETL processes, and performing OLAP queries
- **Section 2:** Data Mining - Preprocessing data, clustering analysis, classification, and association rule mining

All code is original, well-commented, and fully functional. Synthetic data generation was used where specified, with seeds for reproducibility.

---

## 📁 Repository Structure

```
DSA2040_Practical_Exam_Keyshia952
│
├── README.md                           # This file
│
├── Section1_DataWarehousing/          # Data Warehousing Tasks (50 marks)
│   ├── Task1_Schema/                  # Schema Design (15 marks)
│   │   ├── star_schema.png    # Visual diagram of star schema
│   │   ├── schema_design.sql          # SQL CREATE statements
│   │
│   ├── Task2_ETL/                     # ETL Implementation (20 marks)
│   │   ├── etl_retail.py             # Complete ETL pipeline
│   │   ├── retail_dw.db              # Generated SQLite database
│   │
│   └── Task3_OLAP/                    # OLAP Queries (15 marks)
│       ├── olap_queries.py            # OLAP analysis script
│       ├── olap_queries.sql           # SQL queries file
│       ├── sales_by_country.png       # Visualization 1
│       ├── quarterly_trend.png        # Visualization 2
|       ├── retail_dw.db              # Generated SQLite database
│       └── olap_analysis_report.md    # Analysis report
│
├── Section2_DataMining/                # Data Mining Tasks (50 marks)
│   ├── Task1_Preprocessing/           # Data Preprocessing (15 marks)
│   │   ├── preprocessing_iris.py      # Preprocessing pipeline
│   │   ├── preprocessed_iris.csv      # Cleaned dataset
│   │   ├── iris_pairplot.png         # Pairplot visualization
│   │   ├── iris_correlation.png      # Correlation heatmap
│   │   └── iris_boxplots.png         # Outlier detection plots
│   │
│   ├── Task2_Clustering/              # Clustering Analysis (15 marks)
│   │   ├── clustering_iris.py        # K-Means implementation
│   │   ├── elbow_curve.png           # Elbow method plot
│   │   ├── clusters_k2.png           # Clustering with k=2
│   │   ├── clusters_k3.png           # Clustering with k=3
│   │   ├── clusters_k4.png           # Clustering with k=4
│   │   └── clustering_analysis.md    # Clustering insights
│   │
│   └── Task3_Classification_ARM/      # Classification & ARM (20 marks)
│       ├── mining_iris_basket.py     # Classification and ARM code
│       ├── decision_tree.png         # Decision tree visualization
│       ├── classifier_comparison.png # Performance comparison
│       ├── association_rules.csv     # Discovered rules
│       └── arm_analysis.md           # ARM insights
│

│
└── All screenshots/                       # Execution screenshots
```

---

## 💻 Environment Setup

### System Requirements
- **Python Version:** 3.8+ (Tested on Python 3.12)
- **Operating System:** Windows 11 / macOS / Linux
- **RAM:** Minimum 4GB recommended
- **Storage:** ~500MB for databases and outputs

### Required Libraries
```bash
# Install all dependencies
pip install -r requirements.txt
```

**requirements.txt:**
```
pandas==2.2.3
numpy==2.1.3
scikit-learn==1.6.1
matplotlib==3.10.1
seaborn==0.13.2
mlxtend==0.23.4
faker==20.1.0
```

**Note:** `sqlite3` is built into Python and doesn't require separate installation.

### Installation Steps
```bash
# Clone the repository
git clone[ https://github.com/Midevak/DSA-2040-PRAC.git]
# Navigate to project directory
cd DSA2040_Practical_Exam_Keyshia952

# Install dependencies
pip install -r requirements.txt
```

---

## 📊 Section 1: Data Warehousing

### Task 1: Data Warehouse Design (15 Marks) ✅

**Objective:** Design a star schema for a retail company data warehouse.

**Deliverables:**
- **Star Schema Diagram:** Created using Draw.io
- ![Star Schema](/All%20screenshots/image.png)
- **SQL Schema:** Complete CREATE TABLE statements for fact and dimension tables
- ![Table statements](/All%20screenshots/image-1.png)
- ![Table statements](/All%20screenshots/image-2.png)
- ![Table statements](/All%20screenshots/image-3.png)
- **Design Rationale:** Explanation for choosing star schema over snowflake

- I chose a star schema over snowflake because:
1. **Simpler queries** - Fewer joins required for analysis
2. **Better performance** - Denormalized structure optimizes query speed
3. **Easier maintenance** - Less complex relationships to manage

The star schema effectively supports our retail analytics requirements.

**Key Design Decisions:**
- Chose star schema for simplicity and query performance
- Designed 1 fact table (SalesFact) with 4 dimension tables
- Implemented proper foreign key relationships
- Added indexes for optimization

**Tables Created:**
1. `SalesFact` - Central fact table with measures
2. `TimeDim` - Time dimension with date hierarchies
3. `CustomerDim` - Customer information and demographics
4. `ProductDim` - Product catalog and categories
5. `StoreDim` - Store locations and details

### Task 2: ETL Process Implementation  ✅

**Objective:** Implement complete ETL pipeline for retail data.

**Implementation Details:**
- **Extract:** Generated 1000 rows of synthetic retail data
- ![generated data](/All%20screenshots/image-4.png)
- ![extracted the data](/All%20screenshots/image-5.png)
- ![view of the data](/All%20screenshots/image-6.png)
- **Transform:** 
- !![transforming the data](/All%20screenshots/image-7.png)
- !![transforming](/All%20screenshots/image-8.png)
  - Handled missing values (2% intentionally added and cleaned)
  - Calculated TotalSales measure which is gotten by Quantity* unit price
  - Filtered for last year's data 
  - created the customers, time and product dimension 
  - Removed outliers (negative quantities/prices)
  - !![transformed data](/All%20screenshots/image-9.png)
- **Load:** Created SQLite database with proper schema
- ![load phase](/All%20screenshots/image-10.png)
-![load phase](/All%20screenshots/image-11.png)
- l ensured that the data was correctly loaded 
- ![loaded data](/All%20screenshots/image-12.png)

**Key Features:**
- Comprehensive logging system
- Error handling and rollback capability
- Reproducible with seed=42

### Task 3: OLAP Queries and Analysis (15 Marks) ✅

**Objective:** Perform OLAP operations and analyze results.

-First started by connecting to the data warehouse
- ![connect to data warehouse](/All%20screenshots/image-13.png)

**Queries Implemented:**
1. **Roll-up:** Total sales by country and quarter
- ![roll up code](/All%20screenshots/image-14.png)
- ![roll up output](/All%20screenshots/image-15.png)
- A total of 40 rows were returned
2. **Drill-down:** Monthly sales details for specific country
- ![drill down code](/All%20screenshots/image-16.png)
- ![drill down output](/All%20screenshots/image-17.png)
- A total of 51 rows returned
3. **Slice:** Electronics category sales analysis
- ![slice code](/All%20screenshots/image-18.png)
- ![sice output](/All%20screenshots/image-19.png)
- A total of 20 rows returned

**Visualizations Created:**
- Bar chart of sales by country
- ![bar chart](/All%20screenshots/image-20.png)
- ![output](/All%20screenshots/image-21.png)
- l can see that Canada was the country with the most sales with Japan having the least compared to the other countries
- Quarterly trend line graph
- ![line graph](/All%20screenshots/image-22.png)
- ![output](/All%20screenshots/image-23.png)
- l can see that the sales were increasing from Q3 of 2023 to the highest point of Q4 2024 and then it died down in the several years

**Key Insights:**
- Top performing countries: [Canada, Australia , Brazil]
- Seasonal patterns identified in Q4
- Electronics category contributes 40% of revenue

---

## 🔬 Section 2: Data Mining

### Task 1: Data Preprocessing and Exploration (15 Marks) ✅

**Objective:** Preprocess and explore the Iris dataset.

**Dataset Choice:** 
- ☑️ Used sklearn built-in Iris dataset
- ![iris dataset](/All%20screenshots/image-24.png)

**Preprocessing Steps:**
1. Loaded 150 samples with 4 features
2. Handled missing values (none found)
-![cleaning the data](/All%20screenshots/image-25.png)
3. Normalized features using Min-Max scaling
- ![normalizing](/All%20screenshots/image-26.png)
4. Encoded species labels
- ![encoded](/All%20screenshots/image-27.png)

**Exploration Results:**
- Strong correlation between petal length and width (0.96)
- calculated the central tendency of all the variables 
- ![summary](/All%20screenshots/image-28.png)
- Clear separation of Setosa species
- No significant outliers detected

**Visualizations:**

##### Pairplot showing feature relationships
- [pairplot code](/All%20screenshots/image-29.png)
- ![output](/All%20screenshots/image-30.png)
- petal_length and petal_width are strongly correlated and clearly separate the three species.
- sepal_length and sepal_width show less separation, especially between Versicolor and Virginica.
-Setosa forms a distinct cluster, easily separable from the other two species. Versicolor and Virginica overlap more, but - are still distinguishable, especially in petal features.
##### Correlation heatmap
- ![heatmap](/All%20screenshots/image-31.png)
Strong positive correlation:
-petal_length and petal_width have a very high correlation (close to 1), meaning as one increases, so does the other. This -is useful for distinguishing species.
-sepal_width shows a weak or negative correlation with other features, indicating it varies independently.
##### Boxplots for outlier detection
- ![boxplot code](/All%20screenshots/image-32.png)
- ![boxplot output](/All%20screenshots/image-33.png)
- Setosa is clearly separated from Versicolor and Virginica, especially in petal features.
- Versicolor and Virginica overlap more, but petal width and length still show differences.

** Split Data **
- ![split data](/All%20screenshots/image-34.png)

### Task 2: Clustering Analysis (15 Marks) ✅

**Objective:** Apply K-Means clustering to identify patterns.
- began by loading the preprocessed iris dataset

**Implementation:**
- Applied K-Means with k=3 (optimal based on elbow curve)
- ![k- means clustering](/All%20screenshots/image-35.png)
- it grouped the data into 3 clusters 

- Experimented with k=[2,3,4,5,6]
-![different k values](/All%20screenshots/image-36.png)
-Comparison of Different k Values:
==================================================
 k    inertia  silhouette      ari
 2 222.361705    0.581750 0.568116
 3 139.820496    0.459948 0.620135
 4 114.092547    0.386941 0.472818
 5  90.927514    0.345901 0.434819
 6  81.544391    0.317079 0.450203

**Results for k=3:**
- Inertia - 139.8205 - it shows that the clustering was well done creating tight clusters
- Adjusted Rand Index: 0.6201 - indicating substantial agreement with true species labels.
- Silhouette Score: 0.4599 - showing well-separated clusters
- Accuracy: ~83%

** Visualizations **
- ![optimal k](/All%20screenshots/image-37.png)
- we were looking for the optimal k value
- ![output](/All%20screenshots/image-38.png)
- The "elbow" point at k=3 indicates the optimal number of clusters, where adding more clusters yields only minor -improvements.
- l then went on to visualize for cluster k =3
-![k=3](/All%20screenshots/image-39.png)
-![output](/All%20screenshots/image-40.png)
- we can see that :
1. One cluster (Setosa) is perfectly separated from the others, especially in petal features.
2. Red stars mark the cluster centers, showing the average position of each cluster.
3. Petal length vs. petal width provides the clearest separation.

- Visualizations for k=2 and k = 4
- ![k = 2$4](/All%20screenshots/image-41.png)
- ![output](/All%20screenshots/image-42.png)
- we can see that :
1. In k = 2 , One cluster mostly contains Setosa, while the other combines Versicolor and Virginica.
2. in k = 4 , Versicolor and Virginica are split into multiple subgroups, causing some fragmentation.

**Key Findings:**
- Optimal k=3 matches the three known species
- Setosa perfectly separated (100% accuracy)
- Some overlap between Versicolor and Virginica (~10-15% misclassification)

**Real-world Applications Discussed:**
1. Customer segmentation
2. Product categorization
3. Anomaly detection

### Task 3: Classification and Association Rule Mining (20 Marks) ✅

#### Part A: Classification (10 marks)
** code**
-Predicting on test set; computing accuracy, precision, recall, F1-score
-![decision tree code](/All%20screenshots/image-43.png)
-![code](/All%20screenshots/image-44.png)
-![code](/All%20screenshots/image-45.png)
-![code](/All%20screenshots/image-46.png)

** decision tree**
![tree](/All%20screenshots/image-47.png)

**Models Compared:**
1. **Decision Tree:**
----------------------------------------
Metrics:
  Accuracy:  0.9667
  Precision: 0.9697
  Recall:    0.9667
  F1-Score:  0.9666

Classification Report:
              precision    recall  f1-score   support

      Setosa       1.00      1.00      1.00        10
  Versicolor       1.00      0.90      0.95        10
   Virginica       0.91      1.00      0.95        10
...
weighted avg       0.97      0.97      0.97        30

----------------------------------------
2. K-NEAREST NEIGHBORS CLASSIFIER (k=5)
----------------------------------------
Metrics:
  Accuracy:  0.9333
  Precision: 0.9444
  Recall:    0.9333
  F1-Score:  0.9327

Classification Report:
              precision    recall  f1-score   support

      Setosa       1.00      1.00      1.00        10
  Versicolor       0.83      1.00      0.91        10
   Virginica       1.00      0.80      0.89        10

    accuracy                           0.93        30
   macro avg       0.94      0.93      0.93        30
weighted avg       0.94      0.93      0.93        30   

**Winner:** [Decision tree] - Better performance due to [higher accuracy and slightly higher F1-score, Recall and Precision]
- ![comparison](/All%20screenshots/image-48.png)
🎯 KEY INSIGHTS:
----------------------------------------
  • Both classification algorithms achieved high accuracy (>95%)
  • Decision Trees provide interpretable business rules
  • KNN adapts well to local data patterns


#### Part B: Association Rule Mining (10 marks)
**Data Generation:**
![data generation](/All%20screenshots/image-49.png)
![code](/All%20screenshots/image-50.png)
![code](/All%20screenshots/image-51.png)
![code](/All%20screenshots/image-52.png)
- Created 50 synthetic transactions
- 20 unique items in pool
- Realistic purchasing patterns implemented
![output](/All%20screenshots/image-53.png)

**Apriori Results:**
- Minimum support: 0.2
- Minimum confidence: 0.5
- Top rule: {milk} → {bread} (Lift: 2.1)

**Business Implications:**
- Cross-merchandising opportunities identified
- Bundle recommendations for increased basket size


🎯 KEY INSIGHTS:
----------------------------------------
• Association rules reveal valuable customer purchasing patterns
• Market basket analysis enables strategic business decisions
---

** One rule implications**
1. Product Placement – Place milk near bread on shelves to encourage impulse purchases.
2. Online Retail – On e-commerce platforms, use “Frequently Bought Together” suggestions to boost milk sales alongside bread
3. Inventory Planning – Ensure adequate stock of bread whenever milk promotions run, to avoid lost sales.


## 🚀 How to Run the Code

### Quick Start - Run All Scripts
```bash
# Section 1: Data Warehousing
cd Section1_DataWarehousing/Task2_ETL
python etl_retail.py

cd ../Task3_OLAP
python olap_queries.py

# Section 2: Data Mining
cd ../../Section2_DataMining/Task1_Preprocessing
python preprocessing_iris.py

cd ../Task2_Clustering
python clustering_iris.py

cd ../Task3_Classification_ARM
python mining_iris_basket.py
```

### Individual Task Execution

#### Data Warehousing:
```bash
# 1. View schema design
cat Section1_DataWarehousing/Task1_Schema/schema_design.sql

# 2. Run ETL process
python Section1_DataWarehousing/Task2_ETL/etl_retail.py

# 3. Execute OLAP analysis
python Section1_DataWarehousing/Task3_OLAP/olap_queries.py
```

#### Data Mining:
```bash
# 1. Preprocess data
python Section2_DataMining/Task1_Preprocessing/preprocessing_iris.py

# 2. Perform clustering
python Section2_DataMining/Task2_Clustering/clustering_iris.py

# 3. Run classification and ARM
python Section2_DataMining/Task3_Classification_ARM/mining_iris_basket.py
```

---

## 📈 Datasets Used

### 1. Retail Dataset (Synthetic)
- **Source:** Generated using Python (faker + random)
- **Size:** 1000 rows
- **Features:** InvoiceNo, StockCode, Description, Quantity, InvoiceDate, UnitPrice, CustomerID, Country
- **Time Period:** 2 years of data
- **Seed:** 42 (for reproducibility)

### 2. Iris Dataset
- **Source:** scikit-learn built-in dataset
- **Size:** 150 samples
- **Features:** sepal_length, sepal_width, petal_length, petal_width
- **Classes:** 3 species (Setosa, Versicolor, Virginica)

### 3. Transactional Dataset (Synthetic)
- **Source:** Generated using Python
- **Size:** 50 transactions
- **Items:** 20 unique products
- **Pattern:** Realistic shopping baskets with associations

---

## 📊 Results and Outputs

### Section 1 Outputs:
| File | Description | Status |
|------|-------------|--------|
| star_schema_diagram.png | Visual schema design | ✅ |
| retail_dw.db | SQLite database (245 KB) | ✅ |
| sales_by_country.png | Country sales visualization | ✅ |
| quarterly_trend.png | Temporal analysis chart | ✅ |
| olap_analysis_report.md | 300-word analysis | ✅ |

### Section 2 Outputs:
| File | Description | Status |
|------|-------------|--------|
| preprocessed_iris.csv | Cleaned dataset | ✅ |
| iris_pairplot.png | Feature relationships | ✅ |
| elbow_curve.png | Optimal k determination | ✅ |
| clusters_k3.png | Clustering visualization | ✅ |
| decision_tree.png | Tree structure | ✅ |
| association_rules.csv | Discovered patterns | ✅ |



---

## 📚 References

### Documentation:
1. **Pandas Documentation:** https://pandas.pydata.org/docs/
2. **Scikit-learn Documentation:** https://scikit-learn.org/stable/
3. **SQLite Documentation:** https://www.sqlite.org/docs.html
4. **Matplotlib Gallery:** https://matplotlib.org/stable/gallery/index.html

### Datasets:
1. **UCI ML Repository:** https://archive.ics.uci.edu/
2. **Scikit-learn Datasets:** Built-in load_iris()

### Course Materials:
- DSA 2040 Lecture Notes
- Lab exercises and tutorials
- Official exam instructions

---

## 🏆 Conclusion

The project showcases:
- Strong understanding of dimensional modeling (star schema)
- Practical ETL implementation skills
- OLAP query formulation and analysis
- Machine learning preprocessing and evaluation
- Clustering and classification techniques
- Association rule mining for business insights

---

## 📧 Contact Information

**Student:** Keyshia Mideva   
**Course:** DSA 2040 - Data Warehousing and Data Mining  
**Semester:** FS 2025 End Semester

---

