# Kuberenetes

## 1. **What is Kuberenetes**
Kubernetes (K8s) is an open-source container orchestration platform designed to automate the deployment, scaling, and management of containerized applications. It plays a crucial role in DevOps by enabling continuous integration and continuous deployment (CI/CD) pipelines, efficient resource management, and streamlined application delivery.

## 2.**Key Concepts**

**Containers**

Lightweight, standalone, and executable software packages that include everything needed to run a piece of software, including the code, runtime, libraries, and system tools.

**Clusters** 

A set of nodes managed by Kubernetes. A cluster is controlled by a master node, which coordinates all cluster activities.

**Namespaces**

Virtual clusters within a Kubernetes cluster that provide a scope for resources.

**Node**

- Node - master
- A node is a virtual or physical machine in the Kubernetes cluster. Nodes contain the services needed to run pods.

#### **Commands**

This command lists all the nodes in the Kubernetes cluster.

 kubectl get nodes

#### **Output**

      NAME          STATUS   ROLES    AGE    VERSION
      node-1        Ready    <none>   3d     v1.18.2
      node-2        Ready    <none>   3d     v1.18.2

**Pod**:

- Pod - smallest unit of deployment in kubernetes
- A pod is the smallest deployable and manageable unit in Kubernetes. It can contain one or more containers.

  ![Texte alternatif](/media/pod.png)

#### **Commands**

This command lists all the pods in the Kubernetes cluster.

     kubectl get pods

Pods can be created using YAML configuration files, providing more control and flexibility




**Deployment**:

- A deployment manages a set of identical pods, ensuring that a certain number of them are always running.

![Texte alternatif](/media/dep.png)

#### **Command**:

This command lists all the deployments in the cluster or in a specific namespace if specified.

          kubectl get deployment

Deployments are often defined and configured via YAML files


 **Service**:

- A service is a Kubernetes abstraction that defines a logical set of pods and a policy by which to access them (usually through a stable IP address and DNS name).

![Texte alternatif](/media/ser.png)

#### **command**:

This command lists all the services in the cluster or in a specific namespace if specified.

            kubectl get services

Services can be configured in more detail via YAML files, especially to
define different types of Services such as ClusterIP, NodePort, or LoadBalancer.


## 3.**Monitoring and Logging**

   **Prometheus** 
    
   An open-source monitoring and alerting toolkit used to collect metrics from Kubernetes components and applications.

   **Grafana** 
    
  A tool for visualizing metrics collected by Prometheus.

  **ELK Stack (Elasticsearch, Logstash, Kibana)** 
    
 Used for centralized logging, enabling the collection, processing, and visualization of logs.

## 4.**Run a local Docker image in Minikube**

####  1.Install Minikube

#### 2.Install Kubectl

#### 3.Set up Minikube (image from dockerhub)

#### 3.1. Start Minikube

```sh
minikube start
```

#### 3.2. Set Docker Environment

Configure your shell to use the Docker daemon inside Minikube:

```sh
eval $(minikube docker-env)
```

#### 3.3. Pull the image from the repository

```sh
docker pull mariem820/flare-bank:latest
```

#### 3.4. Verify the Image

Ensure the image is available in Minikube's Docker environment.

```sh
docker images
```

#### 3.5. Create a Kubernetes Deployment

Create a YAML file (`deployment.yaml`) in the racine for the deployment:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: flare-bank-deployment
spec:
  replicas: 1
  selector:
    matchLabels:
      app: flare-bank
  template:
    metadata:
      labels:
        app: flare-bank
    spec:
      containers:
        - name: flare-bank
          image: mariem820/flare-bank:latest
          ports:
            - containerPort: 80

- Apply the Deployment:

```sh
kubectl apply -f deployment.yaml
```

#### 3.6. Expose the Deployment

Create a service to expose the deployment. You can do this by creating a YAML file (`service.yaml`) in the racine for the service:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: flare-bank-service
spec:
  type: NodePort
  selector:
    app: flare-bank
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
```

- Apply the service:

```sh
kubectl apply -f service.yaml
```

#### 3.7. Access the Application

Get the URL for the service:

```sh
minikube service flare-bank-service --url
```

- This URL will allow you to access your application running inside Minikube.

#### 3.8. Stop and delete the container running in Kubernetes

- Delete the associated Kubernetes resources (the deployment and service)

1. Stop and Delete the Deployment:

   ```sh
   kubectl delete deployment flare-bank-deployment
   ```

2. Delete the Service:
   ```sh
   kubectl delete service flare-bank-service
   ```

Stop and delete the Minikube cluster

1. Stop Minikube:

   ```sh
   minikube stop
   ```

2. Delete Minikube Cluster:
   ```sh
   minikube delete
   ```



## 5. Set up Minikube (image built from Dockerfile)

#### 1. Start Minikube

```sh
minikube start
```

#### 2. Set Docker Environment

Configure your shell to use the Docker daemon inside Minikube:

```sh
eval $(minikube docker-env)
```

#### 3. Build the Docker Image in the Minikube repo

If you haven't already built the Docker image, you can build it inside Minikube's Docker daemon. If the image is already built on your local system, you can retag it.

```sh
docker build -t flare-bank:latest .
```

#### 4. Verify the Image

Ensure the image is available in Minikube's Docker environment.

```sh
docker images
```

#### 5. Create a Kubernetes Deployment

Create a YAML file (`deployment.yaml`) in the racine for the deployment:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: flare-bank-deployment
spec:
  replicas: 1
  selector:
    matchLabels:
      app: flare-bank
  template:
    metadata:
      labels:
        app: flare-bank
    spec:
      containers:
        - name: flare-bank
          image: flare-bank:testing
          ports:
            - containerPort: 80
```

- Apply the Deployment:

```sh
kubectl apply -f deployment.yaml
```

#### 6. Expose the Deployment

Create a service to expose the deployment. You can do this by creating a YAML file (`service.yaml`) in the racine for the service:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: flare-bank-service
spec:
  type: NodePort
  selector:
    app: flare-bank
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
```

- Apply the service:

```sh
kubectl apply -f service.yaml
```

#### 7. Access the Application

Get the URL for the service:

```sh
minikube service flare-bank-service --url
```

- This URL will allow you to access your application running inside Minikube.
