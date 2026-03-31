# Dynatrace-Observability-Demo-Custom-Metrics-Architecture
Agentless Dynatrace observability demo using custom metrics ingestion with a Python application.

# Dynatrace Observability Demo – Agentless Custom Metrics with Python

## Description

Agentless Dynatrace observability demo using custom metrics ingestion with a Python application.

This repository demonstrates a simple and effective observability pattern using Dynatrace Metrics API v2 without relying on Dynatrace OneAgent.

---

## Purpose

This project illustrates:

- Agentless observability architecture
- Custom metrics ingestion into Dynatrace
- Metric naming best practices
- A reusable Python-based ingestion pattern
- Architecture-focused observability design

It is suitable for portfolio presentation and reflects real-world monitoring scenarios.

---

## Architecture Overview

[ Python Application ]
        |
        | Dynatrace Metrics API v2
        |
[ Dynatrace SaaS ]
        |
        - Custom Metrics
        - Dashboards
        - Alerting / SLOs

Key characteristics:
- No agent dependency
- Decoupled monitoring approach
- Applicable to legacy systems, batch jobs, containers, and sidecar patterns

---

## Custom Metrics

The application simulates a backend service and sends the following metrics:

- custom.app.response_time (Gauge)  
  Application response time in milliseconds

- custom.app.error_count (Counter)  
  Number of simulated application errors

- custom.app.cpu_usage (Gauge)  
  Simulated CPU utilization percentage

All metrics use the `custom.*` namespace following Dynatrace best practices.

---

## Python Application

Location:
app/send_metrics.py

Responsibilities:
- Generate synthetic application metrics
- Send metrics using Dynatrace Metrics API v2
- Run continuously at a fixed interval
- Use environment variables for secure configuration

The application is stateless and easy to extend or containerize.

---

## Prerequisites

- Dynatrace SaaS environment
- API Token with Metrics Ingest permission
- Python 3.8 or newer
- Network access to Dynatrace API endpoint

---

## Setup

1. Clone the repository

git clone https://github.com/<your-username>/dynatrace-observability-demo.git  
cd dynatrace-observability-demo/app

2. Install dependencies

pip install -r requirements.txt

3. Configure environment variables

export DYNATRACE_URL="https://<your-environment>.live.dynatrace.com"  
export DYNATRACE_TOKEN="dt0c01..."

API tokens must not be committed to source control.

---

## Running the Application

python send_metrics.py

Metrics are sent every 10 seconds.

Successful ingestion returns HTTP status code 202 Accepted.

---

## Viewing Metrics in Dynatrace

1. Open Metrics Explorer
2. Search for custom.app.*
3. Create charts or dashboards using the ingested metrics

These metrics can be reused for alerting, SLOs, and dashboards.

---

## Repository Structure

dynatrace-observability-demo/
|
|-- README.md
|-- architecture/
|   |-- architecture.png
|-- app/
|   |-- send_metrics.py
|   |-- requirements.txt
|-- docs/
    |-- dynatrace-setup.md

---

## Applicable Use Cases

- Legacy applications without agents
- Batch jobs and schedulers
- Serverless or edge workloads
- Custom business KPIs
- SAP and enterprise environments requiring agentless monitoring

---

## Future Improvements

- Dynatrace dashboard export
- Threshold-based alerting
- SLO definitions
- Dockerized execution
- Log ingestion
- Metric dimensions such as environment, service, or region

---

## Author

Thiago Farias  
Cloud Engineering – Observability – Resilience  
São Paulo, Brazil
