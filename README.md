# loki-app
Learning the installation of loki

```bash
git clone https://github.com/naren4b/loki-app.git
cd loki-app
helm repo add grafana https://grafana.github.io/helm-charts
helm repo update
helm pull grafana/loki --untar # optional
helm upgrade --install  loki grafana/loki  -f simple-scalable-values.yaml -f my-values.yaml 
```
