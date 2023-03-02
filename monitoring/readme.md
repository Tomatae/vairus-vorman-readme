# Monitoring

There are three posibilities to monitor your infrastructure

 - VK Cloud. Just open cluster info to get perfomance data.

 - Prometheus + Grafana. Run from your local pc `kubectl -n prometheus-monitoring port-forward service/kube-prometheus-stack-grafana 8001:80`. You will be able to monitor and configure literally anything by configuring metrics and building multiple charts.

 - K8S Dashboard
