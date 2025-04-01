# Mastering Kubernetes: kubectl Commands, YAML Templates & GitOps Workflows

This guide includes over 50 essential `kubectl` commands grouped by category, realistic outputs, and reusable YAML templates for Helm, GitOps, and CI/CD workflows.

---

## Introduction

This cheat sheet is your comprehensive reference for working with Kubernetes, specifically designed for DevOps engineers, site reliability engineers (SREs), cloud architects, and platform engineers who interact with Kubernetes clusters daily.

It is structured into two parts:

Part 1 focuses on the foundational and essential `kubectl` commands used for operating Kubernetes resources. These commands are grouped by categories such as Cluster Management, Pod Management, Deployment Management, and more. Each command is paired with a concise explanation and expected output, helping you understand not only what to run-but also what to expect when you do.

These commands cover core concepts like:
- Nodes and clusters: Understanding the health and configuration of your Kubernetes cluster.
- Namespaces: Isolating workloads for dev, stage, and prod environments.
- Pods: The smallest deployable units in Kubernetes that encapsulate containerized applications.
- Deployments: Managing stateless apps with rolling updates and replica sets.
- Services and Ingress: Exposing workloads within or outside the cluster.

Part 2 delves into advanced topics with reusable YAML templates for Helm, GitOps, CI/CD, and Kustomize.

Here's how these concepts help in modern infrastructure workflows:
- Helm simplifies packaging and deploying applications using reusable charts, useful for maintaining versioned microservices.
- GitOps (via FluxCD or ArgoCD) treats Git as the source of truth, enabling automated synchronization between code and cluster state.
- Kustomize provides environment-specific configuration management without duplicating YAML files, helping manage overlays like dev, stage, and prod.
- CI/CD pipelines using tools like GitHub Actions automate deployments to Kubernetes right after code is pushed to your repository, reducing manual ops and human error.

Each template is written for real-world use and ready for you to customize, apply, and scale. The goal of this guide is to eliminate trial-and-error and provide a solid operational and deployment baseline.


---

## Cluster Management
**Check the version of kubectl**
```bash
kubectl version
```
**Output:**
```text
Client Version: v1.26.1
Server Version: v1.26.1
```

**Get the cluster information**
```bash
kubectl cluster-info
```
**Output:**
```text
Kubernetes control plane is running at https://127.0.0.1:6443
```

**Get the nodes in the cluster**
```bash
kubectl get nodes
```
**Output:**
```text
NAME       STATUS   ROLES    AGE   VERSION
node1      Ready    master   3d    v1.26.1
```

**Get the pods in the cluster**
```bash
kubectl get pods
```
**Output:**
```text
NAME              READY   STATUS    RESTARTS   AGE
mypod             1/1     Running   0          5m
```

**Get the services in the cluster**
```bash
kubectl get services
```
**Output:**
```text
NAME         TYPE        CLUSTER-IP     PORT(S)   AGE
kubernetes   ClusterIP   10.96.0.1      443/TCP   3d
```

## Namespace Management
**Get namespaces**
```bash
kubectl get namespaces
```
**Output:**
```text
NAME        STATUS   AGE
default     Active   3d
mynamespace Active   2d
```

**Create a namespace**
```bash
kubectl create namespace mynamespace
```
**Output:**
```text
namespace/mynamespace created
```

**Delete a namespace**
```bash
kubectl delete namespace mynamespace
```
**Output:**
```text
namespace "mynamespace" deleted
```

**Get pods in a namespace**
```bash
kubectl get pods -n mynamespace
```
**Output:**
```text
NAME         READY   STATUS    RESTARTS   AGE
app-pod      1/1     Running   0          2m
```

## Pod Management
**Get pods**
```bash
kubectl get pods
```
**Output:**
```text
mypod  1/1 Running 0 1m
```

**Describe a pod**
```bash
kubectl describe pod mypod
```
**Output:**
```text
Name: mypod
Namespace: default
...
```

**Get logs of a pod**
```bash
kubectl logs mypod
```
**Output:**
```text
Starting Nginx server...
```

**Execute a command inside a pod**
```bash
kubectl exec -it mypod -- /bin/bash
```
**Output:**
```text
root@mypod:/#
```

**Delete a pod**
```bash
kubectl delete pod mypod
```
**Output:**
```text
pod "mypod" deleted
```

## YAML Template: Deployment Manifest
**Defines a Deployment resource for managing replicas of a containerized application.**
```bash
kubectl apply -f deployment.yaml
```
**Output:**
```text
deployment.apps/nginx-deployment created
```
**YAML:**
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  replicas: 2
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:latest
        ports:
        - containerPort: 80
```

---
## Meet the Author
Emmanuel Naweji is an experienced Cloud and DevOps Architect, educator, pastor, and mentor with over 20 years in IT, over 14 years in pastoral ministry and coaching, and over 9 years of hands-on expertise building secure, scalable, and high-performing infrastructure across AWS, Azure, Google Cloud, and On-Premises.

Emmanuel is passionate about helping businesses harness the power of cloud technologies through automation, DevSecOps methodologies, SRE best approaches, and Infrastructure as Code. He has led transformative projects for enterprises and startups in Fintech, healthcare, e-commerce, and ministry-related spaces, always with a focus on performance, security, and innovation.

He offers personalized services to help individuals and organizations thrive in today's tech-driven world:
- Free Initial Consultation - Let's Talk About Your Goals (30 minutes)
- IT Consulting & Contracting for Businesses (30 minutes)
- Technology & Ministry Mentorship for Pastors & Leaders (45 minutes)

Book a 1-on-1 appointment here: https://here4you.setmore.com/emmanuel
