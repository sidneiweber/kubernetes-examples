https://github.com/eksctl-io/eksctl/tree/main/examples

# Elastic Search
helm repo add elastic https://helm.elastic.co 
helm install elasticsearch --values elastic-values.yaml elastic/elasticsearch

# Prometheus, Grafana
helm install prometheus prometheus-community/kube-prometheus-stack -n monitoring
