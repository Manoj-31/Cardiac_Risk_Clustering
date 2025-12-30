# Cardiac Risk Clustering Using Machine Learning

## 📌 Project Overview
This project applies **unsupervised machine learning techniques** to cardiac health records in order to **categorize patients into low, medium, and high cardiovascular risk groups**.  
Since the dataset does not contain predefined labels, clustering methods are used to discover meaningful patient groupings based on clinical similarities.

The project compares **K-Means Clustering** and **Hierarchical Agglomerative Clustering**, evaluates their performance using standard clustering metrics, and analyzes their interpretability in a healthcare context.

---

## 🧠 Dataset Description
The dataset is a **modified heart failure dataset** consisting of clinical and demographic attributes related to cardiac health.

### Key Features
- Age  
- Anaemia  
- Platelet Count  
- Creatinine Phosphokinase  
- Diabetes  
- High Blood Pressure  
- Ejection Fraction  
- Serum Creatinine  
- Serum Sodium  
- Smoking  

Continuous variables such as **age, ejection fraction, serum creatinine, creatinine phosphokinase, and platelet count** are expected to have a stronger influence on cluster formation due to higher variance and clinical relevance.

---

## 🔧 Data Preprocessing

### Handling Missing Values
- **Continuous Variables:** Filled using the **median** (robust to outliers)  
  - e.g., platelets, serum sodium, serum creatinine
- **Binary Variables:** Filled using the **mode**  
  - e.g., anaemia, diabetes, smoking

This ensures a complete and consistent dataset, improving clustering stability.

---

### Feature Scaling
To prevent features with large numeric ranges (e.g., platelet count) from dominating the clustering process, feature scaling was applied:

- **MinMaxScaler:** Scales features to range (0, 1), but sensitive to outliers  
- **StandardScaler:** Less effective for skewed medical data  
- **RobustScaler:** Uses median and IQR, best suited for medical datasets  

📌 **RobustScaler achieved the highest silhouette score** and was selected for the final models.

---

## ⚙️ Clustering Algorithms Applied

### 1️⃣ K-Means Clustering
- Randomly initializes *k* centroids  
- Assigns data points to the nearest centroid  
- Updates centroids using the mean of assigned points  
- Repeats until convergence  

---

### 2️⃣ Hierarchical Agglomerative Clustering
- Starts with each data point as its own cluster  
- Iteratively merges the closest clusters  
- Produces a dendrogram representing cluster hierarchy  

---

## 📊 Cluster Visualization
To visualize high-dimensional data, **t-SNE plots** were used for both algorithms.

- Both K-Means and Hierarchical Clustering produced **largely similar cluster structures**
- Minor discrepancies were observed, but overall consistency indicates meaningful group separation

---

## 📈 Cluster Evaluation

### Evaluation Metrics
- **Silhouette Score** (higher is better)
- **Davies–Bouldin Index** (lower is better)

### K-Means Results
- Evaluated for `k = 2` to `k = 40`
- Best performance at **k = 3**
  - Silhouette Score ≈ **0.60**
  - Davies–Bouldin Index < **0.8**

### Hierarchical Clustering Results
- Evaluated for `k = 2` to `k = 40`
- Best performance at **k = 3**
  - Silhouette Score ≈ **0.57**
  - Davies–Bouldin Index ≈ **0.78**

📌 Both metrics consistently identify **3 clusters** as optimal.

---

## 🔍 Comparative Analysis
- Both algorithms revealed a **clear underlying structure** in the data
- **K-Means** showed a sharper performance peak at `k = 3`, making the optimal cluster count more evident
- **Hierarchical Clustering** provided more flexibility, with good performance across `k = 3–4`

Overall, both methods support **three meaningful cardiac risk groups**.

---

## 🩺 Interpretability & Usefulness
The resulting clusters are **clinically interpretable**, grouping patients based on meaningful health indicators such as:
- Age
- Ejection Fraction
- Serum Creatinine
- Platelet Count

These clusters correspond to:
- **Low Risk**
- **Moderate Risk**
- **High Risk**

### Real-World Impact
- Early identification of high-risk patients
- Improved patient prioritization and monitoring
- Support for personalized treatment planning
- Better resource allocation in healthcare systems

---

## 🛠️ Technologies Used
- Python  
- scikit-learn  
- NumPy  
- Pandas  
- Matplotlib / Seaborn  

---

## 📄 Project Report
The full project report with detailed methodology, evaluation, and visualizations is available here:

📘 **[Project Report (PDF)](Report.pdf)**

---

## 👤 Author
**Sai Manoj Kumar Penikalapati**  
MSc Artificial Intelligence  
University of Galway  
Student ID: 25241477  
