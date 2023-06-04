# my-monitoring-stack
Prometheus + Loki + Grafana + Kubernetes-event-exporter in minikube

# Prometheus
refer: https://github.com/prometheus-community/helm-charts/tree/main/charts/kube-prometheus-stack
## Add helm repository

```shell
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update prometheus-community
```

## Install
```shell
helm install prometheus prometheus-community/kube-prometheus-stack --namespace monitoring --create-namespace -f ./values/prometheus/values.yaml

```

# Grafana
refer: https://github.com/grafana/helm-charts/tree/main/charts/grafana

## Add helm repository

```shell
helm repo add grafana https://grafana.github.io/helm-charts
```

## Install
```shell
helm install --namespace monitoring --create-namespace grafana grafana/grafana
```

# Loki
refer : 
- https://github.com/grafana/helm-charts/tree/main/charts

## Install
```shell
helm upgrade --install loki grafana/loki-stack
```

# Kubernetes-event-exporter
refer:
- https://github.com/resmoio/kubernetes-event-exporter
- https://pseonghoon.github.io/post/kubernetes-event-exporter/

## git clone
git clone https://github.com/resmoio/kubernetes-event-exporter.git

## Install
```shell
kubectl apply -f ./kubernetes-event-exporter-sample/00-role.yaml
kubectl apply -f ./kubernetes-event-exporter-sample/01-config.yaml
kubectl apply -f ./kubernetes-event-exporter-sample/02-deployment.yaml
```

