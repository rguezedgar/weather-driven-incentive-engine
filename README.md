# 🌦️ Weather-Driven Incentive & Communication Automation System

## 📌 Overview
This project implements an **automated, weather-driven decision engine** that evaluates forecasted weather conditions at a city level and determines whether **courier communications and/or incentive campaigns** should be triggered.

The system replaces a **manual, reactive operational workflow** with a **data-driven, rule-based automation**, improving response time, consistency, courier safety, and cost efficiency.

---

## 🎯 Business Problem
Adverse weather conditions (rain, snow, freezing rain) often lead to:
- Courier supply shortages
- Increased delivery times
- Higher order cancellations
- Reactive and inconsistent incentive decisions

Historically, operations teams:
- Manually monitored weather forecasts
- Launched incentives late
- Worked weekends and off-hours
- Lacked standardized decision logic

---

## ✅ Solution Summary
This project:
- Ingests **hourly weather forecasts via API**
- Applies **city-specific business rules**
- Determines whether to trigger:
  - Communications
  - Incentives
  - Safety-only alerts
- Sends **automated email notifications**
- Logs decisions for audit and reporting

---

## 🏗️ Architecture
```Weather API (Open-Meteo)
↓
Weather Client (Python)
↓
Normalized Weather Data (DataFrame)
↓
Campaign Decision Engine
↓
Decision Output (Comms / Incentives)
↓
Email Notification + CSV Export
```

---

## 📂 Project Structure

```weather-incentive-project/
│
├── data/
│   ├── control_center.csv      # City-level configs & thresholds
│   └── recommendations.csv     # Final decision output
│
├── src/
│   ├── weather_client.py       # Weather API ingestion
│   ├── campaign_engine.py      # Business rules & decision logic
│   └── notifier.py             # Email notification logic
│
├── tests/
│   └── test_api_weather.py     # Pytest API validation tests
│
├── main.py                     # Orchestration script
├── requirements.txt
└── README.md
```


---

## 📥 Inputs

### 1️⃣ Weather Forecast API
- Hourly precipitation
- Precipitation probability
- Temperature

### 2️⃣ Control Center (CSV Config)
Defines city-specific rules:
- Weather thresholds
- Safety limits
- Opt-in / Opt-out behavior
- Incentive cohort size
- Communication enablement

---

## 📤 Outputs
- **CSV File:** `recommendations.csv`
- **Email Alerts:** Automated operational notifications
- **Decision Types:**
  - Comms ON + Incentives ON
  - Comms ON + Incentives OFF (Safety)
  - Comms OFF

---

## 🧠 Core Business Logic

- Average precipitation calculation
- % of bad weather hours
- Safety suppression logic
- Opt-in vs Opt-out campaign handling
- Config-driven decision-making

---

## 🧪 Testing
API validation tests implemented using **pytest**:
- HTTP status validation
- JSON schema checks
- Mandatory field presence
- Negative value checks

---

## 🛠️ Tech Stack
- Python
- Pandas
- Requests
- Pytest
- SMTP (Email Automation)

---

## 🚀 How to Run

```bash
pip install -r requirements.txt
python main.py


