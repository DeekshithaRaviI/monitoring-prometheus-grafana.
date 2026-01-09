***# Database \& System Monitoring with Prometheus + Grafana***



***## Overview***

***This project monitors \*\*PostgreSQL\*\*, \*\*MySQL\*\*, and system metrics using \*\*Prometheus\*\* and \*\*Grafana\*\*.***



***## Components***

***- \*\*Prometheus\*\*: Collects metrics from exporters***

***- \*\*Grafana\*\*: Displays dashboards***

***- \*\*Node Exporter\*\*: System metrics (CPU, memory, disk)***

***- \*\*PostgreSQL Exporter\*\*: PostgreSQL metrics***

***- \*\*MySQL Exporter\*\*: MySQL metrics***



***## Setup Steps***

***1. Install Prometheus and Grafana.***

***2. Install Node, PostgreSQL, and MySQL exporters.***

***3. Configure Prometheus targets in `prometheus/prometheus.yml`.***

***4. Start all services and import dashboards in Grafana:***

   ***- System Metrics***

   ***- PostgreSQL***

   ***- MySQL***



***---***



***## Screenshots***



***\*\*Prometheus Targets\*\****  

***!\[Prometheus Targets](screenshots/prometheus-targets.png)***



***\*\*System Dashboard\*\****  

***!\[System Dashboard](screenshots/system-dashboard.png)***



***\*\*PostgreSQL Dashboard\*\****  

***!\[PostgreSQL Dashboard](screenshots/postgres-dashboard.png)***



***\*\*MySQL Dashboard\*\****  

***!\[MySQL Dashboard](screenshots/mysql-dashboard.png)***



***---***



***## Files***



***- `prometheus/prometheus.yml` → Prometheus config***  

***- `services/\*.service` → Exporter services***  

***- `screenshots/` → Dashboard images***



