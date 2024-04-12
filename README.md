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
# Changes in the values.yaml (chart v3.0.0)
#https://github.com/grafana/loki/blob/main/production/helm/loki/values.yaml


# Changes in the simple-scaleble-values.yaml (chart v3.0.0)
#https://github.com/grafana/loki/blob/main/production/helm/loki/simple-scalable-values.yaml


Full setup : [Install Simple Scalable Loki Promtail Grafana stack in KIND cluster](https://naren4b.github.io/nks/docs/setup-loki-grafana-stack-simple-scalable.html)

