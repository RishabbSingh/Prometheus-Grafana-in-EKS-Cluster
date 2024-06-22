# Setting up the monitoring tools in EKS Cluster

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

