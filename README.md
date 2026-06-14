# US Domestic Airline Flights Performance Dashboard

> An interactive analytics dashboard monitoring and reporting US domestic airline flight performance, delay patterns, cancellations, and route-level statistics from 2005 to 2020.

[![Language](https://img.shields.io/badge/Language-Python%203.x-blue?style=flat-square)](https://www.python.org/)
[![Framework](https://img.shields.io/badge/Framework-Plotly%20Dash-purple?style=flat-square)](https://dash.plotly.com/)
[![Data](https://img.shields.io/badge/Data-DOT%20BTS%202005--2020-green?style=flat-square)]()

---

## Overview

This project builds an **interactive Plotly Dash dashboard** for analyzing US domestic airline flight performance data from the **Bureau of Transportation Statistics (BTS)**, covering years 2005–2020. The dashboard allows airline operations analysts, researchers, and aviation enthusiasts to interactively explore flight reliability, delay causes, cancellation trends, and route performance — filtering dynamically by year and airline.

**Goal:** Improve flight reliability insights to enhance customer satisfaction and operational efficiency for reporting airlines.

---

## Dataset

- **Source:** US Department of Transportation — Bureau of Transportation Statistics
- **Year range:** 2005 – 2020 (16 years)
- **Granularity:** Monthly aggregates per airline and route
- **Key fields:** Carrier code, origin/destination state, flight counts, cancellation category, delay type (carrier, weather, NAS, security, late aircraft), average flight time

---

## Dashboard Reports

### Report 1: Yearly Airline Performance Report

For a user-selected year, the dashboard renders 5 interactive visualizations:

| Chart | Type | Insight |
|---|---|---|
| Cancellations by category | Bar chart | Carrier vs. Weather vs. NAS vs. Security cancellations |
| Average flight time by airline | Line chart | Which carriers operate the longest/shortest routes on average |
| Diverted airport landings | Pie chart | % of diverted landings per reporting airline |
| Flights from each state | Choropleth map | Geographic origin volume across the continental US |
| Flights by airline per destination state | Treemap | Airline-to-state routing breakdown |

### Report 2: Yearly Average Flight Delay Statistics

For a user-selected year, 5 delay charts render monthly trends:

| Delay Type | Description |
|---|---|
| **Carrier delay** | Delays caused by airline operations (maintenance, crew, aircraft cleaning) |
| **Weather delay** | Delays caused by significant meteorological conditions |
| **NAS delay** | National Air System delays (ATC, heavy traffic, non-extreme weather) |
| **Security delay** | Terminal evacuation, re-boarding, long security queues |
| **Late aircraft delay** | Knock-on delays from previous flight arriving late |

---

## Technical Architecture

```
[User: Year Dropdown]
        ↓
[Dash Callback: update_input_container()]
        ↓
[Data Filtering: Pandas groupby / pivot on year]
        ↓
[Plotly Figure Generation]
   ├─ Bar (cancellations)
   ├─ Line (avg flight time)
   ├─ Pie (diversions)
   ├─ Choropleth (state map)
   └─ Treemap (airline×state)
        ↓
[Dash Layout: dcc.Graph × 10 panels]
```

**Stack:**
- `Plotly` for all chart types (bar, line, pie, choropleth, treemap)
- `Dash` for reactive web app with dropdown callbacks
- `Pandas` for data loading, year filtering, and groupby aggregation
- `Jupyter Notebook` for exploratory pre-analysis

---

## Getting Started

```bash
git clone https://github.com/tamer017/US-domestic-airline-flights-performance.git
cd US-domestic-airline-flights-performance
pip install pandas plotly dash jupyter

# Run the dashboard
python app.py
# Open http://127.0.0.1:8050 in your browser
```

---

## Key Insights (Sample Findings)

- **Carrier delays** account for the largest share of total delay minutes across most airlines
- **Weather delays** peak in December–January (winter) and June–August (summer storms)
- **Southwest Airlines (WN)** and **Delta (DL)** dominate volume by flights-from-state
- Cancellation rates spiked significantly in **2020** due to COVID-19 travel restrictions
- **NAS delays** have consistently decreased post-2012 due to NextGen ATC modernization

---

## Skills Demonstrated

`Interactive Dashboard` `Plotly` `Dash` `Pandas` `Data Visualization` `Transportation Analytics` `Choropleth Maps` `Treemaps` `Callback Architecture` `Python`
