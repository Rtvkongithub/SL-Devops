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

# Quick Interview Answer

> Kubernetes is an open-source container orchestration platform created by Google and inspired by its internal system called Borg. Docker is used to build and run containers, whereas Kubernetes manages containers across multiple servers by automating deployment, scaling, load balancing, service discovery, self-healing, and rolling updates. The name Kubernetes means "helmsman" or "pilot," symbolizing its role in steering containerized applications. It is commonly abbreviated as **K8s**.
