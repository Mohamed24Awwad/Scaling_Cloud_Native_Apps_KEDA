# 🧪 Lab 1 - Setting Up the Course Lab Environment

## 📘 Overview
Before we dive into the hands-on activities, let's configure the lab environment with the following tools:

- **Docker**: Used by `kind` to provision the Kubernetes cluster.  
- **kind**: Used to create Kubernetes clusters.  
- **kubectl**: Used to manage the Kubernetes cluster.  
- **Helm**: Used for Kubernetes package management.  
- **Siege**: A load testing tool.

---

## ⚙️ Exercise 1.1: Set Up the Course Lab Environment

### 🐧 Linux Environment Setup

Will use **Ubuntu 22.04** as the base system.

#### Install Docker
```bash
curl -fsSL https://get.docker.com/ | sh
sudo systemctl enable --now docker
sudo systemctl status docker
sudo usermod -aG docker $USER
# Re-login to apply group change
docker ps
```

#### Install kubectl
```bash
curl -sSL -O "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
chmod +x kubectl
sudo mv kubectl /usr/local/bin
```

#### Install Helm
```bash
curl -sSL -O https://get.helm.sh/helm-v3.13.0-linux-amd64.tar.gz
tar -zxf helm-v3.13.0-linux-amd64.tar.gz
sudo mv linux-amd64/helm /usr/local/bin/helm
```

#### Install Siege
```bash
sudo apt-get install siege -y
```

#### Install kind
```bash
curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.20.0/kind-linux-amd64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind
kind create cluster
kubectl cluster-info --context kind-kind
kubectl get ns
```

---

### 📊 Metric Server Setup in Kubernetes
```bash
helm repo add metrics-server https://kubernetes-sigs.github.io/metrics-server/
helm upgrade --install metrics-server metrics-server/metrics-server -n kube-system --set args[0]=--kubelet-insecure-tls
kubectl get pods -n kube-system -l=app.kubernetes.io/name=metrics-server
```

✅ **Congratulations!** Your environment is ready to go!
