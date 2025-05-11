Use Official Helm Charts (RECOMMENDED)
These charts are already tested, maintained, and flexible for production use.

1. Add Repos
bash
Copy
Edit
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo add grafana https://grafana.github.io/helm-charts
helm repo update
2. Install Prometheus
bash
Copy
Edit
helm install prometheus prometheus-community/prometheus \
  --namespace monitoring --create-namespace
3. Install Loki
bash
Copy
Edit
helm install loki grafana/loki \
  --namespace monitoring
4. Install Promtail
bash
Copy
Edit
helm install promtail grafana/promtail \
  --namespace monitoring
5. Install Grafana
bash
Copy
Edit
helm install grafana grafana/grafana \
  --namespace monitoring \
  --set adminPassword='admin' \
  --set service.type=NodePort
You can expose Grafana using Ingress too if you’ve already configured ingress.

