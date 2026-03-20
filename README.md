# 📊 Churn Prediction System — Production-Ready Machine Learning Microservice

A fully production-grade **FastAPI + ML** microservice that trains, serves, explains, monitors, and Dockerizes a Churn Prediction model.

This project includes:
- 🧠 Model Training Pipeline (RandomForest)
- 📈 SHAP Explainability (Global + Local)
- ⚡ FastAPI Inference Server
- 🔍 Observability (Prometheus Metrics + Grafana Dashboard)
- 🐳 Docker & Docker Compose Support
- 🔁 CI/CD (GitHub Actions + GitLab CI + DockerHub)
- 🧪 Automated Tests
- 📁 Example Data Files

---
## 🚀 Features
- **/predict** → Probability & label output
- **/explain_local** → SHAP explanation for a row
- **/health** → Service health probe
- **Fully async HTTP client–compatible**
- **Lightweight synthetic model weights included**
- **Monitoring ready** with latency histograms & request counters

---
## 📁 Project Structure
```
src/
  ├── api.py
  ├── config.py
  ├── loader.py
  ├── shap_analysis.py
  ├── train.py
examples/
tests/
Dockerfile
docker-compose.yml
.github/workflows/ci.yml
```

---
## 🧠 Train the Model
```
python src/train.py
```
This generates:
```
artifacts/model.pkl
data/test.csv
```
Plus SHAP-compatible dataset.

---
## 🔮 Run API (Development)
```
uvicorn src.api:app --reload --port 8001
```
Open docs:
```
http://localhost:8001/docs
```

---
## 🐳 Run with Docker
```
docker compose up --build
```
API available at:
```
http://localhost:8001
```

---
## 🔥 Example Request
```
POST /predict
{
  "feature1":0.42,
  "feature2":0.17,
  "feature3":0.88
}
```
Response:
```
{"probability":0.71, "prediction":1}
```

---
## 🧬 SHAP Explainability
```
GET /explain_local?idx=0
```
Returns path to generated `local_row_0.png` waterfall plot.

---
## 📊 Monitoring
### Prometheus
```
http://localhost:8001/metrics
```
### Grafana
Import the provided dashboard JSON.

---
## 🧪 Run Tests
```
pytest
```

---
## 🔧 CI/CD
Includes:
- GitHub Actions → test → build → push Docker image
- GitLab CI mirror
- DockerHub auto-build configuration

Docker Image Target:
```
docker.io/nileshmodlier/churn-system
```

---
## 📝 License
MIT
