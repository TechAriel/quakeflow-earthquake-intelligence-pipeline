# Worldwide – Real-Time Earthquake Intelligence Pipeline

This is an end-to-end data engineering and analytics project built on Microsoft Fabric.
It ingests real-time earthquake data, processes it using a Medallion architecture, and delivers actionable insights through an interactive Power BI dashboard.

---

## Overview

This project uses earthquake data from the **United States Geological Survey (USGS)** API and transforms it into structured, analytics-ready datasets.

The pipeline demonstrates how modern data platforms unify:

* Data ingestion
* Transformation
* Orchestration
* Business intelligence

---

## Architecture

```
USGS API
   ↓
Bronze Layer (Raw JSON - Lakehouse Files)
   ↓
Silver Layer (Cleaned & Structured Delta Table)
   ↓
Gold Layer (Enriched & Business Logic Applied)
   ↓
Power BI Dashboard
```

---

## Key Features

*  API-based data ingestion (real-world data)
*  Medallion Architecture (Bronze → Silver → Gold)
*  Apache Spark transformations
*  Automated pipeline using Data Factory Pipeline
*  Interactive Power BI reporting
*  Geospatial analysis with country mapping

---

##  Bronze Layer – Raw Ingestion

* Fetch data from USGS API using Python
* Store raw JSON files in Lakehouse
* Parameterized ingestion using:

  * `start_date`
  * `end_date`

Output:

```
/Files/start_date_earthquake_data.json
```

---

## Silver Layer – Data Transformation

* Flatten nested JSON structure
* Extract relevant attributes:

  * Magnitude
  * Location
  * Coordinates
  * Timestamp
* Convert Unix timestamps to readable format

Output:

```
earthquake_events_silver (Delta Table)
```

---

## Gold Layer – Data Enrichment

* Add country codes via reverse geocoding
* Classify earthquake significance:

  * Low (<100)
  * Moderate (100–500)
  * High (>500)

Output:

```
earthquake_events_gold (Delta Table)
```

---

## Pipeline Orchestration

* Built using Microsoft Fabric Data Factory Pipeline

* Executes:

  1. Bronze Notebook
  2. Silver Notebook
  3. Gold Notebook

* Uses dynamic parameters:

  * `utcNow()`
  * `addDays()`

* Scheduled for daily execution

---

## Power BI Dashboard

### Features:

*  Map visualization of earthquakes
*  Significance classification (color-coded)
*  Bubble size based on magnitude/significance
*  Filters:

  * Date range
  * Classification

---

## Tech Stack

* Microsoft Fabric
* Apache Spark (PySpark)
* Python (Requests, JSON)
* Data Factory Pipelines
* Power BI
* Delta Lake

---

## Getting Started

1. Create a Fabric Workspace
2. Create a Lakehouse
3. Build Medallion architecture notebooks (Bronze, Silver, Gold)
4. Build Data Factory pipeline
5. Schedule daily execution
6. Connect Power BI to semantic model

---

## Key Concepts Demonstrated

* Medallion Architecture
* Incremental Data Processing
* API Integration
* Data Pipeline Automation
* Lakehouse + BI Integration

---

## Future Improvements

* Streaming ingestion (real-time updates)
* Data quality validation layer
* Monitoring & alerting
* Advanced geospatial analytics
* Magnitude trend analysis

---

## Why This Project Matters

It showcases the ability to:

* Build production-style data pipelines
* Work with real-world APIs
* Design scalable data architectures
* Deliver business-ready insights

---

## Author

Gabriel Oduor
            
Junior Data Engineer
