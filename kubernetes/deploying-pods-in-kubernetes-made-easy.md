
# 🚀 Deploying Pods in Kubernetes Made Easy

![Deploy Pods in Kubernetes Cluster](https://cdn.hashnode.com/res/hashnode/image/upload/v1728836337560/fc1c60c7-022a-4f5b-9c9a-e944ba15f8c2.png?w=1600&h=840&fit=crop&crop=entropy&auto=compress,format&format=webp)

---

## 📦 Deploy Pods in Kubernetes Cluster

This guide demonstrates how to deploy a basic HTTP server pod (`httpd`) inside a Kubernetes cluster using a simple YAML manifest.

---

## ✅ Task Overview

- Create a pod named `pod-httpd` using the `httpd` image with the `latest` tag.
- Label the pod with `app: httpd_app`.
- Name the container inside the pod as `httpd-container`.

---

## 🧑‍💻 Steps to Deploy the Pod

### 1. Create a YAML manifest for the pod

> Save the following content into a file named `pod-httpd.yaml`.

```bash
cat > pod-httpd.yaml <<EOF
apiVersion: v1
kind: Pod
metadata:
  name: pod-httpd
  labels:
    app: httpd_app
spec:
  containers:
    - name: httpd-container
      image: httpd:latest
EOF
````

📸 *Sample YAML preview:*

![pod-httpd YAML](https://cdn.hashnode.com/res/hashnode/image/upload/v1728838613883/67114734-decf-4ebd-8588-1c30a62e7569.png?auto=compress,format\&format=webp)

---

### 2. Apply the pod configuration

Run the following command to deploy your pod:

```bash
kubectl apply -f pod-httpd.yaml
```

📸 *Applying the manifest:*

![kubectl apply](https://cdn.hashnode.com/res/hashnode/image/upload/v1728838777934/41b6845c-6e74-40d9-98dc-9dd591b18ea6.png?auto=compress,format\&format=webp)

---

### 3. Verify the pod is running

Use this command to check the status of your pod:

```bash
kubectl get pods
```

📸 *Verifying pod status:*

![kubectl get pods](https://cdn.hashnode.com/res/hashnode/image/upload/v1728838889673/30a405a8-faf0-4295-ace5-9026fc0fe17f.png?auto=compress,format\&format=webp)

---

## 🏷️ Tags

\#k8s #pods #devops #kubernetes #yaml #httpd

