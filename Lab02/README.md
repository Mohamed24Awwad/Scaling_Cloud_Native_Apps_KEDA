# ⚖️ Lab 2 - Implementing HPA in Kubernetes

## 📘 Overview
In this lab, you'll gain hands-on experience with Kubernetes **Horizontal Pod Autoscaler (HPA)** by setting up autoscaling for a deployment and generating load to see autoscaling in action.

---

## 🧩 Prerequisites
- A running **Kubernetes cluster** with **Metric Server** installed (from Lab 1).

---

## ⚙️ Exercise 2.1: Deploy Sample Application in Kubernetes

Create a simple Nginx web app to demonstrate HPA.

### 📝 Create `webapp.yaml`
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: webapp
spec:
  replicas: 2
  selector:
    matchLabels:
      app: webapp
  template:
    metadata:
      labels:
        app: webapp
    spec:
      containers:
      - image: nginx
        name: nginx
        resources:
          limits:
            cpu: "10m"
          requests:
            cpu: "10m"
```

### 🚀 Deploy and Verify
```bash
kubectl apply -f webapp.yaml
kubectl get deployments
```

### 🌐 Access the App
```bash
kubectl port-forward deploy/webapp 8080:80
curl http://localhost:8080/
```

---

## ⚖️ Exercise 2.2: Configure & Test HPA

### 🏗️ Create HPA Resource
```bash
kubectl autoscale deployment webapp --min=2 --max=5 --cpu-percent=20
kubectl get hpa
```

### 🔥 Generate Load Using Siege
```bash
siege -q -c 2 -t 1m http://localhost:8080
```

### 📈 Monitor Autoscaling
```bash
kubectl get hpa -w
```

The HPA will automatically scale pods when CPU usage exceeds thresholds.

### 🧹 Clean-up
```bash
kubectl delete hpa webapp
kubectl delete deploy webapp
```
