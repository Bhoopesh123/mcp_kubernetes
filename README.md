helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
kubectl create ns metrics
kubectl config set-context --current --namespace=metrics

helm upgrade --install grafana prometheus-community/kube-prometheus-stack

helm repo add grafana-community https://grafana-community.github.io/helm-charts
helm repo update
helm upgrade --install my-release grafana-community/grafana-mcp -n metrics -f values.yaml
