# Flood Prediction & Early Warning System

As part of my project, I have developed a comprehensive Flood Prediction and Early Warning System. Below is a detailed explanation of the methodology and implementation steps, presented from my perspective as a student researcher.

## 1. Data Collection & Dataset Integration
The foundation of this project is a robust historical dataset. I collected individual environmental datasets from **Kaggle**, focusing on data from **2023 to 2025**. These datasets were specific to the regions of **Andhra Pradesh** and **Telangana**, covering various meteorological parameters.

- **Individual Collection**: I started by downloading separate CSV files for different districts and years.
- **Data Combining**: Since the objective was to build a generalized model for the region, I merged these individual datasets into a unified master dataset, ensuring we had a continuous timeline of environmental changes.

## 2. Data Preprocessing Pipeline
Raw data is often noisy, so I spent significant effort on preprocessing to ensure model reliability:
- **Cleaning**: I removed duplicate entries and inconsistencies in naming conventions (especially for rivers and stations).
- **Handling Missing Values**: I used interpolation for short gaps and statistical imputation for larger missing blocks in parameters like humidity and temperature.
- **Normalization**: I standardizing numerical values using scaling techniques to ensure that features like Rainfall (mm) and Reservoir Levels (%) were on a comparable scale for the algorithms.

## 3. Machine Learning Methodology
To provide accurate and explainable predictions, I utilized multiple ML approaches:

### A. Time-Series Forecasting (LSTM)
I implemented a **Long Short-Term Memory (LSTM)** neural network to forecast future river levels. Since river flow is sequential, LSTM is perfect for identifying long-term dependencies in the data over 24, 48, and 72-hour horizons.

### B. Classification (XGBoost & Random Forest)
For the final "Risk Level" (Safe, Warning, Severe), I used ensemble algorithms like **XGBoost** and **Random Forest**. These models evaluate current environmental inputs (Rainfall, Humidity, Soil Type) against historical flood patterns to classify the probability of a flood event.

### C. Explainable AI (SHAP)
To make the "Black Box" of ML understandable for guides and stakeholders, I integrated **SHAP (SHapley Additive exPlanations)**. This allows the system to explain *why* it reached a certain prediction (e.g., "Probability increased by 20% due to high Reservoir Capacity").

## 4. Model Preservation
Once the training achieved satisfactory accuracy, I saved the models professionally:
- **PyTorch Models (.pt)**: Used for the LSTM forecasting logic.
- **Joblib/Pickle Models**: Used for the XGBoost classifiers and SHAP explainer objects for fast loading during runtime.

## 5. System Execution & Integration
The project is integrated into a full-stack dashboard for real-time monitoring:
- **Backend (FastAPI)**: Loads the models on startup and serves the prediction API.
- **Frontend (React)**: A modern dashboard using Recharts and Leaflet for data visualization and map tracking.

### Running the Application:
To run the project, I follow these steps in separate terminal windows:

**Step 1: Start the Backend**
```bash
python -m uvicorn backend.main:app --host 0.0.0.0 --port 8000
```

**Step 2: Start the Frontend**
```bash
npm run dev
```

The system then becomes accessible at `http://localhost:5173`, where I can input current environmental parameters and get instant AI-powered flood risk assessments.
