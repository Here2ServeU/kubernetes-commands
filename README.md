# Mastering Kubernetes: kubectl Commands, YAML Templates & GitOps Workflows

This guide includes over 50 essential `kubectl` commands grouped by category, realistic outputs, and reusable YAML templates for Helm, GitOps, CI/CD, and Kustomize workflows.

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
## Part 1: Foundational and Essential kubectl Commands

### Cluster Management

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

### Namespace Management

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

### Pod Management

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

### Deployment Management

**Get deployments**
```bash
kubectl get deployments
```
**Output:**
```text
NAME           READY   UP-TO-DATE   AVAILABLE   AGE
mydeployment   3/3     3            3           5m
```

**Describe a deployment**
```bash
kubectl describe deployment mydeployment
```
**Output:**
```text
Name: mydeployment
Namespace: default
Replicas: 3 desired | 3 updated | 3 available
```

**Scale a deployment**
```bash
kubectl scale deployment mydeployment --replicas=3
```
**Output:**
```text
deployment.apps/mydeployment scaled
```

**Delete a deployment**
```bash
kubectl delete deployment mydeployment
```
**Output:**
```text
deployment.apps "mydeployment" deleted
```

### Service Management

**Get services**
```bash
kubectl get services
```
**Output:**
```text
NAME         TYPE        CLUSTER-IP     PORT(S)   AGE
myservice    ClusterIP   10.96.0.2      80/TCP    1h
```

**Describe a service**
```bash
kubectl describe service myservice
```
**Output:**
```text
Name: myservice
Type: ClusterIP
IP: 10.96.0.2
```

**Delete a service**
```bash
kubectl delete service myservice
```
**Output:**
```text
service "myservice" deleted
```

### YAML Template: Deployment Manifest
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

### YAML Template: Service Manifest (ClusterIP)
**Exposes a Deployment within the cluster using ClusterIP.**
```bash
kubectl apply -f service.yaml
```
**Output:**
```text
service/nginx-service created
```
**YAML:**
```yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
spec:
  selector:
    app: nginx
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
  type: ClusterIP
```

---

## Part 2: GitOps, CI/CD & Kustomize Templates

This section includes YAML templates to implement GitOps workflows with ArgoCD and FluxCD, CI/CD pipelines using GitHub Actions, and Kustomize overlays for managing environments.

### Helm Chart Deployment
**Use Helm to install a chart for NGINX ingress controller.**
```bash
helm install nginx-ingress ingress-nginx/ingress-nginx
```
**Output:**
```text
NAME: nginx-ingress
LAST DEPLOYED: today
NAMESPACE: default
STATUS: deployed
```
**YAML:**
```yaml
helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
helm repo update
helm install nginx-ingress ingress-nginx/ingress-nginx
```

### GitOps Deployment Example (ArgoCD Application)
**Define an ArgoCD Application manifest to sync with a Git repo for automated deployment.**
```bash
kubectl apply -f argocd-app.yaml
```
**Output:**
```text
application.argoproj.io/myapp created
```
**YAML:**
```yaml
apiVersion: argoproj.io/v1alpha1
kind: Application
metadata:
  name: myapp
  namespace: argocd
spec:
  project: default
  source:
    repoURL: https://github.com/myorg/myapp-k8s
    targetRevision: HEAD
    path: .
  destination:
    server: https://kubernetes.default.svc
    namespace: default
  syncPolicy:
    automated:
      prune: true
      selfHeal: true
```

### EKS Cluster IAM Role Mapping
**Map an IAM user or role to Kubernetes RBAC using aws-auth ConfigMap.**
```bash
kubectl edit configmap aws-auth -n kube-system
```
**Output:**
```text
configmap/aws-auth edited
```
**YAML:**
```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: aws-auth
  namespace: kube-system
data:
  mapRoles: |
    - rolearn: arn:aws:iam::111122223333:role/eksNodeRole
      username: system:node:{{EC2PrivateDNSName}}
      groups:
        - system:bootstrappers
        - system:nodes
```

### FluxCD GitRepository Resource
**Defines a Git repository source for syncing with Kubernetes.**
```bash
kubectl apply -f flux-gitrepo.yaml
```
**Output:**
```text
gitrepository.source.toolkit.fluxcd.io/my-repo created
```
**YAML:**
```yaml
apiVersion: source.toolkit.fluxcd.io/v1beta1
kind: GitRepository
metadata:
  name: my-repo
  namespace: flux-system
spec:
  interval: 1m0s
  url: https://github.com/your-org/your-repo
  ref:
    branch: main
```

### FluxCD Kustomization Resource
**Syncs and applies Kubernetes manifests from a Git repo.**
```bash
kubectl apply -f flux-kustomization.yaml
```
**Output:**
```text
kustomization.kustomize.toolkit.fluxcd.io/my-app created
```
**YAML:**
```yaml
apiVersion: kustomize.toolkit.fluxcd.io/v1beta1
kind: Kustomization
metadata:
  name: my-app
  namespace: flux-system
spec:
  interval: 1m0s
  path: ./manifests
  prune: true
  sourceRef:
    kind: GitRepository
    name: my-repo
  targetNamespace: default
```

### Kustomize Overlay Example
**Base + overlay structure to manage multiple environments.**
```bash
kubectl apply -k overlays/dev
```
**Output:**
```text
deployment.apps/my-app configured
```
**YAML:**
```yaml
# overlays/dev/kustomization.yaml
resources:
  - ../../base
patchesStrategicMerge:
  - patch-deployment.yaml
```

### GitHub Actions Kubernetes Deploy Workflow
**CI/CD pipeline to build, push Docker image, and deploy to Kubernetes.**
```bash
git push triggers GitHub Actions
```
**Output:**
```text
✔ Deployed to Kubernetes cluster via GitHub Actions
```
**YAML:**
```yaml
# .github/workflows/deploy.yml
name: CI/CD Deploy to Kubernetes
on:
  push:
    branches:
      - main
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2
    - name: Set up Kubeconfig
      run: echo "${{ secrets.KUBECONFIG }}" > $HOME/.kube/config
    - name: Deploy to K8s
      run: kubectl apply -f k8s/
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
