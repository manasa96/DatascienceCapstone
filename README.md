# AnomaData - Predictive Maintenance & Anomaly Detection Dataset

## 📌 Project Overview
The **AnomaData** dataset is designed for **predictive maintenance and anomaly detection** in industrial equipment.  
It contains **time-series sensor readings** with binary anomaly labels, helping identify patterns that lead to machine breakdowns.

---

## 📊 Dataset Attributes

| Column Name | Data Type | Description |
|-------------|------------|------------------------------------------------|
| **time** | `datetime` | The timestamp when the sensor data was recorded. |
| **y** | `int (0 or 1)` | The target variable: `0 = Normal`, `1 = Anomaly (Machine Failure)`. |
| **x1** - **x60** | `float` | Sensor readings capturing machine performance, vibration, temperature, and pressure. |

### **1️⃣ Target Variable: `y`**
- `0` → Normal operation  
- `1` → Anomaly detected (machine failure or abnormal event)

### **2️⃣ Time Column: `time`**
- The dataset spans **May 1999**.
- Captures machine behavior **over time** (time-series data).
- Useful for **trend analysis, rolling averages, and lag feature engineering**.

### **3️⃣ Sensor Readings (`x1` to `x60`)**
- These columns represent **various sensor measurements**.
- Can include data like **temperature, pressure, motor speed, vibration levels, and humidity**.
- Each sensor may indicate signs of wear, overheating, or unexpected spikes that signal anomalies.

---

## 📌 Dataset Summary Statistics

- **Total Records**: `~18,398`
- **Anomaly Rate**: `~0.67%` (`y=1` is rare)
- **Feature Count**: `60` sensor readings (`x1` - `x60`)
- **Time Period**: `May 1999`

---

## 🏗️ Preprocessing Steps Applied
- **Converted `time` column to `datetime` format**.
- **Handled missing values** (using median imputation).
- **Standardized sensor readings** (MinMaxScaler).
- **Applied feature engineering** (lag features, rolling averages).
---
-- ** To successfully implement and evaluate One-Class SVM, Autoencoder, and Isolation Forest within a single script, careful structuring and variable management were essential. To maintain reproducibility and fairness in model evaluation, all key variables were reset before each model execution.  Final-report.pdf has all the details. 

## 🔍 Modeling Approaches Used
### **1️⃣ Isolation Forest (IF)**
- Strength: Good for **unsupervised anomaly detection**.
- Weakness: Performed poorly due to **low anomaly recall**.

### **2️⃣ One-Class SVM**
- Strength: Learns from **only normal data (`y=0`)**.
- Weakness: **Recall was very low (4%)**, failing to detect most anomalies.

### **3️⃣ Autoencoder (Best Performing)**
- Strength: **60% anomaly recall**, meaning it correctly detects more anomalies.
- Weakness: **Precision still low (8%)**, meaning too many false positives.

## 📂 File Structure
AnomaData_Project
 ├── AnomaData.xlsx       # Original dataset
 ├── README.md           # Dataset documentation
 ├── Visuals        # visualizations - screenshots of visual charts - EDA and Results of each model.
 ├── notebooks       # Jupyter notebooks for EDA and training
	Main-script.py
 ├── models              # Serialized models and logs
	├── autoencoder_model.h5  # Trained Autoencoder model
	├── isolation_forest_model.pkl # Trained Isolation Forest model

 	├── optimized_isolation_forest.pkl # Trained and optimized Isolation Forest model
├── one_class_svm_model.pkl # Trained SVM Model

 ├── data                # Processed dataset versions
	├── train_data.xlsx
	├── test_data.xlsx
	├── processed_data.xlsx
 ├── requirements.txt     # Python dependencies

## How to Run the Code (A file with all the dependencies - requirements.txt is attached to run the code) 
pip install pandas numpy matplotlib seaborn openpyxl scikit-learn
pip install tensorflow joblib
python notebooks/Main-script.py
