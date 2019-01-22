# kubernetes-prometheus-deploy

#### Raw URI to request from the server
```
kubectl get --raw "/metrics"  # Apiserver metrics
```
```
kubectl get --raw "/api/v1/nodes/master01/proxy/metrics/cadvisor"  # cadvisor metrics
```