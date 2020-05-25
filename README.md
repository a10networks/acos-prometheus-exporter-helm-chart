# acos-prometheus-exporter-helm-chart

This repository contains the Helm package for the A10 ACOS Prometheus Exporter.

## ACOS Prometheus Exporter
The ACOS Prometheus Exporter module collects the ACOS device statistics (stats) and displays the results as metrics.

To analyze the ACOS stats, configure any visualization client, such as, Grafana, to query the stats from the Prometheus server, plot them, set thresholds, configure alerts, create heat maps, generate table, and perform similar functions, as needed.

The Prometheus server works on a pull-based model and periodically queries the Exporter based on the intervals specified.  It runs by default on port 9090.

Users and systems can:
- Create and view dashboards by communicating with the Prometheus server using a Visualization and Analytics tool, like Grafana.
- Configure the Exporter to communicate with multiple ACOS devices in a multi-cloud environment. 
- Query any API stats configured in the Prometheus server’s YAML file. 

  The Exporter creates gauge metrics for each stats field and exposes them on port 9734.

More information on the configuration and the server YAML file will follow soon. 
 
## Setup and Installation
Create config.yaml as specified below.

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
- log_level: Set log_level to DEBUG for debugging purpose. Default log_level is INFO.
 
  
To use the Helm package, run the following commands.

- Add Helm Repo to the local setup:
  ```
  helm repo add a10-prometheus-exporter https://a10networks.github.io/prometheus-exporter-helm/
  ```
- Install the package on the local setup:
  ```
  helm install --name a10-prometheus-exporter a10-prometheus-exporter/acos-prometheus-exporter --set-file config=config.yaml
  ```
To check the status, use one of the following commands:

- For Kubernetes, use the  **kubectl** command:
```
kubectl get all
``` 
- For OpenShift, use the  **oc** command: 
```
oc get all
``` 
