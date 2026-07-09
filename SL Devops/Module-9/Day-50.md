# Task 1: Recall the Kubernetes Story

## 1. Why was Kubernetes created? What problem does it solve that Docker alone cannot?

Docker is an excellent tool for **building, packaging, and running containers**. However, as applications grow, managing hundreds or thousands of containers across multiple servers becomes difficult.

Kubernetes was created to solve this problem through **container orchestration**. It automates the management of containerized applications, making them scalable, reliable, and highly available.

### Kubernetes automates:
- Deploying containers
- Scaling applications up or down
- Load balancing incoming traffic
- Service discovery
- Self-healing (restarting failed containers)
- Rolling updates and rollbacks

### Docker vs Kubernetes

| Docker | Kubernetes |
|---------|------------|
| Creates and runs containers | Manages containers at scale |
| Runs containers on a host | Orchestrates containers across multiple hosts |
| Manual scaling | Automatic scaling |
| Manual recovery | Automatic self-healing |

### Example

Suppose an e-commerce website normally has **2 containers** running.

During a flash sale, traffic suddenly increases from **500 users** to **50,000 users**.

- **With Docker alone:** You must manually create more containers, configure networking, and distribute traffic.
- **With Kubernetes:** It automatically creates additional containers (Pods), distributes traffic among them, and removes extra containers when traffic decreases.

---

## 2. Who created Kubernetes and what was it inspired by?

- Kubernetes was created by **Google**.
- It was inspired by Google's internal cluster management system called **Borg**.
- Google used Borg for many years to manage billions of containers in production before releasing Kubernetes as an open-source project.

---

## 3. What does the name "Kubernetes" mean?

The word **Kubernetes** comes from the Greek word meaning:

- **Helmsman**
- **Pilot**

A helmsman is the person who steers a ship, just as Kubernetes "steers" containerized applications across a cluster.

### Why is it called K8s?

**K8s** is simply an abbreviation for Kubernetes.

```
K + 8 letters + S
```

The eight letters between **K** and **S** are:

```
ubernete
```

So:

```
Kubernetes
K + ubernete + s
```

becomes

```
K8s
```

---

# Task 2: Kubernetes Architecture

## Kubernetes Architecture

```text
                        Kubernetes Cluster
┌───────────────────────────────────────────────────────────────┐
│                                                               │
│                    CONTROL PLANE (Master Node)                │
│                                                               │
│  kubectl                                                     │
│      │                                                        │
│      ▼                                                        │
│ ┌──────────────┐                                              │
│ │  API Server  │  ← Front door of the cluster                 │
│ └──────┬───────┘                                              │
│        │                                                      │
│  ┌─────┼───────────────┐                                      │
│  │     │               │                                      │
│  ▼     ▼               ▼                                      │
│┌──────────┐    ┌───────────────┐    ┌────────────────────┐     │
││  etcd    │    │   Scheduler   │    │ Controller Manager │     │
││Database  │    │ Chooses node  │    │Maintains desired   │     │
││Stores    │    │for new Pods   │    │state of cluster    │     │
││cluster   │    └───────────────┘    └────────────────────┘     │
││state     │                                                   │
│└──────────┘                                                   │
│                                                               │
├───────────────────────────────────────────────────────────────┤
│                                                               │
│                    WORKER NODE 1                              │
│                                                               │
│ ┌───────────┐                                                 │
│ │ kubelet  │ ← Communicates with API Server                   │
│ └─────┬────┘                                                 │
│       │                                                      │
│ ┌─────▼─────┐                                                │
│ │Container  │ ← containerd / CRI-O                           │
│ │ Runtime   │                                                │
│ └─────┬─────┘                                                │
│       │                                                      │
│ ┌─────▼────────────┐                                         │
│ │      Pods        │                                         │
│ └──────────────────┘                                         │
│                                                               │
│ ┌──────────────────┐                                         │
│ │   kube-proxy     │ ← Handles networking & load balancing   │
│ └──────────────────┘                                         │
│                                                               │
├───────────────────────────────────────────────────────────────┤
│                                                               │
│                    WORKER NODE 2                              │
│ (Same components as Worker Node 1)                            │
│                                                               │
└───────────────────────────────────────────────────────────────┘
```

---

# Components

## Control Plane (Master Node)

### 1. API Server

- Front door of the Kubernetes cluster.
- Every command from `kubectl`, dashboards, or applications goes through the API Server.
- Validates requests and updates the cluster state.

---

### 2. etcd

- Distributed key-value database.
- Stores the entire cluster state.
- Keeps information about:
  - Pods
  - Nodes
  - Deployments
  - Services
  - Secrets
  - ConfigMaps

Think of **etcd as Kubernetes' brain (database).**

---

### 3. Scheduler

- Watches for Pods that don't have a node assigned.
- Selects the best Worker Node based on:
  - Available CPU
  - Available Memory
  - Node labels
  - Taints & tolerations
  - Affinity rules

The Scheduler **decides where a Pod should run.**

---

### 4. Controller Manager

Continuously watches the cluster.

It ensures the **actual state** matches the **desired state**.

Example:
- Desired Pods = 3
- Running Pods = 2

The Controller Manager notices the difference and creates another Pod.

This is called the **reconciliation loop**.

---

# Worker Node Components

## 1. kubelet

- Agent running on every Worker Node.
- Communicates with the API Server.
- Receives Pod specifications.
- Starts and monitors Pods.
- Reports Pod status back to the API Server.

---

## 2. kube-proxy

Responsible for networking.

It:
- Routes traffic to Pods.
- Implements Service networking.
- Maintains networking rules.
- Performs load balancing between Pods.

---

## 3. Container Runtime

Actually runs containers.

Common runtimes:
- containerd
- CRI-O

The Container Runtime:
- Pulls container images
- Starts containers
- Stops containers
- Deletes containers

---

# What happens when you run?

```bash
kubectl apply -f pod.yaml
```

### Step 1

`kubectl` sends the Pod manifest to the **API Server**.

↓

### Step 2

The **API Server** validates the request.

↓

### Step 3

The Pod specification is stored inside **etcd**.

↓

### Step 4

The **Scheduler** notices a new Pod without a node assignment.

↓

### Step 5

The Scheduler selects the most suitable Worker Node.

↓

### Step 6

The API Server informs the **kubelet** on that Worker Node.

↓

### Step 7

The kubelet instructs the **Container Runtime** to:
- Pull the image (if needed)
- Create the container
- Start the Pod

↓

### Step 8

The kubelet reports the Pod status back to the API Server.

↓

### Step 9

The **Controller Manager** continuously monitors the Pod to ensure it remains in the desired state.

↓

### Step 10

If the Pod is exposed through a Service, **kube-proxy** updates networking rules so traffic can reach it.

---

# What happens if the API Server goes down?

- `kubectl` commands stop working.
- No new Pods can be created.
- Scheduling stops.
- Controllers cannot update the cluster.
- Existing Pods **continue running** on Worker Nodes.
- The cluster cannot be managed until the API Server is restored.

---

# What happens if a Worker Node goes down?

1. The kubelet on that node stops sending heartbeats.
2. The Control Plane detects the node failure.
3. The node is marked **NotReady**.
4. Pods running on the failed node become unavailable.
5. The Controller Manager creates replacement Pods.
6. The Scheduler assigns the new Pods to healthy Worker Nodes.
7. The kubelets on those nodes start the replacement Pods.

This process provides **self-healing**, one of Kubernetes' key features.

---

# Interview Answer (1 Minute)

> Kubernetes consists of a **Control Plane** and one or more **Worker Nodes**. The Control Plane manages the cluster through the **API Server**, **etcd**, **Scheduler**, and **Controller Manager**. The API Server receives all requests, etcd stores the cluster state, the Scheduler decides where Pods should run, and the Controller Manager ensures the actual state matches the desired state. Each Worker Node runs a **kubelet**, which communicates with the API Server, a **Container Runtime** that executes containers, and **kube-proxy**, which manages networking. When `kubectl apply -f pod.yaml` is executed, the request flows through the API Server, is stored in etcd, scheduled to a Worker Node, and the kubelet instructs the Container Runtime to start the Pod.
