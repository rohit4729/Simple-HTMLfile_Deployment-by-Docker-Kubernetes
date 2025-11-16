# 🚀 Simple HTML Deployment with Docker & Kubernetes

This project demonstrates a basic workflow for containerizing a simple static HTML website with Docker and deploying it to a Kubernetes cluster. The website is then exposed to the web using a NodePort service.

## 💡 Project Workflow

1.  **Static Content:** Start with a simple `index.html` file.
2.  **Containerize:** A `Dockerfile` is used to build a web server image (using Nginx) that serves the `index.html` file.
3.  **Push to Registry:** The built Docker image is pushed to a public registry (Docker Hub).
4.  **Deploy:** Kubernetes manifest files (`deployment.yml`) are used to create:
    * A **Deployment** to manage the application's pods, ensuring a desired number of replicas are running.
    * A **Service** (NodePort) to expose the application to external traffic on a specific port (`30080`).
  

---

## 🔧 Technology Stack

* **HTML:** The static website content.
* **Docker:** For building the container image.
* **Nginx:** As the lightweight web server inside the container.
* **Docker Hub:** As the container registry.
* **Kubernetes:** For container orchestration and deployment.
* **kubectl:** The command-line tool for interacting with Kubernetes.

---

## ⚙️ Prerequisites

Before you begin, ensure you have the following tools installed and configured:

* **Docker:** To build and push the container image. ([Install Docker](https://docs.docker.com/get-docker/))
* **Docker Hub Account:** To host your container image.
* **Kubernetes Cluster:** A running cluster, such as [Minikube](https://minikube.sigs.k8s.io/docs/start/), [kind](https://kind.sigs.k8s.io/), or Docker Desktop's built-in cluster.
* **kubectl:** The Kubernetes command-line tool. ([Install kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/))

---

## ▶️ How to Use

Follow these steps to replicate the deployment.

### 1. Repository Files

This repository contains the following key files:

* **`index.html`**: The simple webpage to be served.
* **`Dockerfile`**: Instructions to build the Nginx container image.
* **`deployment.yml`**: Kubernetes manifests for the Deployment and Service.

#### Sample `Dockerfile`

```dockerfile
# Use the official Nginx image from Docker Hub
FROM nginx:alpine

# Copy the static website files to the Nginx html directory
COPY index.html /usr/share/nginx/html

# Expose port 80 (which is the default port Nginx listens on)
EXPOSE 80
