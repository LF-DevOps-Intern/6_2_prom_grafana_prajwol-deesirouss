[Assignment's Answer in PDF with ScreenShots](https://github.com/LF-DevOps-Intern/6_2_prom_grafana_prajwol-deesirouss/blob/main/Prometheus%26Grafana's%20Answer%20In%20PDF%20_%20withScreenshots.pdf)

# 6_2_Prom_Grafana_Prajwol
Assignment for Prometheus &amp; Grafana for Week 6 Day 2

Tasks:

1. Install Prometheus Server
- Configuration basic authentication username/password
- Screenhot of login prompt while trying to access prometheus
- Screenshot of prometheus dashboard
# [Task 1 Answer in PDF with ScreenShots](https://github.com/LF-DevOps-Intern/6_2_prom_grafana_prajwol-deesirouss/blob/main/1/1-Prometheus%26Basic-Auth.pdf)

2. Install node exporter on another machine than the server
- Add that machine target to server configuration
- Share screenshot from status->targets to show the available nodes
- Share configuration of node exporter & prometheus server
# [Task 2 Answer in PDF with Screenshots](https://github.com/LF-DevOps-Intern/6_2_prom_grafana_prajwol-deesirouss/blob/main/2/2-NodeExporter%26Targets.pdf)

3. Install grafana server on same server as prometheus 
- Add prometheus data source to grafana, should be connected through basic auth
- Screenshot of working data source config
- Import & apply dashboard for node_exporter
- Screenshot of dashboard of nodes with live metrics shown.
# [Task 3 Answer in PDF with ScreenShots](https://github.com/LF-DevOps-Intern/6_2_prom_grafana_prajwol-deesirouss/blob/main/3/3-Grafana-DataSource-Node-Exporter.pdf)

Sample Server Config:
global:
  scrape_interval: 10s
  scrape_timeout: 6s

scrape_configs:
  - job_name: 'prometheus'
    scrape_interval: 5s
    static_configs:
      - targets: ['10.10.4.105:9090']

  - job_name: 'node'
    scrape_interval: 5s
    static_configs:
      - targets: ['10.10.5.218:9100','10.10.4.105:9100']

  - job_name: 'docker'
    scrape_interval: 5s
    static_configs:
      - targets: ['10.10.5.218:9323']

  - job_name: 'mysql'
    scrape_interval: 5s
    static_configs:
      - targets: ['10.10.5.218:9104']

rule_files:
  - "prometheus-rules.yml"

alerting:
  alertmanagers:
  - static_configs:
    - targets: ['localhost:9093']


