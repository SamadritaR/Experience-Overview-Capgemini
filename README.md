# Experience Overview : Capgemini
#  Capgemini Experience: Senior Analyst | DevOps Engineer 

Between September 2021 and June 2024, I worked as a **Senior Analyst** at Capgemini Technology Services across two major workstreams:

- **Jira (Atlassian):** Workflow design, automation, and sprint analytics for a large multi-team program.
- **Mercedes-Benz Global Ordering Platform:** Reliability & platform operations with ML-assisted detection and infrastructure automation.

My role combined **DevOps automation**, **machine learning integration**, and **large-scale system optimization** for Mercedes-Benz, alongside **business analysis**, **data analysis**, and **product execution** on the Jira stack.

This page covers what I actually shipped—problems solved, how I built the solutions, the tools I used—and the measurable outcomes.

---
## PROJECT I: Jira (Atlassian) [December 2021 - November 2022]
**Workflow Design, Automation & Sprint Analytics**

- **Workflow ownership:** Consolidatedand designed new workflows and reduced statuses **16 → 7**, simplifying ticket transitions. Standardized story/bug templates and **acceptance criteria** to cut thrash and clarify handoffs.
- **Automation & integrations:** Connected **Jira ↔ Confluence ↔ GitLab** and built GitLab CI automations for triage, SLA timers, release-note publishing, and routine updates.
- **Backlog & documentation:** Groomed epics into right-sized stories, phased features across sprints, and documented process steps in Confluence using a **modular/compartmentalized** style; communicated changes to stakeholders.
- **Impact:** Reduced sprint overruns and improved delivery predictability across **3 teams (120+ engineers & executives)**.

## PROJECT II: Mercedes-Benz Global Ordering Platform [December 2022 - June 2024]

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
## 2. VM Configuration & Platform Support for Global Ordering (Ansible + Docker)

**Context:**  
The Global Ordering (GO) platform relied on a large fleet of virtual machines supporting critical services. Inconsistent VM configuration and environment-specific setup issues were impacting platform stability and increasing operational overhead during deployments and incident response.

**How I did it:**  
- Used **Ansible** to standardize configuration across GO platform virtual machines, including service initialization, dependency management, environment variables, and access controls.  
- Maintained **Ansible playbooks** to support repeatable VM setup during platform updates, node replacements, and recovery scenarios, ensuring parity between production and non-production environments.  
- Supported **Docker-based services** running on GO platform VMs by validating container runtime configuration, host-level dependencies, and resource settings required for stable operation.  
- Worked closely with GO platform application teams to troubleshoot VM- and container-related issues, isolating failures caused by configuration drift, dependency mismatches, or host-level constraints.

**Result:**  
Improved configuration consistency across GO platform VMs, reduced environment-specific issues during deployments and recovery events, and increased overall platform stability for customer-facing services.

---

##  3. Predictive Resource Management (EDA + XGBoost + TensorFlow)

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

##  4. Real-Time Anomaly Detection (PyTorch + DBSCAN + KMeans)

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

## 5. Monitoring & Observability Stack (Docker Compose + Prometheus + Grafana + ELK)

**Context:**  
There were too many siloed dashboards — we needed a unified, real-time view of system health, migration logs, and application latency.

**How I did it:**

- Deployed **Prometheus + Grafana stacks** via **Docker Compose**, with job-specific exporters (node, VM, infra, app layer).
- Built custom dashboards to visualize CPU/mem trends, network spikes, and alert conditions.
- Integrated **ELK Stack (Elasticsearch, Logstash, Kibana)** for full-text log search and live filtering of errors.
- Used **Portainer** to manage containers visually during rapid debugging and testing.

**Result:**  
Reduced root cause analysis time by 70%, improved alerting coverage across distributed systems.

---
## 6. Container Monitoring & System Observability (cAdvisor + Node Exporter + ELK)

**Context:**  
We were running containerized applications across multiple VMs, but didn’t have a clean, unified view into CPU/memory usage, disk I/O, or container-level resource bottlenecks.  
Our team needed a way to monitor container health, performance trends, and flag spikes **before** they became service issues.

---

###  How I Did It

1. **Setup cAdvisor on each container host**
   - Used Docker to deploy cAdvisor containers across all VM instances.
   - Exposed metrics at port `:8080` and mounted Docker socket for access to live container stats.
   - Metrics included: CPU usage, memory limit vs consumption, I/O stats, and container uptime.

2. **Integrated with Prometheus**
   - Added `cAdvisor` as a scrape target in Prometheus configuration.
   - Defined scrape intervals based on container volatility and load conditions.
   - Used `prometheus.yml` config to group container metrics by VM region and environment tag (e.g., staging, prod).

3. **Visualized in Grafana**
   - Created Grafana dashboards to monitor:
     - Top resource-consuming containers
     - CPU throttling
     - Memory spikes vs limits
     - Container restart trends
   - Added annotations from deployment logs to correlate code pushes with performance issues.

4. **Extended logging with ELK Stack**
   - Used **Logstash** to collect container logs and push them to **Elasticsearch**.
   - Set up dashboards in **Kibana** for full-text search and filtering by container ID, image, or log level.
   - Combined this with system logs to give full observability across container + VM.

5. **Used Node Exporter for host-level metrics**
   - Monitored host metrics (CPU, disk I/O, swap, file descriptors) via Node Exporter.
   - Overlaid these on Grafana dashboards to correlate system-level and container-level behavior.

---

###  Outcome

- Enabled live observability across 100+ containers  
- Improved debugging efficiency during on-call rotations by **>60%**  
-  Helped DevOps proactively manage workloads and spot memory leaks or crash loops early  
-  Supported transition to GitOps by making container health part of the CI/CD health checks

---

Tools Used:
- `cAdvisor` for per-container resource monitoring  
- `Prometheus` + `Node Exporter` for system metrics  
- `Grafana` for visual dashboards  

## 7. Data Engineering & Log Processing (Hadoop + AWS S3 + Hive + SQL)

**Context:**  
We had terabytes of logs across VM environments — impossible to process with standard tools. I helped build a scalable pipeline for log analytics.

**How I did it:**

- Ingested logs from **AWS S3**, parsed using Python scripts with regular expressions and stored structured outputs.
- Ran processing jobs using **Hadoop MapReduce** and queried summaries via **Hive**.
- Used **PostgreSQL/MSSQL/Snowflake** to store aggregated metrics for later BI consumption.

**Result:**  
 Reduced log processing time by 60%, enabled ML pipelines to pull directly from structured summaries.

---

##  8. Sprint Analytics + Jira Automation (SQL + Power BI + API Scripting)

**Context:**  
PMs wanted visibility into sprint health and backlog severity, but data was scattered across Jira, GitHub, and Slack.

**How I did it:**

- Built SQL pipelines to query Jira API data for issue type, cycle time, and velocity metrics.
- Developed **Power BI dashboards** for sprint tracking and stakeholder reporting.
- Automated updates via **Python-based API triggers** — syncing Confluence, Slack, and GitHub updates in real time.

**Result:**  
Reduced backlog review time and helped product managers reduce sprint overruns by 25%.

---

Alongside these , I have also :

- Simplified Jira Workflows
- Created Project Customizations
- Worked on Numerous Docker Compose Files
- Worked on various Infrastructure enhancement tasks 



---
Connect with me on [LinkedIn](https://www.linkedin.com/in/samadrita-roy-chowdhury)  
Back to Main Portfolio: [GitHub Profile](https://github.com/SamadritaR)
