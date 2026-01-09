## Database Monitoring with Prometheus + Grafana
Objective

Set up monitoring for PostgreSQL, MySQL, and system metrics using Prometheus and Grafana.

You will get:

Prometheus targets UP

Node Exporter for system metrics

Database exporters for MySQL & PostgreSQL

Grafana dashboards for all metrics

Setup Steps
1. Install Prometheus

sudo mkdir /etc/prometheus /var/lib/prometheus

wget https://github.com/prometheus/prometheus/releases/download/v2.48.0/prometheus-2.48.0.linux-amd64.tar.gz

tar xvf prometheus-2.48.0.linux-amd64.tar.gz

sudo cp prometheus-2.48.0.linux-amd64/prometheus /usr/local/bin/

sudo cp -r prometheus-2.48.0.linux-amd64/consoles /etc/prometheus/

sudo cp -r prometheus-2.48.0.linux-amd64/console_libraries /etc/prometheus/

2. Prometheus Config

Create /etc/prometheus/prometheus.yml:

global:
  scrape_interval: 15s

scrape_configs:
- job_name: 'prometheus'
  static_configs:
    - targets: ['localhost:9090']

- job_name: 'node_exporter'
  static_configs:
    - targets: ['localhost:9100']

- job_name: 'postgres_exporter'
  static_configs:
    - targets: ['localhost:9187']

- job_name: 'mysql_exporter'
  static_configs:
    - targets: ['localhost:9104']


Run Prometheus:

prometheus --config.file=/etc/prometheus/prometheus.yml

3. Node Exporter (System Metrics)

wget https://github.com/prometheus/node_exporter/releases/download/v1.6.0/node_exporter-1.6.0.linux-amd64.tar.gz

tar xvf node_exporter-1.6.0.linux-amd64.tar.gz

sudo cp node_exporter-1.6.0.linux-amd64/node_exporter /usr/local/bin/node_exporter

4. PostgreSQL Exporter

wget https://github.com/prometheus-community/postgres_exporter/releases/download/v0.13.0/postgres_exporter_v0.13.0_linux-amd64.tar.gz

tar xvf postgres_exporter_v0.13.0_linux-amd64.tar.gz

sudo cp postgres_exporter /usr/local/bin/postgres_exporter 

export DATA_SOURCE_NAME="postgresql://username:password@localhost:5432/postgres?sslmode=disable"

5. MySQL Exporter

wget https://github.com/prometheus/mysqld_exporter/releases/download/v0.15.0/mysqld_exporter-0.15.0.linux-amd64.tar.gz

tar xvf mysqld_exporter-0.15.0.linux-amd64.tar.gz

sudo cp mysqld_exporter /usr/local/bin/mysqld_exporter

export DATA_SOURCE_NAME="username:password@(localhost:3306)/"



6. Grafana Setup

sudo apt-get install -y grafana

sudo systemctl enable grafana-server

sudo systemctl start grafana-server


Open Grafana at http://localhost:3000

Login: admin/admin

Add Prometheus as data source: http://localhost:9090

Import dashboards:

System Metrics: Node Exporter Full

PostgreSQL Metrics: PostgreSQL Overview

MySQL Metrics: MySQL Overview

Dashboards

System Metrics → CPU, Memory, Disk, Network

PostgreSQL Metrics → Connections, Queries/sec, Replication

MySQL Metrics → Connections, Queries, Slow Queries

## Screenshots


<img width="1920" height="978" alt="prometheus-targets" src="https://github.com/user-attachments/assets/8cf8fd6c-b992-4a83-87bc-4c349860bbf0" />

All targets UP

#### system-dashboard
<img width="1920" height="975" alt="system-dashboard" src="https://github.com/user-attachments/assets/87659687-e18c-47d4-86e5-d0e11ef15e5e" />

#### postgres-dashboard
<img width="1920" height="975" alt="postgres-dashboard" src="https://github.com/user-attachments/assets/482d3487-6e7f-4db7-84bc-1431475205fa" />

#### mysql-dashboard
<img width="1920" height="988" alt="mysql-dashboard" src="https://github.com/user-attachments/assets/19c04e13-0b99-4804-ba8d-0041be1e9ece" />

### Conclusion

The monitoring stack is successfully set up with Prometheus and Grafana.
All targets are UP, and dashboards for system metrics, PostgreSQL, and MySQL are working correctly.
This setup allows easy monitoring and visualization of database and system performance in real-time.


