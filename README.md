
# Refinery Process Performance & Production Analytics

An educational refinery process performance and production analytics project built using Excel, Power Query, and Microsoft Power BI.

> **Data disclaimer:** This project uses a synthetic refinery process dataset developed for educational and portfolio purposes. It does not represent actual refinery operating records or validated industry benchmarks.

## Project Overview

The project explores how process and production data can be organised, cleaned, analysed, and presented through an interactive Power BI dashboard.

The raw dataset contains 2,166 records covering 90 days, from 1 January 2026 to 31 March 2026, across three processing units:

- CDU-01
- VDU-01
- NHT-01

## Objectives

- Prepare a structured process dataset for analysis.
- Examine feed volume and throughput.
- Review process temperature and pressure.
- Analyse energy consumption and energy intensity.
- Explore downtime patterns.
- Compare reported product yields across products, units, shifts, and time.

## Tools Used

- **Microsoft Excel** — Initial data inspection and cleaning.
- **Power Query** — Data preparation and product-yield reshaping.
- **Microsoft Power BI** — Data modelling, DAX measures, and dashboard development.

## Data Preparation

The observation-level cleaned dataset is loaded into Power BI as `Refinery Data`.

A separate Power Query reference, `Product Yield Data`, is created by unpivoting the four product-yield columns. This supports product-level analysis while preserving the original observation-level table.

See `docs/data_dictionary.csv` for field descriptions and `docs/data_cleaning_log.md` for cleaning notes.

The raw dataset contains **2,166 records**. After removing **6 exact duplicates**, the cleaned dataset contains **2,160 records (720 per unit)**.

The **24 blank values** across temperature, pressure, and energy columns were left blank.

## Dashboard Pages

1. **Executive Overview** — Feed, throughput, efficiency, energy, and downtime indicators.
2. **Unit & Process Performance** — Processing-unit comparison and process conditions.
3. **Energy & Operational Reliability** — Energy consumption, energy intensity, and downtime analysis.
4. **Product Yield Analysis** — Reported product yields by product, processing unit, shift, and week.

## DAX Measures

The measures used in the report are documented in `docs/dax_measures.txt`.

## Repository Structure

```text
Refinery-Process-Analytics/
├── data/
│   ├── refinery_raw_data.csv
│   ├── refinery_raw_data.xlsx
│   ├── refinery_cleaned_data.csv
│   └── refinery_cleaned_data.xlsx
├── powerbi/
│   └── Refinery_Process_Performance_Analytics.pbix
├── screenshots/
│   ├── 01_Executive_Overview.png
│   ├── 02_Unit_Process_Performance.png
│   ├── 03_Energy_Operational_Reliability.png
│   └── 04_Product_Yield_Analysis.png
├── docs/
│   ├── data_dictionary.csv
│   ├── data_cleaning_log.md
│   └── dax_measures.txt
└── README.md
```

## Limitations

- The dataset is synthetic and intended for learning and demonstration.
- Results are descriptive analyses of generated data, not operational conclusions about a real refinery.
- The project does not establish process safety limits, equipment design limits, or industry performance benchmarks.

## Conclusion

This project demonstrates a learning workflow for preparing process data, building analytical measures, and communicating refinery performance indicators through an interactive dashboard.
