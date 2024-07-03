# KubernetesExplain
Kubernetes (K8s) is an open-source container orchestration platform developed by Google. It automates the deployment, scaling, and management of containerized applications. It provides a platform for automating the deployment, scaling, and operations of application containers across clusters of hosts, providing container-centric infrastructure.

# Key Concepts
## Containerization: 

Kubernetes manages containerized applications, primarily using Docker.

## Cluster: 

A Kubernetes cluster consists of a set of worker machines (nodes) and a control plane (master node).

## Nodes: 

Each node is a VM or physical machine that serves as a worker in the Kubernetes cluster. Nodes run containerized applications.

## Pod:

The smallest and simplest Kubernetes object. A pod represents a single instance of an application, consisting of one or more containers that share network and storage resources.

## Controller:

Kubernetes controllers manage application lifecycle operations, such as deployments, replica sets, stateful sets, daemon sets, etc.

## Service:

An abstraction that defines a set of pods and how to access them. It provides a stable endpoint (IP address and port) to access pods, even if the pods themselves are replaced or rescheduled.

## Namespace:

Kubernetes supports multiple virtual clusters backed by the same physical cluster. Namespaces provide scope for names, and they are a way to divide cluster resources between multiple users (via resource quota) or projects.

# Kubernetes Architecture

## Master Node:

Controls the Kubernetes cluster and manages its overall state. It includes several components:

## API Server:

Exposes Kubernetes API and is the front-end for the Kubernetes control plane.

## Scheduler:

Assigns pods to nodes based on resource availability and constraints.

## Controller Manager:
Manages various controllers responsible for different aspects of the cluster (nodes, endpoints, etc.).

## etcd: 
Consistent and highly-available key-value store used to store all cluster data.

## Worker Nodes:

Each worker node runs Kubernetes components necessary to maintain pod lifecycle:

## Kubelet:

Agent that runs on each node and ensures pods are running and healthy.

## Container Runtime:

Software responsible for running containers, such as Docker or containerd.

## Kube-proxy: 

Manages network connectivity to Kubernetes Services.

## Namespaces:

### Purpose: 
Used to partition cluster resources among multiple users or projects.
Commands:
List namespaces: 
```

kubectl get namespaces

```
Switch namespace context:

```
kubectl config set-context --current --namespace=<namespace>

```
## Pods:


### Purpose:

The smallest deployable units of computing that can be created and managed in Kubernetes.
Commands:
Create a pod: 

```

kubectl apply -f pod-definition.yaml

```
Get pods: 

```

kubectl get pods

```

Describe a pod: 

```

kubectl describe pod <pod-name>

```
Delete a pod: 

```

kubectl delete pod <pod-name>

```

## Deployments:

### Purpose: 

Provides declarative updates to applications, managing the deployment and scaling of replica sets.
Commands:
Create a deployment: 

```

kubectl create deployment <deployment-name> --image=<image-name>

```

Scale a deployment: 

```

kubectl scale deployment <deployment-name> --replicas=<number>

```

Update a deployment: 

```

kubectl set image deployment/<deployment-name> <container-name>=<new-image>

```

Rollback a deployment:

```

kubectl rollout undo deployment/<deployment-name>

```

## ReplicaSets:

### Purpose:

Ensures a specified number of pod replicas are running at any given time.

Commands:
Get replica sets:

```
kubectl get rs

```

Scale a replica set: 

```

kubectl scale rs <replica-set-name> --replicas=<number>

```
Services:

Purpose: Provides networking and load balancing to pods, allowing access to a set of pods.
Commands:
Create a service: kubectl expose deployment <deployment-name> --port=<port> --target-port=<target-port> --type=<type>
Get services: kubectl get services
Volumes:

Purpose: Provides persistent storage for pod containers.
Commands:
Create a persistent volume: kubectl apply -f persistent-volume.yaml
Create a persistent volume claim: kubectl apply -f persistent-volume-claim.yaml
List persistent volumes: kubectl get pv
List persistent volume claims: kubectl get pvc
ConfigMaps and Secrets:

Purpose: Store configuration data and sensitive information securely.
Commands:
Create a config map: kubectl create configmap <configmap-name> --from-file=<path-to-file>
Create a secret: kubectl create secret generic <secret-name> --from-literal=<key>=<value>
DaemonSets:

Purpose: Ensures all (or some) nodes run a copy of a pod, typically for system daemons.
Commands:
Create a daemon set: kubectl apply -f daemonset-definition.yaml
StatefulSets:

Purpose: Manages the deployment and scaling of a set of pods with unique identities and persistent storage.
Commands:
Create a stateful set: kubectl apply -f statefulset-definition.yaml
Jobs and CronJobs:

Purpose: Executes a task to completion (Job) or at a scheduled time (CronJob).
Commands:
Create a job: kubectl apply -f job-definition.yaml
Create a cron job: kubectl apply -f cronjob-definition.yaml
Advanced Kubernetes Commands
kubectl explain: Detailed information about Kubernetes resources.
Example: kubectl explain pod.spec.containers
kubectl logs: Fetch the logs of a container.
Example: kubectl logs <pod-name>
kubectl exec: Execute commands inside a container.
Example: kubectl exec -it <pod-name> -- /bin/bash
kubectl top: View resource usage (CPU, memory) of nodes or pods.
Example: kubectl top pods
Kubernetes Networking and Services
Network Policies: Define how groups of pods are allowed to communicate with each other and other network endpoints.
Ingress Controllers: Exposes HTTP and HTTPS routes from outside the cluster to services within the cluster.
Advanced Topics
Horizontal Pod Autoscaler (HPA): Automatically scales the number of pods based on observed CPU utilization.
Pod Affinity and Anti-Affinity: Control the scheduling of pods based on the presence of other pods.
Custom Resource Definitions (CRDs): Extend Kubernetes API to manage custom resources (e.g., operators).
Service Mesh (e.g., Istio): Enhances network observability, security, and traffic management for microservices.
