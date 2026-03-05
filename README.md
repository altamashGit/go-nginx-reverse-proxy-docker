# 🚀 Go Web App with Nginx Reverse Proxy (Dockerized DevOps Project)

## 📌 Project Overview

This project demonstrates how to deploy a **Go web application using Docker with production-level best practices**.

The application is served behind **Nginx as a reverse proxy** and built using a **Docker multi-stage build** to reduce image size. Security best practices are applied by running the container with a **non-root user** and restricting permissions on the application directory.

The project is orchestrated using **Docker Compose**, where the **Nginx configuration and static public files are mounted from the host machine**.

This project showcases practical **DevOps skills including container security, image optimization, reverse proxy configuration, and container orchestration.**

---

# 🧑‍💻 Author

**Altamash Alam**

DevOps & Cloud Enthusiast

---

# 🛠️ Technologies Used

* **Go (Golang)** – Backend application
* **Nginx** – Reverse proxy and static content server
* **Docker** – Containerization
* **Docker Multi-stage Build** – Image optimization
* **Docker Compose** – Multi-container orchestration
* **Linux Permissions** – Container security

---

# 🏗️ Project Architecture

```
User Browser
      │
      ▼
   Nginx (Port 80)
      │
      ▼
  Go Application (Port 3000)
```

### Flow

1. User sends request from browser
2. Nginx receives request
3. Nginx forwards API request to Go application
4. Go application processes request and returns response

---

# 📂 Project Structure

```
project-folder
│
├── main.go
├── go.mod
│
├── public
│   ├── index.html
│   ├── style.css
│   └── script.js
│
├── Dockerfile
├── docker-compose.yml
├── nginx.conf
│
└── README.md
```

---

# ⚙️ Key DevOps Implementations

## 1️⃣ Docker Multi-Stage Build

The Dockerfile uses **multi-stage builds** to:

* Compile the Go application in a builder stage
* Copy only the binary into the final lightweight image

### Benefits

✔ Smaller image size
✔ Faster container startup
✔ Reduced attack surface

---

# 🔐 Container Security (Non-Root User)

For security purposes:

* A **non-root user and group** are created inside the container
* The application directory ownership is changed

Example concept used:

```
RUN groupadd appgroup
RUN useradd -g appgroup appuser
RUN chown -R appuser:appgroup /app
USER appuser
```

### Benefits

✔ Prevents container privilege escalation
✔ Follows Docker security best practices

---

# 🌐 Nginx Reverse Proxy

Nginx is used to:

* Serve frontend static files
* Forward API requests to the Go backend

Example routing logic:

```
/           → static frontend
/api/       → Go backend
```

---

# 📦 Docker Compose Setup

`docker-compose.yml` is used to run the complete stack.

It mounts:

* **public folder**
* **nginx configuration**

from the **local machine** into the container.

### Benefits

✔ Easier configuration management
✔ Faster development iteration
✔ Clean multi-container orchestration

---

# 📥 Docker Image Published

The final optimized Docker image is pushed to **Docker Registry** for easy deployment.

Example workflow:

```
docker build -t go-nginx-app .
docker tag go-nginx-app username/go-nginx-app
docker push username/go-nginx-app
```

---

# 🚀 Running the Project

### Clone the repository

```
git clone https://github.com/yourusername/go-nginx-devops-project.git
cd go-nginx-devops-project
```

### Start containers

```
docker compose up --build
```

### Access application

```
http://localhost
```

---

# 📸 Project Screenshots

Add screenshots inside a folder:

```
screenshots/
```

Example:

```
screenshots/
├── app-ui.png
├── docker-running.png
├── nginx-container.png
```

Then add them in README like:

```
## Application UI

![UI](screenshots/app-ui.png)
```

---

# 📊 DevOps Skills Demonstrated

* Docker Multi-Stage Builds
* Secure Container Design
* Non-Root User Containers
* Reverse Proxy with Nginx
* Docker Compose Orchestration
* Image Optimization
* Docker Registry Publishing

---

# 🎯 Project Purpose

This project is built to demonstrate **practical DevOps and containerization skills** including:

* Building production-ready Docker images
* Securing containers
* Running microservices using Docker Compose
* Deploying Go applications behind Nginx

---

# ⭐ Future Improvements

* Add CI/CD pipeline (GitHub Actions / Jenkins)
* Deploy on AWS ECS or Kubernetes
* Add monitoring with Prometheus & Grafana
* Add Redis or database integration.

---

# 📜 License

This project is open-source and available for learning and portfolio use.
