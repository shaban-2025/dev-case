1) install

helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update

helm install monitoring prometheus-community/kube-prometheus-stack \
  --set prometheus.service.type=NodePort \
  --set prometheus.service.nodePort=30090 \
  --set grafana.service.type=NodePort \
  --set grafana.service.nodePort=30091 \
  --set grafana.adminPassword=admin123


2) get grafana admin user password

kubectl --namespace saban get secrets monitoring-grafana -o jsonpath="{.data.admin-password}" | base64 -d ; echo


