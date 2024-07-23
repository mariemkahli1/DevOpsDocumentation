## 1.What is monitoring in DevOps:

It's a practice of tracking and measuring the performance and health of a system and applications, in order to identify and correct issues early.

## 2.Why we need monitoring:

To get reports about what is happining in the environement we have built, by collecting informations about the infrastructure .

## 3.What you can check using a monitoring tool:

CPU usage, memory,storage, running services , deployed applications, application response time .

## 4.How to use monitoring:

Deploy monitoring tool on a server and a monitoring agent on each server we need to monitor so the monitoring server can pull data from those servers.

## 5.What is monitoring agent:

The monitoring agent collect information about the system every specific amount of time (1min,5min...) and share this information with the monitoring server.

## 6.How the monitoring system works:

We set rules in a configuration file where we specify for example: if the processor usage exceed 50% we need to get an alert .

## 7.What are the most used monitoring tools:

### **Prometheus**: 
it is an open source for system monitoring , alerting tool which collect and store logs and metrics.

### **Alert manager**
Handle alerts sent by applications such as prometheus and route them to the receuver integration such as e-mails,slack .

### **Grafana**

it is an open source for data-visualization , which allow users to see their data via charts and graphs for easier understanding .

### **Datadog**
it is a monitoring and analytics tool tha can be used to determine performance metrics as well as events monitoring for infrastructure and database ...

##  8.What is Helm 
Helm is a package manager for Kubernetes it allows you to describe , install and upgrades applications running on kubernetes .Helm uses packages called "charts" to define the necessary kubernetes ressources for deploying an application.

### **Install Helm**
Kubernetes must be installed and configure kubectl must be installed 

### **Using Helm**
#### charts :
A chart is a Helm package that contains all the resources definitions necessary to run an application on Kubernetes.
#### Repositories :
A repository is a place where charts are stored and shared .
#### Releases :
A release is an instance of a chart running in a Kubernetes cluster.

 ## 9.Setup Prometheus Monitoring and Grafana on Kubernetes using Helm

 ### Ensure that Minikube is running and the application is accessible.

Start Minikube

```sh
minikube start
```

Get the URL for the service:

```sh
minikube service flare-bank-service --url
```

### Install Helm

```sh
curl https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 | bash
```

### Add the Prometheus and Grafana Helm Repositories

```sh
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo add grafana https://grafana.github.io/helm-charts
helm repo update
```

### Create a namespace for monitoring:

```sh
kubectl create namespace monitoring
```

### Install Prometheus using Helm

Install Prometheus

```sh
helm install prometheus prometheus-community/prometheus --namespace monitoring
```

### Install Grafana using Helm

```sh
helm install grafana grafana/grafana --namespace monitoring
```

### Access Prometheus and Grafana

#### Access Prometheus

```sh
kubectl --namespace monitoring port-forward svc/prometheus-server 9090:80 &
```

you can type ctrl + c without problem.
Open your browser and navigate to `http://localhost:9090`.

#### Access Grafana

```sh
kubectl --namespace monitoring port-forward svc/grafana 3000:80 &
```

you can type ctrl + c without problem.
Open your browser and navigate to `http://localhost:3000`.

### Get Grafana Admin Password

The default username for Grafana is `admin`. You can get the admin password with the following command:

```sh
kubectl get secret --namespace monitoring grafana -o jsonpath="{.data.admin-password}" | base64 --decode ; echo
```

### Add Prometheus as a Data Source in Grafana

1. Login to Grafana (`http://localhost:3000`).
2. Go to Configuration > Data Sources.
3. Click on `Add data source`.
4. Select `Prometheus`.
5. Set the URL to `http://prometheus-server.monitoring.svc.cluster.local:80`.
6. Click `Save & Test`.
