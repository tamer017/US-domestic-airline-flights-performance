# US Domestic Airline Flights Performance Dashboard

> **Interactive Plotly Dash dashboard analyzing US domestic airline performance from 2005–2020 with dual-report architecture: yearly performance summaries and monthly delay breakdowns.**

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![Plotly](https://img.shields.io/badge/Plotly-Dash-blue.svg)](https://dash.plotly.com/)
[![Data](https://img.shields.io/badge/Data-BTS_2005--2020-green.svg)](https://www.transtats.bts.gov/)

---

## Overview

This project builds a **multi-page interactive dashboard** for exploring US domestic airline performance data sourced from the Bureau of Transportation Statistics (BTS). Users can select any year and airline to dynamically generate two types of reports covering flight performance and delay root-cause analysis.

---

## Dashboard Architecture

```
User Input: Year + Airline Selector
           │
    ┌───────┼───────┐
    │             │
Report 1      Report 2
Yearly        Monthly
Performance   Delay
    │         Analysis
    │             │
5 Charts      5 Charts
```

---

## Report 1: Yearly Airline Performance

| Chart | Type | Insight |
|---|---|---|
| Monthly flight volume | **Bar chart** | Seasonal demand patterns |
| Average flight distance | **Line chart** | Route network evolution |
| Cancellation rate | **Pie chart** | Cancel reason breakdown |
| Diverted flights by state | **Choropleth map** | Geographic diversion hotspots |
| Flights by reporting airline | **Treemap** | Market share visualization |

## Report 2: Monthly Delay Root-Cause Analysis

Breaks down average delay minutes per carrier by cause:

| Delay Type | Description |
|---|---|
| **Carrier delay** | Airline-controllable issues (maintenance, crew) |
| **Weather delay** | Meteorological events |
| **NAS delay** | National Airspace System (ATC, airport ops) |
| **Security delay** | Security screening issues |
| **Late aircraft delay** | Cascading delays from previous flight |

---

## Key Findings

- **2020 COVID spike**: Cancellation rates surged 15× above historical average in April 2020
- **Post-2012 NAS reduction**: FAA NextGen ATC modernization reduced NAS delays by ~23%
- **Late aircraft cascade**: Accounts for ~38% of all delay minutes — the largest single cause
- **Southwest dominance**: Highest flight volume treemap share throughout 2010s
- **Alaska/Hawaii diversions**: Disproportionate diversion rates due to limited alternate airports

---

## Callback Architecture

```python
@app.callback(
    [Output('bar-plot', 'figure'),
     Output('line-plot', 'figure'),
     Output('pie-chart', 'figure'),
     Output('choropleth', 'figure'),
     Output('treemap', 'figure')],
    [Input('year-dropdown', 'value'),
     Input('report-type', 'value')]
)
def update_charts(selected_year, report_type):
    filtered_df = df[df['Year'] == selected_year]
    # ... generate 5 charts
    return bar_fig, line_fig, pie_fig, map_fig, tree_fig
```

---

## Installation

```bash
git clone https://github.com/tamer017/US-domestic-airline-flights-performance.git
cd US-domestic-airline-flights-performance
pip install dash plotly pandas numpy
python app.py
# Open http://localhost:8050
```

---

## Skills & Concepts

`Plotly Dash` `Interactive Dashboards` `Choropleth Maps` `Treemaps` `Callback Architecture` `Transportation Analytics` `BTS Data` `Time-Series Visualization` `Multi-Chart Layout`

---

## Author

**Ahmed Tamer Assy** — [GitHub](https://github.com/tamer017) | Machine Learning Researcher @ Volkswagen AG
