# Experience-Overview---Capgemini
#  Capgemini Experience: DevOps Engineering | AI/ML Infrastructure | Scalable Systems

Between September 2021 and June 2024, I worked as a Senior Analyst at Capgemini Technology Services. My role blended DevOps automation, machine learning integration, and large-scale system optimization for one of our flagship clients: Mercedes-Benz.

This page walks through what I actually did — how I built things, the problems I solved, and the tools I used.

---

##  1. Infrastructure Automation (Groovy + GitLab CI/CD + Cron)

**Context:**  
Manual weekly reboots for VMs (both Linux and Windows) were disrupting workflows and wasting ops time. We needed a safe, repeatable way to automate reboots without risking service downtime.

**How I did it:**

- Wrote **Groovy scripts** that handled service shutdowns, reboot conditions, and fallback safety checks.
- Created **cron jobs** with time-zone-specific triggers to avoid overlaps and ensure distributed coordination.
- Integrated these scripts into **GitLab CI/CD pipelines**, enabling centralized control over deployment and rollback.
- Monitored reboot results using logs and post-deployment health checks.

**Result:**  
 Cut manual overhead by 85% and reduced missed reboots across environments.

---

##  2. Predictive Resource Management (EDA + XGBoost + TensorFlow)

**Context:**  
Our team was facing unpredictable spikes in CPU/memory/disk usage. I built a forecasting system to help autoscale the infrastructure **before** performance bottlenecks hit.

**How I did it:**

- Used **Exploratory Data Analysis (EDA)** on telemetry logs to identify meaningful signals (e.g., CPU load cycles, I/O wait patterns).
- Engineered time-series features and fed them into a **TensorFlow/XGBoost model pipeline**.
- Tuned hyperparameters using grid search, evaluated with MAPE + RMSE.
- Integrated this into a staging environment to simulate predictions on real usage data.
- Connected forecasts to **auto-scaling policies** via config-driven alerts.

**Result:**  
Improved auto-scaling response time by 35% and reduced alert fatigue for the infrastructure team.

---

##  3. Real-Time Anomaly Detection (PyTorch + DBSCAN + KMeans)

**Context:**  
During VM domain migrations (Windows/Linux), unexpected errors would disrupt services. There was no proactive signal for these failures.

**How I did it:**

- Extracted **log features** using Python + regex (patterns, error codes, frequencies).
- Used **unsupervised learning** (DBSCAN + KMeans with PyTorch) to group normal patterns and highlight outliers.
- Deployed these models using Docker containers and integrated them into the pipeline for scheduled batch inference.
- Set thresholds dynamically to adjust for workload volume (avoiding too many false positives).

**Result:**  
 Detected migration issues 60% faster, reducing system downtime by 40%.

---

## 4. Monitoring & Observability Stack (Docker Compose + Prometheus + Grafana + ELK)

**Context:**  
There were too many siloed dashboards — we needed a unified, real-time view of system health, migration logs, and application latency.

**How I did it:**

- Deployed **Prometheus + Grafana stacks** via **Docker Compose**, with job-specific exporters (node, VM, infra, app layer).
- Built custom dashboards to visualize CPU/mem trends, network spikes, and alert conditions.
- Integrated **ELK Stack (Elasticsearch, Logstash, Kibana)** for full-text log search and live filtering of errors.
- Used **Portainer** to manage containers visually during rapid debugging and testing.

**Result:**  
📉 Reduced root cause analysis time by 70%, improved alerting coverage across distributed systems.

---

## 5. Data Engineering & Log Processing (Hadoop + AWS S3 + Hive + SQL)

**Context:**  
We had terabytes of logs across VM environments — impossible to process with standard tools. I helped build a scalable pipeline for log analytics.

**How I did it:**

- Ingested logs from **AWS S3**, parsed using Python scripts with regular expressions and stored structured outputs.
- Ran processing jobs using **Hadoop MapReduce** and queried summaries via **Hive**.
- Used **PostgreSQL/MSSQL/Snowflake** to store aggregated metrics for later BI consumption.

**Result:**  
 Reduced log processing time by 60%, enabled ML pipelines to pull directly from structured summaries.

---

##  6. Sprint Analytics + Jira Automation (SQL + Power BI + API Scripting)

**Context:**  
PMs wanted visibility into sprint health and backlog severity, but data was scattered across Jira, GitHub, and Slack.

**How I did it:**

- Built SQL pipelines to query Jira API data for issue type, cycle time, and velocity metrics.
- Developed **Power BI dashboards** for sprint tracking and stakeholder reporting.
- Automated updates via **Python-based API triggers** — syncing Confluence, Slack, and GitHub updates in real time.

**Result:**  
Reduced backlog review time and helped product managers reduce sprint overruns by 25%.

---



---

## 💬 Final Reflection

This wasn’t just a job — it was a training ground. I didn’t just work with technologies — I learned how to scale systems, automate decisions, and build resilient pipelines.  
Every solution I worked on started with a real pain point. My job was to **make it easier, smarter, and faster** — with code, data, and design thinking.

---
 Connect: [LinkedIn](https://www.linkedin.com/in/samadrita-roy-chowdhury)  

