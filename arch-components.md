# Kubernetes Basic Architecture

## Overview
Kubernetes (K8s) is a container orchestration platform used to deploy, scale, and manage containerized applications across a cluster of machines.

A Kubernetes cluster consists of:
- Control Plane (Master components)
- Worker Nodes (Application runtime)

---

## High-Level Architecture Diagram

```
                     +----------------------+
                     |     Control Plane    |
                     |----------------------|
kubectl / CI/CD ---> |  kube-apiserver      |
                     |  kube-scheduler      |
                     |  controller-manager  |
                     |  etcd                |
                     +----------+-----------+
                                |
              +-----------------+------------------+
              |                 |                  |
        +-----v------+     +----v-------+     +----v-------+
        | Worker 1   |     | Worker 2    |     | Worker 3    |
        |------------|     |-------------|     |-------------|
        | kubelet    |     | kubelet     |     | kubelet     |
        | kube-proxy |     | kube-proxy  |     | kube-proxy  |
        | runtime    |     | runtime     |     | runtime     |
        | Pods       |     | Pods        |     | Pods        |
        +------------+     +-------------+     +-------------+
```

---

## Control Plane Components

### 1. kube-apiserver
- Entry point to the Kubernetes cluster
- Handles all REST requests
- Authenticates and validates requests

### 2. kube-scheduler
- Assigns Pods to worker nodes
- Considers CPU, memory, affinity, taints, and tolerations

### 3. kube-controller-manager
- Ensures desired state matches actual state
- Runs controllers like:
  - Node Controller
  - ReplicaSet Controller
  - Deployment Controller

### 4. etcd
- Distributed key-value store
- Stores complete cluster state
- Critical component (requires regular backups)

---

## Worker Node Components

### 1. kubelet
- Agent running on each worker node
- Communicates with API Server
- Ensures containers defined in Pods are running

### 2. Container Runtime
- Responsible for running containers
- Common runtimes:
  - containerd
  - CRI-O

### 3. kube-proxy
- Manages networking rules
- Enables Service-to-Pod and Pod-to-Pod communication
- Uses iptables or IPVS

### 4. Pods
- Smallest deployable unit in Kubernetes
- Can contain one or more containers
- Containers share:
  - Network namespace
  - Storage volumes

---

## Application Deployment Flow

1. User runs `kubectl apply -f app.yaml`
2. Request reaches kube-apiserver
3. State is stored in etcd
4. Scheduler selects a worker node
5. kubelet pulls container image
6. Container runtime starts container
7. kube-proxy configures networking
8. Application becomes accessible

---

## Why Kubernetes Architecture Matters

### Operations (DevOps)
- High availability and scalability
- Self-healing workloads
- Efficient resource utilization

### Security (Cybersecurity)
- API Server authentication and RBAC
- etcd encryption at rest
- Network Policies for traffic isolation
- Secure kubelet configuration

---

## Summary
- Control Plane manages the cluster
- Worker Nodes run applications
- Kubernetes ensures declarative, self-healing infrastructure
- Strong foundation for DevOps and Cybersecurity roles
