## Fresh Installation
Steps to follow install prometheus operator

- Add helm repo
```sh
    helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
    helm repo update 
```

- Create monitoring namespace
```sh
    kubectl create namespace monitoring
```

- Install prometheus monitoring
```sh
    helm upgrade --install --wait --atomic --timeout 500s prommonitor prometheus-community/prometheus-operator -n monitoring -f /monitoring/config/values.yaml --set prometheusOperator.createCustomResource=false
```

## Notes

- Write ServiceMonitor to monitor the metrics
- Write PrometheusRule to configure the alert manager

