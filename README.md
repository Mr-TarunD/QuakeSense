# <div align="center">🌍 **QuakeSense – Real-Time Seismic Analytics System**</div>

<div align="center">
A real-time earthquake monitoring, visualization, and risk intelligence platform powered by global seismic data.
<br><br>
</div>

---

<img width="1564" height="897" alt="Image" src="https://github.com/user-attachments/assets/085f887a-d367-4114-851b-b0874dc5ed2d" />
<img width="1562" height="902" alt="Image" src="https://github.com/user-attachments/assets/9372adfe-fd9b-4caa-aab2-ecc648eb81d1" />

## 🚀 **Overview**

**QuakeSense** is a real-time seismic analytics system that ingests live earthquake data from the USGS GeoJSON API, enriches it with domain-specific metrics, and presents it through an interactive, user-friendly analytics dashboard.
It enables **global monitoring**, **risk assessment**, **trend analysis**, and **data export** — all from a clean, browser-based interface.

This project serves as a practical prototype of how real-time data pipelines, enrichment layers, and analytical dashboards power **disaster intelligence systems**.

---

## 🎯 **Key Features**

### 🔹 **Live 24-Hour Seismic Dashboard**

* Fetches real-time earthquake events from USGS (last 24 hours)
* Filter by **minimum magnitude** and **region/country**
* Sort by **Newest**, **Highest Magnitude**, or **Highest Risk**
* Interactive **bubble chart** (Magnitude vs Time)
* Automatic **Major Quake Alert** (≥ 6.0 magnitude)
* Download filtered results as **CSV**

### 🔹 **Top 10 Major Earthquakes (Last 30 Days)**

* Analyzes the global seismic dataset from the last month
* Extracts the **Top 10 strongest events**
* Visualized via a clean **horizontal bar chart**
* Includes severity, depth category, region, and official USGS links

### 🔹 **Data Enrichment Layer**

Automatically derives:

* **Severity levels** (Micro → Great)
* **Depth categories** (Shallow / Intermediate / Deep)
* **Region extraction** from raw location text
* **Risk score** (magnitude × depth factor)
* **Risk level** (Low / Moderate / High / Critical)

### 🔹 **Minimal Setup, Runs Anywhere**

* Fully container-less
* Works on **Google Colab**, local Python, or cloud notebooks
* Clean Gradio UI — no HTML/JS required

---

## 🧠 **System Architecture**

```
USGS GeoJSON API  →  Data Ingestion  →  Data Enrichment  →  Analytics Layer  →  Gradio Web UI
                         │                    │                   │                     │
                         └── Error Handling   └── Risk Model      └── Top-10 Engine     └── Visualization & CSV Export
```

### Core Components:

* **Data Ingestion:**
  Fetches real-time JSON feeds using `requests`

* **Preprocessing & Enrichment:**
  Implemented with `pandas` + custom risk model:

  * `severity`, `depth_category`, `region`, `risk_score`, `risk_level`

* **Analytics Engine:**
  Filters, sorts, aggregates, and generates insights for:

  * Live dashboard
  * Monthly Top 10 report

* **Visualization Layer:**
  Built using `plotly.express`
  Includes:

  * Scatter plots
  * Bar charts
  * Tabular results

* **UI Layer:**
  Powered by **Gradio Blocks**
  Tabbed interface:

  * *Live Dashboard (24h)*
  * *Top 10 Major Earthquakes (30 days)*

---

## ⚙️ **Tech Stack**

| Layer           | Technologies                        |
| --------------- | ----------------------------------- |
| Data Source     | USGS Earthquake Hazards GeoJSON API |
| Backend         | Python 3.x                          |
| Data Processing | pandas, numpy                       |
| Visualization   | plotly.express                      |
| UI / Deployment | Gradio                              |
| Export          | CSV (pandas)                        |
| Environment     | Google Colab / Local Python         |

---

## 📂 **Project Structure**

```
QuakeSense/
│── quake_sense.ipynb          # Complete working notebook (Colab-friendly)
│── src/
│     ├── ingestion.py         # API fetch logic
│     ├── enrichment.py        # Feature engineering / risk model
│     ├── dashboard.py         # Live dashboard logic
│     └── top10_analyzer.py    # 30-day Top 10 analytics
│── app/
│     └── ui.py                # Gradio interface
│── assets/
│     └── screenshots/         # Plots, dashboard images
│── README.md                  # This documentation
```

---

## ▶️ **How to Run**

### **Option A — Run on Google Colab (Recommended)**

1. Upload the notebook
2. Run all cells top-to-bottom
3. The Gradio app will open automatically

### **Option B — Run Locally**

```bash
pip install -r requirements.txt
python app/ui.py
```

---

## ⚠️ **Risk Scoring Model**

The risk score is derived as:

```
risk_score = magnitude × depth_factor
```

Where:

* `1.3` for **shallow** (< 70 km)
* `1.1` for **intermediate** (70–300 km)
* `0.9` for **deep** (> 300 km)

**Risk Levels:**

| Score | Level    |
| ----- | -------- |
| ≥ 7.0 | Critical |
| ≥ 5.5 | High     |
| ≥ 4.0 | Moderate |
| < 4.0 | Low      |

This provides an intuitive approximation of potential hazard impact.

---

## 📈 **Sample Visuals**

### Live Dashboard

* Bubble chart: Magnitude vs Time
* Filtered event table
* Real-time risk alert

<img width="1564" height="897" alt="Image" src="https://github.com/user-attachments/assets/085f887a-d367-4114-851b-b0874dc5ed2d" />

### Top 10 View

* Horizontal bar chart
* Ranked magnitude-based comparison

<img width="1562" height="902" alt="Image" src="https://github.com/user-attachments/assets/9372adfe-fd9b-4caa-aab2-ecc648eb81d1" />



* **A polished GitHub description section**
* **Badges (build, version, license, python version)**
* **Sample screenshots**
* **README banner design prompt**

Just say **“Give me badges”** or **“Generate banner prompt”**.
