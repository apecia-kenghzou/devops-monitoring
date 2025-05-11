# 📊 Monitoring & Logging Stack with Helm

This Helm chart deploys a full monitoring and logging stack on Kubernetes including:

- **Prometheus** – Metrics collection
- **Grafana** – Visualization
- **Loki** – Log aggregation backend
- **Promtail** – Log collection agent
- **Optional: Prometheus Operator** for easier app monitoring integration

---

## 🚀 Features

- Collects application logs and metrics
- Provides dashboards via Grafana
- Supports ServiceMonitor and PodMonitor if Prometheus Operator is used
- Easy to integrate with other Helm charts

---

## 🧱 Directory Structure

monitoring/
├── Chart.yaml
├── values.yaml
├── templates/
│ ├── grafana-deployment.yaml
│ ├── grafana-service.yaml
│ ├── loki-deployment.yaml
│ ├── loki-service.yaml
│ ├── prometheus-deployment.yaml
│ ├── prometheus-service.yaml
│ ├── promtail-deployment.yaml
│ └── promtail-service.yaml

---

## 🛠️ Prerequisites

- Kubernetes cluster (local or cloud)
- [kubectl](https://kubernetes.io/docs/tasks/tools/)
- [Helm](https://helm.sh/docs/intro/install/)

---

## 🔧 Installation

### 1. Clone the repository

```bash
git clone https://github.com/your-org/monitoring-stack.git
cd monitoring-stack

### Deploy Helm Chart
```bash
helm install monitoring ./monitoring --namespace monitoring --create-namespace
```

### Expose Service Via Ingress

```bash
kubectl port-forward --namespace ingress-nginx service/ingress-nginx-controller 8080:80
```
Please take note on the host file if doesnt have please do add 
via ip is not accessible

