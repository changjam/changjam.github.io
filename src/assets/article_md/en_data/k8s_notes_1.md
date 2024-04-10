# Kubernetes Notes
> *Kubernetes, also known as k8s, is named for the eight characters between "k" and "s."*

## Introduction
Kubernetes is an automated deployment tool for managing multiple containers, with the following main functions:
* Deploying multiple containers to multiple machines simultaneously (Deployment)
* Automatically scaling containers when the load on services changes (Scaling)
* Managing the state of multiple containers, automatically detecting and restarting failed containers (Management)

## Architecture
### K8S
* The following are the four components of Kubernetes, described from smallest to largest.
* ### Pod
    * The smallest unit in Kubernetes
    * A pod usually corresponds to one container, but it can also have multiple containers
    * Each pod corresponds to a YAML file
* ### Worker Node
    * Corresponds to a server (hardware device)
    * Each node contains three components
        * ### kubelet
            * Manages pods and is responsible for communication with the master node
        * ### kube-proxy
            * By updating iptables, it ensures that traffic is correctly forwarded to the components on the Pod
            * iptables is a firewall on Linux, not only limiting which connections can come in, but also managing network connections, deciding which Pod to hand incoming requests to
        * ### Container Runtime
            * The component responsible for actually running the containers
* ### Master Node
    * A node dedicated to managing other worker nodes
    * Each master node contains four components
    * ### kube-apiserver
        * Communication between nodes
        * Authentication and authorization
    * ### etcd
        * Backup data
    * ### kube-controller-manager
        * Manages controllers
        * Controllers are processes responsible for monitoring the Cluster's status
    * ### kube-scheduler
        * Determines which node is suitable for allocating the current open pods
* ### Cluster
    * A collection of "the first three components" in Kubernetes

## Operation Process
### Creating a New Pod
#### 1. The command to create a Pod is sent to kube-apiserver
    1-1. User identity and permissions are verified
    1-2. The command is backed up to etcd
    1-3. kube-controller-manager, kube-scheduler, kubelet are notified
#### 2. kube-controller-manager receives a message from kube-apiserver indicating the need to create a Pod
    2-1. kube-controller-manager checks permissions and creates the Pod
#### 3. kube-scheduler periodically queries kube-controller-manager for new Pods
    3-1. If there are any, the Pod is assigned to the corresponding Worker Node.
#### 4. kubelet receives instructions from the master node and creates a Pod.
    4-1. kube-proxy updates iptables, indicating that the Pod is currently available.
### User Sends Request

#### 1. When users send requests, they first go to the Load Balancer to determine which Node to send the request to
#### 2. Upon reaching the node, iptables determine which Pod to send the request to
#### 3. If the receiving Node does not have a Pod that can handle the request, it will use iptables to forward the request to another Node that can handle the request.

## Advanced Components
* ### Service
    * Allows setting rules for a group of pods for easy management
    * Uses port forwarding to connect internally and externally
    * Node <--> Service <--> Pod
* ### Ingress
    * When services increase, having many internal and external ports can lead to poor management. Using Ingress can unify the port numbers of services and use paths for redirection
    * Node <--> Ingress <--> Service <--> Pod
* ### Deployments
    * Can replicate and delete the same pod. The purpose is to replace the pod with a new one in case of pod failure or when updating versions, ensuring uninterrupted service of the API
    * Can be used for load balancing
