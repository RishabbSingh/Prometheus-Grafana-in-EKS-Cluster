# Setting up the monitoring tools in EKS Cluster
### :camera: Screenshots
 <div align="center"> 
  <img src="./assets/P & G.png" alt="screenshot" />
</div>

What is Prometheus?
-------------------

Prometheus is an open-source monitoring tool that provides out-of-the-box monitoring capabilities for the Kubernetes container orchestration platform. It can also monitor servers and databases. Prometheus collects and stores metrics as time-series data, recording information with a timestamp. It is based on a pull model, collecting metrics from targets by scraping metrics HTTP endpoints.

What is Grafana?
----------------

Grafana is an open-source visualization and analytics software that allows you to query, visualize, alert on, and explore your metrics no matter where they are stored.


### Key Components:

1.  **Prometheus Server:** Processes and stores metrics data.
2.  **Grafana:** Visualizes scraped data in a UI.

Installation Method
-------------------
 **Helm Chart (Recommended):** Using Helm to install Prometheus Operator including Grafana. This method ensures you don't miss any configuration steps and is very efficient.

### Why Use Helm?

Helm is a package manager for Kubernetes that simplifies the installation of all components with one command. It is recommended as it ensures you don't miss any configuration steps and is very efficient.

Prerequisites
-------------

-   An EKS Cluster up and running.
-   Helm 3 installed.
-   EC2 instance to access the EKS cluster.

### Step 1: Add Helm Repositories

First, add the necessary Helm repositories to your local client.

`helm repo add stable https://charts.helm.sh/stable
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm search repo prometheus-community`

### Step 2: Create Prometheus Namespace

Create a namespace for Prometheus in your Kubernetes cluster.

`kubectl create namespace prometheus`

### Step 3: Install kube-prometheus-stack

Use the following Helm command to install the `kube-prometheus-stack`. This stack includes both Prometheus and Grafana deployments.

`helm install stable prometheus-community/kube-prometheus-stack -n prometheus`

### Step 4: Verify Installation

Check if the Prometheus and Grafana pods are running.

`kubectl get pods -n prometheus
kubectl get svc -n prometheus`

### Step 5: Expose Prometheus and Grafana

To make Prometheus and Grafana available outside the cluster, use `LoadBalancer` or `NodePort` instead of `ClusterIP`.

#### Edit Prometheus Service

`kubectl edit svc stable-kube-prometheus-sta-prometheus -n prometheus`

#### Edit Grafana Service

`kubectl edit svc stable-grafana -n prometheus`

Verify if the service type is changed to `LoadBalancer` and get the Load Balancer URL.

`kubectl get svc -n prometheus`

### Step 6: Access Grafana UI

Get the URL from the above command and open it in your browser.

#### Default Credentials:

-   **UserName:** admin
-   **Password:** prom-operator

### Step 7: Create Dashboard in Grafana

In Grafana, you can create various kinds of dashboards as per your needs to visualize the metrics collected by Prometheus.

### Conclusion

By following these steps, you have successfully set up monitoring on your Kubernetes cluster using Prometheus and Grafana on EKS. This setup will provide you with real-time insights and alerting capabilities to ensure your applications and infrastructure are running smoothly.
