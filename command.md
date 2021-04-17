#### List Pods using Kubectl
#### Info: Add -o wide option to the kubectl get command to get more details.

#### List Pods in the default Namespace for the current context:

$ kubectl get pods
$ kubectl get pods -o wide

#### List all Pods from the all Namespaces:

$ kubectl get pods --all-namespaces 
$ kubectl get pods --all-namespaces -o wide
#### Get Pods from the particular Namespace:

$ kubectl get pods --namespace <namespace_name>
$ kubectl get pods --namespace <namespace_name> -o wide
#### Get detailed information about a Pod:

$ kubectl describe pode <pode_name>


#### create Minikube cluster
    minikube start --cpus 4 --memory 8192 --vm-driver hyperkit

#### install Prometheus-operator
    helm install prometheus stable/prometheus-operator

###### add repos  
    helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
    helm repo add stable https://charts.helm.sh/stable
    helm repo update

###### install chart
    helm install prometheus prometheus-community/kube-prometheus-stack

    ###### Note

   By default this chart installs additional, dependent charts:

    kubernetes/kube-state-metrics
    prometheus-community/prometheus-node-exporter
    grafana/grafana 

###### install chart with fixed version    
    helm install prometheus prometheus-community/kube-prometheus-stack --version "9.4.1"

###### Link to chart
[https://github.com/prometheus-community/helm-charts/tree/main/charts/kube-prometheus-stack]


#### install Mongodb-exprter
###### add repos
    helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
    helm repo update

###### install chart
    helm install mongodb-exporter prometheus-community/prometheus-mongodb-exporter

###### install chart with fixed version    
    helm install mongodb-exporter prometheus-community/prometheus-mongodb-exporter --version "2.8.1"

###### Link to chart
[https://github.com/prometheus-community/helm-charts/tree/main/charts/prometheus-mongodb-exporter]


#### port-forwardings
###### Prometheus-UI
    kubectl port-forward service/prometheus-kube-prometheus-prometheus 9090

###### Alert Manager UI
    kubectl port-forward svc/prometheus-kube-prometheus-alertmanager 9093

###### Grafana
    kubectl port-forward deployment/prometheus-grafana 3000

###### Grafana Dashboard credentials
    user: admin
    pwd: prom-operator (from values.yaml file set as default)

###### Mongodb-exporter 
    kubectl port-forward service/mongodb-exporter-prometheus-mongodb-exporter 9216  

