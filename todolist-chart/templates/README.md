# Kubernetes Final Project - TodoList App 📝

This project deploys a full-stack microservices application (Frontend, Backend, Database) on Kubernetes using Helm.
Developed as a final project for the Cloud Native Development course.

## 🚀 Features

* **Microservices Architecture:** separated Vue.js frontend, Go backend, and MariaDB database.
* **StatefulSet:** Used for the database to ensure data persistence.
* **InitContainers:** Implemented to dynamically download and inject a custom title image based on configuration.
* **Configuration Management:** Uses `ConfigMaps` and `Secrets` to decouple config from code.
* **Security:** Implemented `NetworkPolicies` to restrict database access.
* **Autoscaling:** `HPA` configured for the frontend service.
* **Package Management:** Fully packaged as a Helm Chart and hosted on GHCR.

## 🛠️ Installation

You can install the chart directly from the GitHub Container Registry:

```bash
# 1. Login to GHCR (if required, usually public)
helm registry login ghcr.io -u am1its

# 2. Install the chart
helm install my-todo oci://ghcr.io/am1its/todolist-k8s/todolist \
  --version 0.1.0 \
  --set database.rootPassword=secret123
  ```

 ##  🖥️ Usage
After installation, follow the instructions printed in the terminal (NOTES.txt) to access the application via port-forward:

```Bash
kubectl port-forward svc/todos-api-svc 8081:8080 &
kubectl port-forward svc/todolist-frontend 8000:80 &
Open http://localhost:8000 in your browser.
```

## 📸 Screenshots



## Pods & Services
  NAME                      READY   STATUS    RESTARTS   AGE
pod/mariadb-0             1/1     Running   0          5m
pod/todolist-frontend-x   1/1     Running   0          5m
pod/todos-api-x           1/1     Running   0          5m