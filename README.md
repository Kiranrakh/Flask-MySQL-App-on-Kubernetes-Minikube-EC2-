# Flask-MySQL-App-on-Kubernetes-Minikube-EC2-
Deploy a Flask + MySQL Web App using Docker and Kubernetes via Minikube on a single AWS EC2 Ubuntu instance.


## 🚀 Project Goal  
**Deploy a Flask + MySQL Web App** using **Docker** and **Kubernetes** via **Minikube** on a single **AWS EC2 Ubuntu instance**.

---

## 🔧 Tools Involved  
- AWS EC2  
- Docker  
- Minikube (Kubernetes)  
- kubectl  
- Flask (Python backend)  
- MySQL (Database)  
- Kubernetes YAMLs (Deployment, Service, PVC)

---

## ✅ FULL PROJECT STEPS

---

### 🔹 Step 1: Launch EC2 Instance on AWS

- **AMI**: Ubuntu 22.04 LTS  
- **Instance Type**: t2.medium (2 vCPU, 4GB RAM)  
- **Ports to open**:
  - 22 (SSH)
  - 30000–32767 (NodePort)
  - 80 (optional, for HTTP)

---

### 🔹 Step 2: Install Docker

```bash
sudo apt update
sudo apt install -y docker.io
sudo systemctl start docker
sudo systemctl enable docker
sudo usermod -aG docker $USER
newgrp docker
```

---

### 🔹 Step 3: Install kubectl and Minikube

```bash
# Install kubectl
curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl
chmod +x kubectl
sudo mv kubectl /usr/local/bin/

# Install Minikube
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
```

---
### 🔹 Step 7: Deploy to Kubernetes
```
Create project files
OR
clone gitHub Repo: "https://github.com/Kiranrakh/Flask-MySQL-App-on-Kubernetes-Minikube-EC2-"

```
### 🔹 Step 5: Build and Push Docker Image to Docker Hub

```
docker build -t kiran22222/flask-k8s-app:v1 .
docker run -p 5000:5000 kiran22222/flask-k8s-app:v1
docker login
docker push kiran22222/flask-k8s-app:v1

```
---
### 🔹 Step 6: Start Minikube with Docker driver

```bash
minikube start --driver=docker
```

Check node:
```bash
kubectl get nodes
```

---
### 🔹 Step 7: Deploy to Kubernetes

```bash
kubectl apply -f mysql-deployment.yml
kubectl apply -f flask-deployment.yml
```

---

In your browser:
```
http://<EC2 Public IP>:30001
```

You should see "Welcome to the Flask + MySQL TODO API 🚀".

GET http://<EC2-IP>:30001/

### 🔹GET Request to /tasks 
GET http://<EC2-IP>:30001/tasks
[
  {
    "id": 1,
    "task": "Deploy Flask app on Kubernetes"
  },
  {
    "id": 2,
    "task": "Connect Flask to MySQL DB"
  }
]

### 🔹POST Request to /tasks
POST http://<EC2-IP>:30001/tasks



---
