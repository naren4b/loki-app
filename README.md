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
![image](https://github.com/naren4b/loki-app/assets/3488520/088904e7-26ee-45db-b8a1-49f0515f8afd)


# Changes in the simple-scaleble-values.yaml (chart v3.0.0)
#https://github.com/grafana/loki/blob/main/production/helm/loki/simple-scalable-values.yaml
![image](https://github.com/naren4b/loki-app/assets/3488520/8b13bd5f-20f6-4681-9604-f0a0634572ae)


Full setup : [Install Simple Scalable Loki Promtail Grafana stack in KIND cluster](https://naren4b.github.io/nks/docs/setup-loki-grafana-stack-simple-scalable.html)

