# Introduction to Kubernetes (K8s)

Before Kubernetes, Docker and Docker Swarm transformed how developers package applications. It allowed them to bundle an application and its dependencies into a single, portable unit called a **container**. This worked fine for small-scale deployments, but when applications grew to hundreds or thousands of containers, the following problems appeared:

- Scalability Issues  
- Multi-Cloud Deployments  
- Security & Resource Management  
- Rolling Updates & Zero Downtime Deployments  

This is the problem Kubernetes was created to solve. It acts as the **"brain"** or orchestrator for your containers, handling the complex task of managing them at scale automatically.

---

## What is Kubernetes?

Kubernetes, often shortened to **K8s** (K, 8 letters, s), is an open-source platform that automates the deployment, scaling, and management of containerized applications.

- **Origin:** Developed by Google, inspired by internal systems Borg and Omega  
- **Launch:** Officially released in 2014  
- **CNCF Donation:** Donated to the Cloud Native Computing Foundation (CNCF) in 2015, which now maintains it  
- **Adoption:** Widely used across major cloud providers today  
- **Name Meaning:** Kubernetes comes from Greek, meaning *“helmsman”* or *“pilot”*, symbolizing its role in steering applications  

Think of Kubernetes as an **orchestra conductor**. Each container is a musician. While you can manage a few musicians yourself, you need a conductor to coordinate an entire orchestra to play a complex symphony. You simply give the conductor the sheet music (your desired configuration), and they ensure every musician plays their part correctly—replacing someone who falls ill and bringing in more players.

---

## Some Features of K8s

- **Automated Scheduling** – Efficiently places containers on nodes for optimal resource use  
- **Self-Healing** – Automatically restarts, replaces, and reschedules failed containers  
- **Rollouts & Rollbacks** – Manages application updates and reverts when needed  
- **Scaling & Load Balancing** – Supports horizontal scaling and distributes traffic  
- **Resource Optimization** – Monitors and ensures efficient resource utilization  

---

## Monolithic vs Microservices

In the past, applications were built using a **monolithic architecture**, where everything was interconnected and bundled into one big codebase. This made updates risky. For example, if you wanted to change just the payment module in an e-commerce app, you had to redeploy the entire application. A small bug could crash the whole system.

**Monolithic Architecture:**
- Single large codebase  
- Tight coupling  
- Hard to scale and update  

To overcome this, the industry moved toward **microservices**, where each feature (like payments, search, or notifications) is built and deployed independently. This made applications more flexible and scalable.

But with microservices came a new challenge: instead of running one big app, companies now had to manage hundreds or thousands of small containerized services. Containers solved the packaging problem, but without a way to orchestrate them, things got messy.

That’s where **Kubernetes** came in—acting like a smart manager that automates deployment, scaling, and coordination of all those microservices.

---

## Terminologies in K8s

Think of Kubernetes as a well-organized company where different teams and systems work together to run applications efficiently.

### 1. Pod
A **Pod** is the smallest unit you can deploy in Kubernetes. It wraps one or more containers that need to run together, sharing the same network and storage. Containers inside a Pod can easily communicate and work as a single unit.

### 2. Node
A **Node** is a machine (physical or virtual) in a Kubernetes cluster that runs your applications. Each Node contains:
- Container runtime (Docker, containerd, etc.)
- Kubelet (agent)
- Kube-proxy (networking)

### 3. Cluster
A **Kubernetes cluster** is a group of computers (nodes) that work together to run containerized applications.

There are two types of nodes:

- **Master Node (Control Plane):**
  - The brain of the cluster  
  - Handles scheduling, decisions, and cluster state  

- **Worker Nodes:**
  - Run applications inside containers  
  - Include Kubelet, container runtime, and networking tools  

### 4. Deployment
A **Deployment** is a Kubernetes object used to manage a set of Pods. It provides **declarative updates**, meaning you define the desired state and Kubernetes handles the rest.

### 5. ReplicaSet
A **ReplicaSet** ensures that a specified number of identical Pods are always running.

### 6. Service
A **Service** provides a stable way for Pods to communicate with each other, even if Pods are recreated or replaced.

### 7. Ingress
**Ingress** manages external access to services in a Kubernetes cluster. It provides HTTP/HTTPS routing and acts as a reverse proxy.

### 8. ConfigMap
A **ConfigMap** stores configuration data separately from application code.

Example use case:
- Database configuration  
- API endpoints  

This allows configuration changes without rebuilding or redeploying applications.

### 9. Secret
A **Secret** securely stores sensitive information such as:
- Passwords  
- API keys  
- Tokens  

### 10. Persistent Volume (PV)
A **Persistent Volume (PV)** is storage in the cluster that persists even if a Pod is deleted or restarted.

### 11. Kubelet
The **Kubelet** runs on each Worker Node and ensures that Pods are running as expected.

### 12. Kube-proxy
**Kube-proxy** manages networking inside the cluster, enabling communication between Pods and Services.
# Introduction to Kubernetes (K8s)

**Last Updated:** 10 Sep, 2025

Before Kubernetes, Docker and Docker Swarm transformed how developers package applications. It allowed them to bundle an application and its dependencies into a single, portable unit called a **container**. This worked fine for small-scale deployments, but when applications grew to hundreds or thousands of containers, the following problems appeared:

- Scalability Issues  
- Multi-Cloud Deployments  
- Security & Resource Management  
- Rolling Updates & Zero Downtime Deployments  

This is the problem Kubernetes was created to solve. It acts as the **"brain"** or orchestrator for your containers, handling the complex task of managing them at scale automatically.

---

## What is Kubernetes?

Kubernetes, often shortened to **K8s** (K, 8 letters, s), is an open-source platform that automates the deployment, scaling, and management of containerized applications.

- **Origin:** Developed by Google, inspired by internal systems Borg and Omega  
- **Launch:** Officially released in 2014  
- **CNCF Donation:** Donated to the Cloud Native Computing Foundation (CNCF) in 2015, which now maintains it  
- **Adoption:** Widely used across major cloud providers today  
- **Name Meaning:** Kubernetes comes from Greek, meaning *“helmsman”* or *“pilot”*, symbolizing its role in steering applications  

Think of Kubernetes as an **orchestra conductor**. Each container is a musician. While you can manage a few musicians yourself, you need a conductor to coordinate an entire orchestra to play a complex symphony. You simply give the conductor the sheet music (your desired configuration), and they ensure every musician plays their part correctly—replacing someone who falls ill and bringing in more players.

---

## Some Features of K8s

- **Automated Scheduling** – Efficiently places containers on nodes for optimal resource use  
- **Self-Healing** – Automatically restarts, replaces, and reschedules failed containers  
- **Rollouts & Rollbacks** – Manages application updates and reverts when needed  
- **Scaling & Load Balancing** – Supports horizontal scaling and distributes traffic  
- **Resource Optimization** – Monitors and ensures efficient resource utilization  

---

## Monolithic vs Microservices

In the past, applications were built using a **monolithic architecture**, where everything was interconnected and bundled into one big codebase. This made updates risky. For example, if you wanted to change just the payment module in an e-commerce app, you had to redeploy the entire application. A small bug could crash the whole system.

**Monolithic Architecture:**
- Single large codebase  
- Tight coupling  
- Hard to scale and update  

To overcome this, the industry moved toward **microservices**, where each feature (like payments, search, or notifications) is built and deployed independently. This made applications more flexible and scalable.

But with microservices came a new challenge: instead of running one big app, companies now had to manage hundreds or thousands of small containerized services. Containers solved the packaging problem, but without a way to orchestrate them, things got messy.

That’s where **Kubernetes** came in—acting like a smart manager that automates deployment, scaling, and coordination of all those microservices.

---

## Terminologies in K8s

Think of Kubernetes as a well-organized company where different teams and systems work together to run applications efficiently.

### 1. Pod
A **Pod** is the smallest unit you can deploy in Kubernetes. It wraps one or more containers that need to run together, sharing the same network and storage. Containers inside a Pod can easily communicate and work as a single unit.

### 2. Node
A **Node** is a machine (physical or virtual) in a Kubernetes cluster that runs your applications. Each Node contains:
- Container runtime (Docker, containerd, etc.)
- Kubelet (agent)
- Kube-proxy (networking)

### 3. Cluster
A **Kubernetes cluster** is a group of computers (nodes) that work together to run containerized applications.

There are two types of nodes:

- **Master Node (Control Plane):**
  - The brain of the cluster  
  - Handles scheduling, decisions, and cluster state  

- **Worker Nodes:**
  - Run applications inside containers  
  - Include Kubelet, container runtime, and networking tools  

### 4. Deployment
A **Deployment** is a Kubernetes object used to manage a set of Pods. It provides **declarative updates**, meaning you define the desired state and Kubernetes handles the rest.

### 5. ReplicaSet
A **ReplicaSet** ensures that a specified number of identical Pods are always running.

### 6. Service
A **Service** provides a stable way for Pods to communicate with each other, even if Pods are recreated or replaced.

### 7. Ingress
**Ingress** manages external access to services in a Kubernetes cluster. It provides HTTP/HTTPS routing and acts as a reverse proxy.

### 8. ConfigMap
A **ConfigMap** stores configuration data separately from application code.

Example use case:
- Database configuration  
- API endpoints  

This allows configuration changes without rebuilding or redeploying applications.

### 9. Secret
A **Secret** securely stores sensitive information such as:
- Passwords  
- API keys  
- Tokens  

### 10. Persistent Volume (PV)
A **Persistent Volume (PV)** is storage in the cluster that persists even if a Pod is deleted or restarted.

### 11. Kubelet
The **Kubelet** runs on each Worker Node and ensures that Pods are running as expected.

### 12. Kube-proxy
**Kube-proxy** manages networking inside the cluster, enabling communication between Pods and Services.
