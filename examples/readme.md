## 🧩 Integrating with Other Applications
### Option 1: Manual Prometheus scrape annotations
In your app's Deployment:

``` yaml
metadata:
  annotations:
    prometheus.io/scrape: "true"
    prometheus.io/port: "8080"
```
##⚠️ Requires Prometheus to be configured to scrape all pods with prometheus.io/scrape=true

### Option 2: Using Prometheus Operator + ServiceMonitor
Install Prometheus Operator via Helm:

```bash

helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
helm install kube-prometheus-stack prometheus-community/kube-prometheus-stack \
  --namespace monitoring --create-namespace
```
Add this to your app’s Helm chart:

```yaml
apiVersion: monitoring.coreos.com/v1
kind: ServiceMonitor
metadata:
  name: my-app-monitor
  labels:
    release: kube-prometheus-stack
spec:
  selector:
    matchLabels:
      app: my-app
  endpoints:
    - port: http
      path: /metrics
      interval: 15s
```