# Security Log Analyzer

A Python command-line project for parsing web-server logs, summarising access patterns, identifying suspicious activity, calculating heuristic threat scores, and producing CSV, JSON, and interactive HTML reports.

## Implemented features

- Parses the included combined-format sample log
- Counts requests by IP address and endpoint
- Detects repeated failed-login activity
- Applies Isolation Forest anomaly detection to request patterns
- Calculates configurable heuristic threat scores
- Retrieves optional IP geolocation through `ipapi.co`
- Writes structured CSV and JSON reports
- Generates Plotly request-distribution and endpoint heatmap visualisations

The anomaly and prediction outputs are exploratory heuristics. They are not a substitute for a security information and event management platform or a professionally calibrated detection model.

## Run locally

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
python main.py
```

Generated files are written to the repository directory. Geolocation requires internet access and depends on the availability and terms of the external `ipapi.co` service.

## Project structure

```text
main.py                Orchestrates analysis and reporting
loganalyzer.py         Log parsing and aggregate analysis
threat_detection.py    Anomaly detection and threat scoring
visualization.py       Plotly HTML reports
utils.py               Geolocation and JSON report helpers
sample.log             Demonstration input
```

## Current limitations

- Input parsing targets one log structure and needs hardening for arbitrary formats.
- Thresholds and threat weights are demonstration values, not production-calibrated rules.
- Network requests do not currently include retry, timeout, or rate-limit handling.
- The project does not yet include automated tests or a streaming ingestion path.
