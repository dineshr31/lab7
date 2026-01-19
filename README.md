# lab7
Below is a **clean, exact, step-by-step guide for Program-7**
❌ No extra theory
❌ No optional steps removed
✅ Exactly follows your lab manual order and commands

---

# ✅ Program-7

## Deploy a Web Application to Kubernetes using Minikube

---

## 🔹 Step 0: Prerequisites

Ensure **Minikube** and **kubectl** are installed.

Check:

```bash
minikube version
kubectl version --client
```

---

## ▶️ Step 1: Start Minikube

```bash
minikube start
```

---

## 🔍 Step 2: Check Minikube Status

```bash
minikube status
```

---

## ✅ Step 3: Verify Status (Should be similar)

```
type: Control Plane
host: Running
kubelet: Running
apiserver: Running
kubeconfig: Configured
```

---

## 🔄 Step 4: If Minikube is NOT Running

```bash
minikube delete
minikube start --driver=docker
```

---

## 📁 Step 5: Create Deployment File

```bash
nano nginx-deployment.yaml
```

**Paste EXACT content:**

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

Save → **CTRL + X → Y → Enter**

---

## 🚀 Step 6: Apply the Deployment

```bash
kubectl apply -f nginx-deployment.yaml
```

---

## 📊 Step 7: Check Deployment and Pods

```bash
kubectl get deployments
kubectl get pods
```

---

## 🌐 Step 8: Expose the Deployment as a Service

```bash
kubectl expose deployment nginx-deployment \
--type=NodePort \
--port=80
```

---

## 🔎 Step 9: Check Services

```bash
kubectl get services
```

---

## 🌍 Step 10: Access the Web Application

```bash
minikube service nginx-deployment
```

✔️ NGINX welcome page will open in browser

---

## 🧹 Step 11: Clean-up – Delete Pods

```bash
kubectl delete pods --all
```

---

## 🧹 Step 12: Delete All Services

```bash
kubectl delete svc --all
```

---

## 🧹 Step 13: Delete All Deployments

```bash
kubectl delete deployments --all
```

---

## 📁 Final Project Structure

```
Program-7/
│
└── nginx-deployment.yaml
```

---

