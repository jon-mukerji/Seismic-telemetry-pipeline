# 🌐 Automated Seismic Telemetry & Visualization Pipeline

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Networking](https://img.shields.io/badge/Networking-API%20Ingestion-brightgreen)
![Infrastructure](https://img.shields.io/badge/Infrastructure-Data%20Pipeline-orange)
![License](https://img.shields.io/badge/License-see%20LICENSE-lightgrey)

## 📌 Overview

This project is an automated data pipeline that ingests, parses, and visualizes large-scale seismic event telemetry. It queries the live [USGS FDSN REST API](https://earthquake.usgs.gov/fdsnws/event/1/) to retrieve geographic and severity data for major seismic events (Magnitude ≥ 5.0) occurring in Japan between 2015 and 2024.

While the data domain is seismology, the pipeline's design borrows heavily from infrastructure and monitoring engineering: resilient API ingestion, structured parsing of nested JSON payloads, and translation of raw event data into interactive, near-real-time visual dashboards.

## 🚀 Core Features

- **Robust API Ingestion** — Uses Python's `requests` library to interface with external endpoints, enforcing connection timeouts and HTTP status validation (`raise_for_status()`) to prevent silent failures on bad or slow responses.
- **Data Parsing & Transformation** — Unpacks complex, nested JSON payloads into structured tabular formats (Pandas) and geographic objects (GeoPandas).
- **Automated Event Mapping** — Generates high-resolution static maps (Matplotlib, Contextily) and interactive web-based heatmaps (Folium).
- **Multivariate Symbolization** — Clusters and visualizes data points using severity-based scaling (magnitude and focal depth), useful for quickly triaging which events matter most in a large dataset.

## 🛠️ Technology Stack

| Category | Tools |
|---|---|
| Language | Python 3.x |
| Network & API | `requests`, RESTful architecture, JSON/GeoJSON parsing |
| Data Processing | `pandas`, `numpy`, `geopandas` |
| Visualization | `matplotlib`, `folium` (HeatMap, MarkerCluster), `contextily` |

## ⚙️ Installation and Execution

1. **Clone the repository:**
   ```bash
   git clone https://github.com/jon-mukerji/seismic-telemetry-pipeline.git
   cd seismic-telemetry-pipeline
   ```

2. **Set up a virtual environment:**
   ```bash
   python -m venv venv
   source venv/bin/activate   # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Run the pipeline:**
   ```bash
   jupyter notebook notebooks/seismic_analysis.ipynb
   ```
   This executes the API pull and generates the localized maps.

## 🔎 Transferable Methodologies

Although built for seismic data, several patterns used here map directly onto infrastructure and security monitoring work:

- **Continuous data collection** — programmatically requesting and processing time-series event data on a schedule, rather than as a one-off pull.
- **Fault-tolerant ingestion** — handling network timeouts, malformed payloads, and inconsistent API responses without the pipeline breaking.
- **Actionable visualization** — turning raw coordinate and severity data into maps that let a viewer immediately identify the highest-priority events, rather than reading a table of numbers.

## 👤 About the Author

**Srijan Mukherjee**
- LinkedIn: [linkedin.com/in/srijanmukerji097](https://linkedin.com/in/srijanmukerji097)
- Email: jon.mukerji@gmail.com

Network engineer transitioning into data science and AI, with a background in enterprise networking hardware and infrastructure support (Concentrix-Certified Network Engineer). This project reflects a systems-first approach to data analytics — prioritizing reliable data transport, resilient ingestion, and clear, actionable output.

## 📄 License

See [LICENSE](./LICENSE) for details.
