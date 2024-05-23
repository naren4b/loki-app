# Install extra container 

Build and Load the image (ref: https://github.com/naren4b/monitoring-stack/tree/main/loki )

```bash
docker build -t loki-curator:1.1 .
kind create cluster
kind load docker-image loki-curator:1.1

```

Loki custom helm value file

```bash

cat<<EOF >$PWD/loki-demo-values.yaml
loki:
  commonConfig:
    replication_factor: 1
  storage:
    type: "filesystem"
  auth_enabled: false
singleBinary:
  persistence:
    size: 1Gi
    #storageClass: standard
  replicas: 1
  extraContainers:
    - name: curator
      image: "loki-curator:1.1" # https://github.com/grafana/loki/issues/2314#issuecomment-1028637269
      imagePullPolicy: IfNotPresent
      env:
        - name: SPACEMONITORING_FOLDER
          value: "/data/loki/chunks"
        - name: SPACEMONITORING_DELETINGITERATION
          value: "5"
        - name: SPACEMONITORING_MAXUSEDPERCENTE
          value: "80"
        - name: CLEANUP_INTERVAL
          value: "60"
      resources:
        limits:
          memory: 1Gi
        requests:
          memory: 10Mi
      terminationMessagePath: /dev/termination-log
      terminationMessagePolicy: File
      volumeMounts:
        - name: storage
          mountPath: "/data"
          subPath:

test:
  enabled: false
gateway:
  enabled: false
monitoring:
  lokiCanary:
    enabled: false
  selfMonitoring:
    enabled: false
    grafanaAgent:
      installOperator: false

EOF
```
