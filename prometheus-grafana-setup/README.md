### 🚀 Prometheus & Grafana Setup on Kubernetes

A hands-on setup where I learned how to **monitor a Kubernetes cluster** using **Prometheus** and **Grafana** deployed via **Helm**, and visualized metrics through Grafana dashboards.

---

## 🧩 Overview

In this project, I explored:

- Setting up **Prometheus** on Kubernetes using Helm.
- Accessing Prometheus through port-forwarding.
- Integrating **Grafana** with Prometheus.
- Importing ready-made dashboards for visualization (Dashboard ID: `3226`).

---

## ⚙️ Prerequisites

Make sure you have:
- A running **Kubernetes cluster** (Minikube)
- **kubectl**
- **Helm**
- **Docker**

```bash
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
```

## 🧭 Step 2: Install Prometheus
```
helm install prometheus prometheus-community/prometheus
```

Check running services:
```
kubectl get svc
```

## 📡 Step 3: Access Prometheus

Expose Prometheus locally using port forwarding:

```
kubectl port-forward svc/prometheus-server 9090:80
```

Now open Prometheus in your browser:

👉 http://localhost:9090

## 📊 Step 4: Access Grafana

Grafana is automatically installed via the Helm chart.
Check if the service is running:

```
kubectl get svc
```

Expose Grafana using port-forwarding:
```
kubectl port-forward svc/grafana 3000:80
```

Then visit Grafana in your browser:
👉 http://localhost:3000

Default credentials:

Username: admin
Password: admin

## 🔗 Step 5: Connect Grafana to Prometheus

- In Grafana:

- Go to Settings → Data Sources → Add data source

- Select Prometheus

- Set the URL to:

`http://prometheus-server.default.svc.cluster.local`


Click Save & Test

📈 Step 6: Import Dashboard

- Go to Dashboards → Import

- Enter dashboard ID: 3226

- Choose the Prometheus data source

View beautiful real-time metrics 🎉

## 🖼️ Screenshots
Prometheus Dashboard	Grafana Dashboard

	
## 🧠 Key Learnings

- How to deploy Prometheus & Grafana using Helm
- How to visualize Kubernetes metrics with Grafana
- How to use `kubectl port-forward` for local access
- How Prometheus scrapes metrics and Grafana queries them

---
