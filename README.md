# NTT-Dynamic-Machine-Data-Management-Local-Risk-PredictioN
# Dynamic Machine Data Management & Local Risk Prediction

A local web-based application for managing dynamic machine information and predicting machine risk levels using locally trained Python machine learning models.

The application allows users to:

- Dynamically configure machine fields
 - Create, view, update, and delete machine records
 - Store dynamic machine attributes without changing the database schema
 - Select a machine for risk prediction
 - Select different local ML models
 - Predict machine risk as Low, Medium, or High
 - Add new dynamic fields such as Humidity
 - Run all ML predictions locally without cloud AI or external AI APIs

---

## 1. Project Overview

The objective of this project is to build a simple machine management and risk prediction system where machine attributes can be configured dynamically.

The initial machine risk prediction model uses:

- Temperature
 - Pressure
 - Vibration

The application also supports additional dynamic fields such as:

- Humidity
 - Text fields
 - Number fields
 - Dropdown fields

Additional fields are stored and displayed by the application without requiring changes to the database schema.

The current ML models use the original three features:

```text
 Temperature
 Pressure
 Vibration
# 12. Execution / How to Run

## Step 1 — Clone the Repository

Open PowerShell or Command Prompt and run:

git clone https://github.com/sudheer-gsc/NTT-Dynamic-Machine-Data-Management-Local-Risk-PredictioN.git

Navigate into the project:

cd Dynamic-Machine-Data-Management-Local-Risk-Prediction

---

## Step 2 — Create Python Virtual Environment

Navigate to the backend:

cd backend

Create a virtual environment:

python -m venv venv

---

## Step 3 — Activate the Virtual Environment

### Windows PowerShell

.\venv\Scripts\Activate.ps1

After activation, the terminal should show:

(venv)

---

## Step 4 — Install Required Packages

Install the backend dependencies:

pip install -r requirements.txt

The main dependencies include:

- FastAPI
 - Uvicorn
 - SQLAlchemy
 - Scikit-learn
 - NumPy
 - Joblib

---

## Step 5 — Start the FastAPI Application

Make sure you are inside the `backend` directory:

cd backend

Start the application:

python -m uvicorn app.main:app --reload --reload-dir app

Expected output:

INFO: Uvicorn running on http://127.0.0.1:8000
 INFO: Application startup complete.

---

## Step 6 — Open the Application

Open a web browser and navigate to:

http://127.0.0.1:8000

The Machine Risk Intelligence dashboard will be displayed.

---

# 13. Application Execution Flow

After starting the application, follow these steps.

### Step 1 — Check API Status

The dashboard should display:

API Online

The backend health endpoint can also be checked at:

http://127.0.0.1:8000/health

Expected response:

{
 "status": "healthy"
 }

---

### Step 2 — Configure Machine Fields

Go to:

Field Configuration

Create fields such as:

| Field Name | Type | Required |
 |---|---|---|
 | Temperature | Number | Yes |
 | Pressure | Number | Yes |
 | Vibration | Dropdown | Yes |
 | Humidity | Number | Yes |

For Vibration, configure the dropdown options:

Low
 Medium
 High

---

### Step 3 — Create a Machine

Go to:

Machine Management

Enter the configured machine parameters.

Example:

Temperature:

85

Pressure:

120

Vibration:

High

Humidity:

75

Click:

Create Machine

The machine will be stored in the SQLite database.

---

### Step 4 — Select a Machine

Go to:

Risk Prediction

Select the machine that was created.

---

### Step 5 — Select an ML Model

The application supports the following local models:

- Random Forest
 - Decision Tree
 - Gradient Boosting
 - Extra Trees
 - Logistic Regression

Select the required model from the model dropdown.

---

### Step 6 — Run Risk Prediction

Click:

Run Risk Prediction

The application sends the selected machine data to the local FastAPI prediction endpoint.

Example request:

POST /prediction/1?model_name=extra_trees

The backend then calls the local Python prediction script.

---

# 14. ML Prediction Execution

The prediction flow is:

Browser
 |
 v
 FastAPI Backend
 |
 v
 prediction.py
 |
 v
 Local Python Process
 |
 v
 ml/predict.py
 |
 v
 Joblib Model
 |
 v
 Scikit-learn
 |
 v
 Risk Level
