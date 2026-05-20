# Community_health_dashboard
End-to-end public health data pipeline for a County, CA — automated API ingestion, Python ETL, Power BI star schema, integrating 50+ health, economic, and social indicators from federal and state APIs into an interactive Power BI dashboard.
Built as a portfolio project demonstrating capabilities for Research Data Analyst/Specialist roles.
## Project Context
This dashboard was built as an independent learning project to demonstrate end-to-end public health data analysis capabilitie. It deliberately uses transparent methodologies, public data sources, and free or low-cost tools to show that high-quality community health dashboards can be built without expensive proprietary platforms.
The pipeline architecture follows the bronze/silver/gold data layering pattern used by professional data engineering teams, separating raw ingestion from processing from final presentation.
## Overview
This project develops a community health analytics platform using open-source tools and publicly available government data sources. The pipeline ingests and transforms multi-source health data following CDPH statistical standards and delivers an interactive Power BI dashboard with county-, state-, and national-level benchmarking.
#### Key components include:
Automated Python-based data ingestion pipeline
Star schema data model for analytics and reporting
Interactive Power BI dashboard with drill-through navigation
10 years of historical health data analysis (2014–2024)
All sources are free, publicly available government datasets. API keys (where required) are stored in a local .env file, not committed to the repository.
## Indicators Tracked
The dashboard currently displays demographic and socioeconomic indicators across these categories:
Age & Sex
Race & Ethnicity
Income & Poverty
Housing
Education
Health & Disability
Labor Force
Households & Language

## Architecture
Federal & State APIs (Census ACS, SAHIE, CBP)
              |
              v
Python Ingestion Layer
  - Automated fetch scripts (JupyterLab notebooks)
  - Multi-year, multi-geography support
  - Handles B-tables, S-tables, and DP-tables
  - Census suppression code cleanup
              |
              v
Raw Data Layer (Parquet)
  - data/raw/census/  - ACS data
  - data/raw/sahie/   - Health insurance data
  - data/raw/cbp/     - Employment data
              |
              v
Processing Layer
  - Rate calculations (poverty, homeownership, age brackets)
  - Geography combining (Tehama + California + US)
  - Year-over-year change calculations
              |
              v
Final Dataset (Parquet)
  - data/final/tehama_dashboard_data.parquet
  - Single source for Power BI dashboard
              |
              v
Power BI Dashboard

## Dashboard Design
The dashboard follows a three-tier navigation pattern:
Level 1 — Home Page
18 category tiles covering health outcomes, economic conditions, community indicators, education, and environmental health. Users click a category to drill down.
Level 2 — Category Overview
For Demographics, displays all indicators in a comparison table showing County value, prior year value, California benchmark, US benchmark, and a 10-year sparkline trend.
Level 3 — Indicator Detail
A single dynamic template page that updates based on the indicator selected. Shows large KPI cards (COunty, Prior Year, CA, US), a 10-year trend line chart with multi-geography comparison, and a year-over-year change chart.

## Tech Stack
Language               Python 3.11+
Data manipulation      pandas, numpy
API calls              requests
File format            Parquet (via pyarrow)
Notebooks              JupyterLab
Version control        Git, GitHub
Visualization          Power BI 
Configuration          python-dotenv

## Acknowledgments
Built with publicly available data from the US Census Bureau, including the American Community Survey, Small Area Health Insurance Estimates program, and County Business Patterns program. Methodology informed by guidance from the California Department of Public Health and County Health Rankings & Roadmaps.
