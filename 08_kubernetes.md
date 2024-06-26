# Kuberenetes

## 1. **Installation**:

- Installation kubectl - minikube
- Configuration kubectl
- Installation kubernetes dashboard (Lens)

## 2. **Node**:

- Node - master
- A node is a virtual or physical machine in the Kubernetes cluster. Nodes contain the services needed to run pods.

**Commands**

This command lists all the nodes in the Kubernetes cluster.

             kubectl get nodes

**Output**

      NAME          STATUS   ROLES    AGE    VERSION
      node-1        Ready    <none>   3d     v1.18.2
      node-2        Ready    <none>   3d     v1.18.2

## 3. **Pod**:

- Pod - smallest unit of deployment in kubernetes
- A pod is the smallest deployable and manageable unit in Kubernetes. It can contain one or more containers.

  ![Texte alternatif](/media/pod.png)

**Commands**

This command lists all the pods in the Kubernetes cluster.

            kubectl get pods

Pods can be created using YAML configuration files, providing more control and flexibility

![Texte alternatif](/media/podyaml.png)

**Managing Pods**

![Texte alternatif](/media/podconf.png)

## 4. **Deployment**:

- A deployment manages a set of identical pods, ensuring that a certain number of them are always running.

![Texte alternatif](/media/dep.png)

**Command**:

This command lists all the deployments in the cluster or in a specific namespace if specified.

          kubectl get deployment

Deployments are often defined and configured via YAML files

![Texte alternatif](/media/depyaml.png)

**Managing Deployments**

![Texte alternatif](/media/depcon.png)

## 5. **Service**:

- A service is a Kubernetes abstraction that defines a logical set of pods and a policy by which to access them (usually through a stable IP address and DNS name).

![Texte alternatif](/media/ser.png)

**command**:

This command lists all the services in the cluster or in a specific namespace if specified.

            kubectl get services

Services can be configured in more detail via YAML files, especially to
define different types of Services such as ClusterIP, NodePort, or LoadBalancer.

![Texte alternatif](/media/seryaml.png)

**Managing Services**
![Texte alternatif](/media/serconf.png)
