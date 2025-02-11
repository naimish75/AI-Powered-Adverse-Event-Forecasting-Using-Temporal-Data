# AI-Powered-Adverse-Event-Forecasting-Using-Temporal-Data


## Overview
This project aims to predict **future drug interactions and adverse events** using **temporal data analysis**. By leveraging real-world datasets from **FAERS, ClinicalTrials.gov, WHO ICTRP, and OpenFDA**, the model continuously learns and updates risk levels dynamically. This provides a **preemptive approach** to adverse event detection, allowing healthcare professionals to take action before risks become clinically significant.

##  Key Features
- **Predictive Risk Analysis:** Identifies potential future drug interactions.
- **Time-Series Forecasting:** Uses **LSTM/Transformer-based models** to analyze temporal trends in adverse events.
- **Dynamic Updates:** Integrates real-time FAERS reports for continuous learning.
- **Customizable API:** Provides an interface for querying real-time risk predictions.

## Data Sources
The project utilizes publicly available datasets:

| Dataset | Description | Access | Size |
|---------|-------------|--------|------|
| **FAERS (FDA)** | Reports of adverse drug reactions | [Download](https://fis.fda.gov/extensions/FPD-QDE-FAERS/FPD-QDE-FAERS.html) | 60-140 MB per quarter |
| **ClinicalTrials.gov** | Data on clinical drug trials and reported adverse events | [Download](https://clinicaltrials.gov/ct2/resources/download) | Several GBs |
| **WHO ICTRP** | International clinical trials registry data | [Download](https://www.who.int/clinical-trials-registry-platform/network/who-data-set/downloading-records-from-the-ictrp-database) | 200-500 MB |
| **OpenFDA API** | Live API for real-time adverse event tracking | [API Docs](https://open.fda.gov/apis/drug/event/) | API-based |

## Tech Stack
- **Programming Language:** Python
- **Machine Learning:** TensorFlow, PyTorch
- **Data Processing:** Pandas, NumPy, Scikit-learn
- **Time-Series Models:** LSTM, Transformer models
- **Data APIs & Extraction:** OpenFDA API, Requests
- **Visualization:** Matplotlib, Plotly
- **Deployment:** Flask / FastAPI (for REST API), Streamlit (for visualization dashboard)

## Implementation Workflow
### 1️⃣ **Data Collection & Preprocessing**
- Download and clean FAERS, ClinicalTrials.gov, and WHO ICTRP datasets.
- Parse JSON/XML/CSV data into structured format.
- Align time-series data for modeling.

### 2️⃣ **Feature Engineering**
- Extract key event timestamps, drug categories, and patient demographics.
- Create aggregated time-series sequences for each drug.

### 3️⃣ **Model Training**
- Train **LSTM** or **Transformer-based models** to forecast adverse event trends.
- Implement **dynamic risk scoring** based on recent event patterns.

### 4️⃣ **Real-Time Data Updates**
- Use OpenFDA API to **ingest new adverse event reports**.
- Continuously update risk predictions.

### 5️⃣ **Deployment & API Integration**
- Expose model predictions via **REST API**.
- Create a **dashboard (Streamlit)** for interactive risk assessments.

## 🖥️ How to Run
### **1️⃣ Setup Environment**
```bash
# Clone the repository
git clone https://github.com/your-username/ai-adverse-event-forecasting.git
cd ai-adverse-event-forecasting

# Create virtual environment
python -m venv env
source env/bin/activate  # (Linux/macOS)
# OR
env\Scripts\activate  # (Windows)

# Install dependencies
pip install -r requirements.txt
```

### **2️⃣ Download Datasets**
- Manually download FAERS, ClinicalTrials.gov, and WHO ICTRP datasets from their respective links.
- Store them in the `data/` directory.

### **3️⃣ Train the Model**
```bash
python train.py
```

### **4️⃣ Run the API Server**
```bash
python app.py
```

### **5️⃣ Access the Dashboard**
Open [http://localhost:5000](http://localhost:5000) in your browser.

## Example API Usage
```python
import requests

url = "http://localhost:5000/predict"
data = {"drug_name": "Ibuprofen", "date_range": "2022-2024"}
response = requests.post(url, json=data)
print(response.json())
```

## Future Enhancements
- 🔹 Expand to **multi-modal analysis** (combining clinical notes, imaging, and genomic data).
- 🔹 Implement **knowledge graph-based drug interactions**.
- 🔹 Enhance model interpretability with **SHAP/LIME explanations**.



