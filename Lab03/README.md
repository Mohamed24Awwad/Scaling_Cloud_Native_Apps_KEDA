# ⏰ Lab 3 - Installing KEDA and Setting Up Cron Scaler

## 📘 Overview
This lab provides hands-on experience installing **KEDA** in Kubernetes and configuring a **Cron Scaler** to scale workloads based on a schedule.

---

## 🧩 Prerequisites
- Kubernetes cluster with Metric Server installed (Lab 1).

---

## ⚙️ Exercise 3.1: Install KEDA Using Helm Chart

### 🪄 Install KEDA
```bash
helm repo add kedacore https://kedacore.github.io/charts
helm repo update
helm upgrade -i keda kedacore/keda --namespace keda --create-namespace
```

### ✅ Verify Installation
```bash
kubectl get deployment -n keda
```

### 🚀 Create Sample Deployment
```bash
kubectl create deploy myapp --image nginx --replicas=2
kubectl get deployments
```

---

## 🕒 Create Cron ScaledObject

### 📝 `cron.yaml`
```yaml
apiVersion: keda.sh/v1alpha1
kind: ScaledObject
metadata:
  name: cron-scaledobject
  namespace: default
spec:
  scaleTargetRef:
    name: myapp
  triggers:
  - type: cron
    metadata:
      timezone: Asia/Kolkata
      start: 30 * * * *
      end: 45 * * * *
      desiredReplicas: "10"
```

### ⚙️ Apply Configuration
```bash
kubectl apply -f cron.yaml
kubectl get scaledobject.keda.sh
```

### 📊 Observe Scaling Behavior
```bash
watch kubectl get all
```

When the time window starts, replicas increase to the desired count.

🧠 **Tip:** Explore other KEDA scalers for different metrics and event sources!
