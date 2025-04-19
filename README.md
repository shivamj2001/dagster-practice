# NYC Taxi Data Pipeline with Dagster

## Overview
A production-ready data pipeline built with Dagster that processes and analyzes NYC taxi trip data. This project demonstrates how to build robust data pipelines by representing them as data assets and implementing proper orchestration.

## Project Architecture
![Asset Lineage](screenshots/asset_lineage.png)

The pipeline consists of several key components:

### Data Assets
- `taxi_trips_file`: Raw taxi trip data ingestion
- `taxi_zones_file`: NYC taxi zone information
- `taxi_trips`: Processed trip data in DuckDB
- `taxi_zones`: Processed zone information
- `manhattan_stats`: Aggregated statistics for Manhattan
- `manhattan_map`: Visualization of trip patterns
- `trips_by_week`: Weekly trip metrics

### Automation
![Automation Setup](screenshots/automation.png)
- `trip_update_job_schedule`: Runs on day 5 of each month
- `weekly_update_job_schedule`: Runs every Monday
- `adhoc_request_sensor`: Event-driven processing

### Visualizations
![Manhattan Trip Heatmap](screenshots/manhattan_heatmap.png)
The heatmap visualization shows the density of taxi trips across different zones in Manhattan, with colors indicating the number of trips (ranging from ~50,000 to ~400,000 trips).

## Technical Implementation

### Resources
![Database Resource](screenshots/database_resource.png)
- DuckDB for efficient data storage and querying
- GeoPandas for geospatial analysis
- Matplotlib for visualization

### Project Structure
```python
dagster_essentials/
├── assets/
│   ├── trips.py      # Taxi trip data processing
│   ├── metrics.py    # Analytics and visualizations
│   └── requests.py   # Ad-hoc request handling
├── resources/        # Database configurations
├── jobs/            # Job definitions
├── schedules/       # Scheduling logic
└── sensors/         # Event triggers
```

### Testing
The project includes comprehensive tests in `dagster_essentials_tests/` covering:
- Unit tests for each component
- Integration tests for data pipeline
- Test fixtures and utilities

## Setup and Usage

1. Install dependencies:
```bash
pip install dagster dagster-webserver dagster-duckdb duckdb pandas geopandas matplotlib
```

2. Run the Dagster UI:
```bash
dagster dev
```

3. Open http://localhost:3000 with your browser to see the project.

> [!NOTE]
> Running `dagster dev` will put you in the starter Dagster project. To see any of the completed lessons execute:
> `dagster dev -m dagster_essentials.completed.lesson_{LESSON NUMBER}.definitions`

## Completed Code Reference
If you need to reference the completed code for each lesson:
