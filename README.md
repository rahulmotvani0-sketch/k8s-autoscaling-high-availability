# Kubernetes High Availability & Auto-Scaling Engine (Lab 6)

[![Kubernetes](https://img.shields.io/badge/Kubernetes-HPA%20v2-blue?logo=kubernetes)](https://kubernetes.io/)
[![High Availability](https://img.shields.io/badge/Resilience-Pod_Disruption_Budget-green)](#)
[![Autoscaling](https://img.shields.io/badge/Scale-2_to_10_Replicas-orange)](#)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

A production-grade Kubernetes resilience, high availability, and auto-scaling implementation. Designed to survive node evictions, rolling upgrades, and traffic spikes with zero downtime.

---

## 🌟 Key Highlights

- **Horizontal Pod Autoscaling (HPA v2):** Dynamic scaling between 2 and 10 replicas triggered at 60% CPU and 75% Memory utilization.
- **Aggressive Scale-Up / Controlled Scale-Down:** Immediate scale-up with a 5-minute stabilization window on scale-down to prevent thrashing and flapping.
- **Pod Anti-Affinity:** Distributes replica pods across distinct physical nodes or availability zones to eliminate single-point-of-failure (SPOF).
- **Pod Disruption Budget (PDB):** Guarantees `minAvailable: 1` during node maintenance or Kubernetes cluster upgrades (`kubectl drain`).
- **Zero-Downtime Rolling Updates:** Configured with `maxSurge: 1` and `maxUnavailable: 0` alongside tuned readiness probes.

---

## 🚀 Quickstart

```bash
# Apply HA stack
kubectl apply -f manifests/ha-stack.yaml

# Inspect HPA
kubectl get hpa ha-microservice-hpa --watch

# Simulate cluster node maintenance (zero downtime test)
kubectl drain <node-name> --ignore-daemonsets --delete-emptydir-data
```

---

## 👤 Author
- **Engineer:** Rahul Motvani (DevOps / SRE / DevSecOps)
- **GitHub:** [github.com/rahulmotvani0-sketch](https://github.com/rahulmotvani0-sketch)
