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
3. Open `shg_itfm.ipynb` in Jupyter Notebook or VS Code.


## Data Visualizations

To identify cost-saving opportunities, the high-dimensional IT infrastructure data was processed through a machine learning pipeline. The order of operations reflects the technical logic used in the `itfm.ipynb` script.

### 1. Dimensionality Reduction Analysis (PCA)
Before clustering, we utilized **Principal Component Analysis** to reduce noise and ensure our model focused on behavioral patterns. This plot shows the cumulative variance explained by the components.

![PCA Information Distribution](images/pca_information_distribution.png)
*Above: The Variance Explained ratio showing that 3 components capture the majority of data variance.*

### 2. The Infrastructure Cluster Map (Agglomerative Clustering)
After reducing dimensions, we applied **Agglomerative Clustering**. By plotting the 3D projection, we can clearly isolate "High-Waste" assets from "Efficient" resources.

![3D PCA Space](images/3d_pca_space.png)
*Above: The 3D Cluster Map where Clusters 1 & 2 represent low-utilization, high-cost "Ghost Assets".*

### 3. Strategic ROI Summary
The final step translates these clusters into financial data. The script identifies approximately **$500,000 in annualized savings** by targeting the specific inefficiencies found in the clusters above.






