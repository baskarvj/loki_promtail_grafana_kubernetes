![loki_cover_image (1)](https://github.com/baskarvj/loki_promtail_grafana_kubernetes/assets/103120325/514d64c8-b423-48cc-bbab-7904a379c3e7)

### Helm Installation ######
~~~
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh
~~~
~~~
helm version
~~~

### Grafana , loki & promtail installation ####
~~~
helm repo add grafana https://grafana.github.io/helm-charts
helm repo update
~~~
~~~
helm search repo Grafana
~~~

### value reference file for loki-stack

https://github.com/grafana/helm-charts/blob/main/charts/loki-stack/values.yaml

~~~
vi loki.yml
~~~
~~~
loki:
  enabled: true

promtail:
  enabled: true

grafana:
  enabled: true
  service:
    type: NodePort
~~~

~~~
helm install loki grafana/loki-stack --values loki.yml
~~~
### elable all TCP in security Group
security group -- all tcp 

### To get admin password
~~~
kubectl get secret --namespace default loki-grafana -o jsonpath="{.data.admin-password}" | base64 --decode ; echo
~~~
### Dashboard creation #######
id for dashboard
~~~
15141
~~~   
