#### Creacion del cluster Minikube (Kubernetes) (previa instalacion)
    minikube start --cpus 4 --memory 8192 --vm-driver hyperkit

#### Instalacion de Prometheus-operator
###### Añadir repositorios de Helm  (previa instalacion de Helm)
    helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
    helm repo add stable https://kubernetes-charts.storage.googleapis.com/
    helm repo update

###### Instalacion del Helm chart 
    helm install prometheus prometheus-community/kube-prometheus-stack

###### Link al chart de Prometheus
[https://github.com/prometheus-community/helm-charts/tree/main/charts/kube-prometheus-stack]


#### Port-forwarding de las ip internas del cluster
###### Prometheus-UI
    kubectl port-forward service/prometheus-kube-prometheus-prometheus 9090

###### Alert Manager UI
    kubectl port-forward svc/prometheus-kube-prometheus-alertmanager 9093

###### Grafana
    kubectl port-forward deployment/prometheus-grafana 3000

###### Grafana Dashboard credencinales de acceso
    user: admin
    pwd: prom-operator (obtenido del archivo values.yaml, por defecto)
