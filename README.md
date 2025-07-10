# Customer Segmentation using Clustering

This project performs customer segmentation using clustering techniques based on behavioral transaction data. It helps businesses understand customer purchasing behavior, categorize customers, and target them with personalized marketing strategies.

---

##  Dataset Overview

The dataset is synthetically generated and includes 5000 transactions for 500 customers across 2 years (2022–2023). Each transaction contains:

- `TransactionID`: Unique identifier for each transaction
- `CustomerID`: Unique customer identifier
- `TransactionDate`: Date of purchase
- `ProductID`: Purchased product
- `Quantity`: Number of units bought
- `UnitPrice`: Price per unit
- `TotalPrice`: Total amount spent (`Quantity × UnitPrice`)

---

##  Project Workflow & Analysis

### 1. ** Data Generation**
- A synthetic dataset was created using NumPy and Python's `datetime` to simulate realistic purchase behavior.
- Customer profiles were generated with different spending capacities and frequencies.

### 2. ** Data Cleaning**
- Transaction data was stored in a Pandas DataFrame.
- `TransactionDate` column was converted to `datetime` format.
- `TotalPrice` column was computed as `Quantity × UnitPrice`.
- (Note: As this is synthetic data, no missing values or outliers were present.)

### 3. ** RFM Feature Engineering**
We computed three key behavioral metrics per customer:

- **Recency (R)**: Days since the customer's most recent transaction.
- **Frequency (F)**: Total number of transactions by the customer.
- **Monetary (M)**: Total amount spent by the customer.

These metrics were aggregated at the `CustomerID` level using groupby and aggregation.

### 4. ** Exploratory Data Analysis (EDA)**
- Histograms were plotted to visualize distributions of Recency, Frequency, and Monetary values.
- All RFM features showed **right-skewed** distributions typical in transaction data.
- Log transformation (`np.log1p`) was applied to normalize skewness.

### 5. ** Feature Scaling**
- After transformation, features were standardized using `StandardScaler` to ensure equal contribution to the clustering algorithm.

### 6. ** Clustering**
- **K-Means Clustering** was used for segmentation.
- The optimal number of clusters (`k`) was determined using:
  - **Elbow Method**
  - **Silhouette Score**

- Final model trained with the optimal `k`, and customer segments were labeled accordingly.

### 7. ** PCA & Visualization**
- Principal Component Analysis (PCA) was applied to reduce RFM feature space to 2D for visualization.
- Scatter plot of customer clusters was generated to observe separation in customer behavior.

---

##  Output Summary

- Each customer was assigned to a segment based on RFM behavior.
- Clear differences were observed between customer groups:
  - High spenders with frequent purchases
  - Infrequent, low-spending customers
  - Recently active but low-frequency buyers
- Clusters can be used for:
  - Targeted promotions
  - Loyalty programs
  - Churn prevention campaigns


