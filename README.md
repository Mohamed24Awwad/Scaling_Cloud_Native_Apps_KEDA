

# Scaling Cloud-Native Applications with KEDA

![License](https://img.shields.io/badge/License-MIT-yellow.svg)
![Repo](https://img.shields.io/badge/KEDA--Labs-repo-blue?logo=github)

Hi Dudes, I put these labs together to give a practical, hands-on path for learning autoscaling on Kubernetes. The goal was to make step-by-step exercises that are short, repeatable, and useful whether you're experimenting locally or teaching a class.

I wrote the instructions from real lab runs, so you should find commands and sequences that actually work. If something doesn't, please open an issue or send a pull request — contributions and fixes are very welcome.

## Table of Contents

- [Labs Overview](#labs-overview)
- [What you will learn](#what-you-will-learn)
- [Prerequisites](#prerequisites)
- [Setup Instructions](#setup-instructions)
- [Labs (quick index)](#labs-quick-index)
- [Useful commands](#useful-commands)
- [Learning outcomes](#learning-outcomes)
- [References](#references)
- [License ](#license)


## Labs Overview

Below is a short summary of the three labs included in this repository. Each lab folder has a README with step-by-step instructions.

| Lab | Title | Key focus |
|-----|-------|-----------|
| Lab 01 | Setting Up the Course Lab Environment | Docker, kind, Helm, kubectl, Metrics Server setup |
| Lab 02 | Implementing HPA in Kubernetes | Horizontal Pod Autoscaler (HPA), CPU-based scaling |
| Lab 03 | Installing KEDA and Setting Up Cron Scaler | KEDA installation, Cron-based autoscaling |

## What you will learn

Here’s what you’ll walk away knowing after the labs:

- How to provision a local Kubernetes cluster with kind
- How to install and use the Metrics Server for HPA
- How to configure and test an HPA based on CPU metrics
- How to install KEDA using Helm and create ScaledObjects/ScaledJobs
- How to use KEDA’s cron scaler to automate scaling on schedules

## Prerequisites

You’ll need the following tools available in your PATH:

- Docker (or Docker Desktop)
- kubectl
- Helm
- kind (Kubernetes in Docker)
- Optional: Metrics Server installed in-cluster for HPA lab

I developed and tested these labs on a Linux host, but they run fine on Windows and macOS as long as Docker is available.

## Setup Instructions

Clone the repository and change into the project folder:

```bash
git clone https://github.com/mohamed-eldemery/KEDA-Labs.git
cd KEDA-Labs
```

Work through the labs in order — each lab folder includes a focused README with commands and expected outputs.

## Labs (quick index)

- Lab01 — Environment setup
- Lab02 — Implement HPA
- Lab03 — KEDA with Cron Scaler

## Useful commands

Quick references you’ll use a lot:

```bash
# show cluster nodes
kubectl get nodes

# watch HPA behavior in real time
kubectl get hpa -w

# list KEDA ScaledObjects
kubectl get scaledobject.keda.sh
```

## Learning outcomes

After finishing these exercises you should be comfortable:

- Building small, autoscaling-ready clusters with kind
- Using Helm to deploy components like Metrics Server and KEDA
- Creating HPA rules and testing CPU-driven scaling
- Creating KEDA ScaledObjects and ScaledJobs to implement event-driven scaling

## References

- KEDA Official Documentation: https://keda.sh/docs
- Kubernetes Autoscaling Concepts: https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale/
- Helm: https://helm.sh
- kind: https://kind.sigs.k8s.io

## License

All Rights Reserved To THE LINUX FOUNDATION

[![The Linux Foundation](https://cdn.brandfetch.io/id_CoieTrV/theme/dark/logo.svg?c=1bxid64Mup7aczewSAYMX&t=1702423853110)](https://linuxfoundation.org)





