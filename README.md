# 🏦 Bank Retirement Prediction API

Production-ready **Machine Learning inference API** for predicting customer retirement subscription decisions, built with **FastAPI**, **Docker**, and deployed on **Railway**.

This repository demonstrates how a trained ML model can be exposed as a **containerized REST API** and deployed to a cloud platform.

---

## 🚀 What This Project Is

This project is a **deployment and serving layer** for a pre-trained machine learning model.

It focuses on:
- serving predictions via a REST API
- containerized deployment using Docker
- cloud deployment on Railway
- clean API design and validation
- health monitoring endpoints

The ML model itself is developed and packaged separately and is consumed here as a dependency.

---

## 🧠 Model Overview

- **Task:** Binary classification  
- **Domain:** Banking / Customer behavior  
- **Goal:** Predict whether a customer will subscribe to a retirement deposit product  
- **Model:** Pre-trained ML model packaged as a Python module  

This repository **does not train the model** — it only serves it.

---

## 📦 Model Distribution & Versioning

The machine learning model used by this API is distributed as a **versioned Python package** via **GitHub Releases**.

During the Docker build process, the model package is automatically downloaded and installed from a release artifact (`.whl` file).

This approach ensures:
- reproducible deployments
- explicit model versioning
- immutable model artifacts
- clean separation between training and serving

The API always serves the exact model version defined in `requirements.txt`.

---

## 🌐 API Endpoints

| Method | Endpoint | Description |
|------|--------|-------------|
| GET | `/api/v1/health` | Health check |
| POST | `/api/v1/predict` | Generate prediction |

Interactive API documentation is available via Swagger UI at `/docs`.


---

## 🖥️ Live Deployment (Railway)

The API is deployed on **Railway** and publicly accessible:

🔗 **Live URL:**  
https://exemplary-balance-production.up.railway.app/

You can test requests directly via the Swagger UI.

---

## 🧪 Health Check

```
GET /api/v1/health
```

Response:
```
{
  "name": "Bank_retirement_classification_api",
  "api_version": "0.0.2",
  "model_version": "0.0.1"
}
```

---

## 🐳 Dockerized Deployment

The service is fully containerized using Docker.

Deployment flow:
1. ML model package is installed from a GitHub Release (`.whl`)
2. Application is packaged in a Docker image
3. Image is deployed to Railway
4. Railway handles runtime, scaling and exposure

The same container can be deployed locally or on other cloud providers.

---

## 📁 Project Structure
```
bank_retirement_api/
├── bank_retirement_api
│   ├── app
│   │   ├── __init__.py
│   │   ├── api.py
│   │   ├── config.py
│   │   ├── main.py
│   │   ├── schemas
│   │   │   ├── __init__.py
│   │   │   ├── health.py
│   │   │   └── predict.py
│   │   └── tests
│   │       ├── __init__.py
│   │       ├── conftest.py
│   │       └── test_api.py
│   ├── mypy.ini
│   ├── Procfile
│   ├── requirements.txt
│   ├── run.sh
│   ├── test_requirements.txt
│   ├── tox.ini
│   └── typing_requirements.txt
├── .gitignore
├── .dockerignore
├── Dockerfile
└── README.md
```


---

## ⚙️ How It Works
	1.	Client sends a request to /api/v1/predict
	2.	Input is validated via Pydantic schemas
	3.	The packaged ML model is loaded
	4.	Prediction is generated
	5.	JSON response is returned

---

## 🛠️ Tech Stack
- Python
- FastAPI
- Pydantic
- Docker
- Railway
- Uvicorn
- Tox

---

## 🎯 Why This Repository Exists

This project demonstrates:
- real-world ML inference serving
- clean separation of training and deployment
- Docker-based deployment
- cloud deployment using Railway
- MLOps fundamentals

---

## 📌 Project Status

✅ Deployed and stable
🚀 Future improvements:
- CI/CD pipeline
- monitoring & metrics
- authentication