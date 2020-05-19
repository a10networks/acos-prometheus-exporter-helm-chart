# prometheus-exporter-helm

This repository contains Helm package for A10 ACOS Prometheus exporter.

## More about ACOS Prometheus exporter
The ACOS Prometheus exporter module is responsible for collecting ACOS device stats as metrics. 
- It internally invokes the target ACOS device axAPIs to obtain those statistics and then exposes the respective metrics via HTTP(s) which can be pulled by a Prometheus server. 
- Any visualization client like Grafana can be configured to query the stats from Prometheus server, plot them, set thresholds, configure alerts, create heat maps, generate tables etc. as needed to analyze the ACOS stats.
- The Prometheus server works on a pull-based model and periodically queries the exporter based on interval specified. It runs by default on port 9090. 
- End users/systems can directly communicate with the Prometheus server or create and view dashboards using a visualization/analytics tools like Grafana.
- The exporter can be configured to communicate with multiple ACOS devices in a multi-cloud environment. More details on configuration follows later.
- The exporter supports querying of any stats API as configured in Prometheus server yaml file. Gauge metrics are created for each stats field and are exposed on the port 9734 by the exporter.
More details on server yaml file follows later. 

## Setup/ installation steps
Create config.yaml as specified in section 1 above.

```
hosts:
  <host_ip goes here>:
    username: <uname goes here>
    password: <pwd goes here>
log:
  log_file: logs.log
  log_level: INFO
```
- host_ip: ACOS instance IP which is to be monitored
- log_level: set log level to debug for debugging purposes. Default log_level id set to INFO.
 
  
To use the Heml package, run following commands.

Add Helm Repo to local setup
```
helm repo add a10-prometheus-exporter https://a10networks.github.io/prometheus-exporter-helm/
```
Install the package to local 
```
helm install a10-prometheus-exporter/acos-prometheus-exporter --version 0.1.0
```
Check the Status using kubectl command
```
kubectl get all
``` 

