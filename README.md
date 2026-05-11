<div align="center">

# 🧬 GlucoVision Digital Twin Service

**A living computational model of each patient's metabolic system using Neural ODE.**  
*Neural ODE · What-if simulation · Glucose-insulin dynamics · Per-patient calibration*

[![PyTorch](https://img.shields.io/badge/PyTorch-2.x-EE4C2C?style=for-the-badge&logo=pytorch)](#)
[![FastAPI](https://img.shields.io/badge/FastAPI-Python-009688?style=for-the-badge&logo=fastapi)](#)
[![InfluxDB](https://img.shields.io/badge/InfluxDB-Time--Series-22ADF6?style=for-the-badge&logo=influxdb)](#)
[![MLflow](https://img.shields.io/badge/MLflow-Registry-0194E2?style=for-the-badge)](#)
[![Docker](https://img.shields.io/badge/Docker-Containerised-2496ED?style=for-the-badge&logo=docker)](#)
[![Status](https://img.shields.io/badge/Status-In%20Development-f59e0b?style=for-the-badge)](#)

</div>

---

## 📌 Purpose

GlucoVision Digital Twin creates a **patient-specific physiological simulation model** using Neural Ordinary Differential Equations (Neural ODE). It enables **what-if scenario exploration**: *"What happens to my glucose if I eat hoppers instead of string hoppers tomorrow?"* and projects 24–72 hour health trends (glucose, HbA1c, BMI).

> **Research-grade service** — Neural ODE is a frontier research technique. Separated from production inference because it has an experimental lifecycle and different compute profile.

---

## 📁 Project Structure

```
19-glucovision-digital-twin-service/
└── (Git repository initialised — structure to be scaffolded)
```

---

## ✨ Planned Features (by phase)

### Phase 1 — ODE Engine
- [ ] Neural ODE patient state model (torchdiffeq)
- [ ] Patient state vector: glucose, insulin, BMI, HbA1c
- [ ] Per-patient ODE parameter fitting (adjoint sensitivity)
- [ ] FastAPI simulation endpoint

### Phase 2 — What-If Scenarios
- [ ] Scenario runner: proposed meal/exercise → simulated glucose curve
- [ ] 24–72 hour health projection (glucose, energy, weight)
- [ ] Scenario save and comparison API
- [ ] Chart data endpoints for mobile and web dashboard

### Phase 3 — Integration & Calibration
- [ ] Continuous twin updates from `12` glucose prediction + `15` recommendation
- [ ] Daily batch recalibration per patient
- [ ] Redis twin state caching for fast scenario evaluation
- [ ] Uncertainty quantification (Monte Carlo dropout)

---

## 🚀 Getting Started

### Prerequisites

- Python ≥ 3.11, InfluxDB, Redis, MLflow, Docker & Docker Compose
- Optional: NVIDIA GPU for ODE parameter calibration

### Setup (once scaffolded)

```bash
pip install -r requirements.txt
uvicorn main:app --reload --port 8014

docker compose up --build
```

---

## 🏗️ Planned Tech Stack

| Layer | Technology |
|---|---|
| Framework | FastAPI (Python) |
| Neural ODE | torchdiffeq (PyTorch ODE solver) |
| Deep Learning | PyTorch 2.x |
| Scientific Computing | SciPy, NumPy |
| Time-Series DB | InfluxDB |
| Cache | Redis |
| Experiment Tracking | MLflow |
| Containerisation | Docker |

---

## 🔗 Backend Dependencies

| Service | Interaction |
|---|---|
| `12` glucose-prediction | Glucose data feed for twin calibration |
| `15` recommendation-engine | Meal and energy context for simulation |
| `07` user-service | Patient physiological parameters |
| InfluxDB | Historical glucose for ODE fitting |
| Redis | Twin state caching |

---

## 🔐 Security Notes

- Digital twin contains patient physiology — classified as PHI, encrypted at rest
- What-if scenarios access-controlled per patient
- Twin parameters never shared across patients (each twin is personal)

---

## 🧪 Testing (Planned)

```bash
pytest tests/ode/          # Simulated vs actual glucose RMSE < 1 mmol/L (24hr)
pytest tests/whatif/       # Meal → glucose peaks within plausible range
pytest tests/calibration/  # ODE parameters converge in 100 iterations
pytest tests/cache/        # Redis twin state used on repeated scenarios
```

---

<div align="center">

*Part of the [GlucoVision Platform](../01-glucovision-platform-architecture) — 21-Repo AI Diabetes Management System*

</div>
