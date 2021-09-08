## Fresh Installation
Steps to follow install istio using istioctl 

- Download Istio
```sh
    curl -L https://istio.io/downloadIstio | ISTIO_VERSION=1.11.2 (or)
    curl -L https://istio.io/downloadIstio | sh -
```
- Export istioctl path
```sh
    cd istio-1.11.2
    export PATH=$PWD/bin:$PATH
```
- Install istio using istioctl
```sh
    istioctl install -f /Users/murali/Documents/workspace/personal/istio-doc/config/istio-config.yaml
```
- Rollout deployment in all namespace
```sh
    kubectl rollout restart deployment -n {namespace}
```

## Upgrade Istio
Steps to follow CANARY upgrade istio using istioctl

- Download Istio
```sh
    curl -L https://istio.io/downloadIstio | ISTIO_VERSION=1.6.8 (or)
    curl -L https://istio.io/downloadIstio | sh -
```
- Export istioctl path
```sh
    cd istio-{ISTIO_VERSION}
    export PATH=$PWD/bin:$PATH
```
- Install istio using istioctl
```sh
    istio_revision = ISTIO_VERSION.replace(".", "-")
    istioctl install --set revision={istio_revision} -f {IstioOperator config file}
```
- Rollout Canary deployment in all namespace
```sh
    istio_revision = ISTIO_VERSION.replace(".", "-")
    kubectl label namespace {namespace} istio-injection- istio.io/rev={istio_revision}  
    kubectl rollout restart deployment -n {namespace}
```