![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/scikit--learn-%23F7931E.svg?style=for-the-badge&logo=scikit-learn&logoColor=white)
![Jupyter Notebook](https://img.shields.io/badge/jupyter-%23FA0F00.svg?style=for-the-badge&logo=jupyter&logoColor=white)



# IT Infrastructure Cost Optimization (ITFM)

### **Overview**
This project applies **Unsupervised Machine Learning** to IT Financial Management (ITFM). By clustering IT assets and department spending patterns, we identify "Ghost Resources" and "Inefficiency Clusters" that traditional rule-based reporting often misses.

### **The Problem**
Enterprise IT environments are often "black boxes." Departments over-provision cloud resources to avoid performance bottlenecks, leading to massive financial waste. 

### **The Solution (The Pipeline)**
1.  **Data Engineering:** Synthesis of a 30-feature dataset with intentional "dirty" data (outliers, missing values) to simulate real-world messiness.
2.  **Dimensionality Reduction:** Utilizing **PCA** to compress 30 variables into 3 Principal Components.
3.  **Clustering:** Applying **Agglomerative Clustering** to group assets by behavior rather than just cost.
4.  **Financial Impact:** Identifying clusters with <15% utilization but high spend.

### **Key Results**
* **Identified Annual Savings:** Over **$500,000** in recoverable OpEx.
* **Efficiency Gains:** 20% potential reduction in total IT overhead through "Right-Sizing."
* **Strategy:** Implementation of a "Tag-or-Terminate" policy for zombie assets.

## Technology Stack

* **Language:** Python 3.x
* **Data Manipulation:** `Pandas`, `NumPy` (Handling 2.5k+ infrastructure snapshots)
* **Machine Learning:** `Scikit-Learn`
    * **PCA:** Dimensionality reduction from 30+ features to 3 principal components.
    * **Agglomerative Clustering:** Hierarchical grouping for nested cost patterns.
* **Visualization:** `Matplotlib`, `Seaborn` (3D Projection and Variance plots)
* **Environment:** Jupyter Notebook / VS Code


## 📂 Project Structure
```text
├── data/
│   ├── itfm_raw_dirty_data.csv        # Simulated "messy" IT logs
│   └── itfm_cleaned_and_clustered.csv # Processed data with ML labels
├── images/                            # Plots and visualizations
├── itfm.ipynb                         # Main analysis notebook
├── requirements.txt                   # Dependency list
└── .gitignore                         # Metadata exclusion
```

### **How to Run**
1. Clone the repo.
2. Install dependencies: `pip install -r requirements.txt`
3. Open `itfm.ipynb` in Jupyter Notebook or VS Code.


## Data Visualizations & ML Pipeline

### Step 1: Data Engineering & Cleaning
The analysis transforms raw IT asset data into actionable business insights. The dataset simulates real-world messiness, including missing values, duplicates, and inconsistent formats across 30+ features. Automated cleaning pipelines handled nulls, standardized strings, and normalized numeric columns, ensuring metrics like `Monthly_Spend` and `Uptime_Percentage` were comparable and meaningful for analysis.

### Step 2: PCA & Dimensionality Reduction
To handle the "Curse of Dimensionality," the project employs Principal Component Analysis (PCA).

- Compression: 30+ infrastructure variables (CPU, RAM, Age, License Fees, etc.) are compressed into 3 Principal Components.
- Spatial Mapping: This allows us to map every IT asset into a 3D coordinate system, making hidden patterns visible to the human eye.

![3D Projection](images/3d_projection_it_data_pca.png)

### Step 2.1: Variance Analysis
Before clustering, we validate the PCA performance to ensure meaningful dimensionality reduction:

- Total Variance Explained: 17.61% (PC1: 6.44%, PC2: 5.68%, PC3: 5.49%), preserving the key patterns in server usage, cost, and efficiency.
- Information Retention: Analysis of the explained variance confirms that the three components capture the majority of the dataset’s signal, maintaining distinctions between efficient and wasteful assets.
- Elbow Plotting: Ensures dimensionality reduction simplifies the data without losing critical nuances, providing a reliable foundation for clustering and business insights.

![Variance Analysis](images/pca_information_distribution.png)

### Step 3: Clustering & Profiling
Agglomerative Clustering identified four actionable infrastructure archetypes:
- Efficient Core (Cluster 0): Optimal servers, serve as a blueprint for other departments.
- High Waste (Clusters 1 & 2): Underutilized or over-provisioned servers, target for right-sizing or decommissioning.
- Legacy Risk (Cluster 3): Older, high-maintenance servers requiring hardware refresh or cloud migration.

![3D Cluster Map](images/3d_pca_space.png)

### Step 4: Strategic ROI Analysis
Mapping clusters to financial impact revealed that high-waste servers account for $498K of monthly spend. Applying a conservative 20% optimization factor projects $1.2M in annual savings, reducing total IT overhead by ~12%. These insights support evidence-based IT policy decisions, such as targeted decommissioning and capacity planning.









