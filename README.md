# 📦 DevOps Assignment – Nginx Reverse Proxy with Docker Compose

This project sets up a microservice system with two backend services — one in **Go** and one in **Python** — behind a reverse proxy using **Nginx**, all containerized with **Docker** and orchestrated using **Docker Compose**.

---

## 🧰 Technologies Used

- 🐳 Docker & Docker Compose  
- 🌐 Nginx (Reverse Proxy)  
- ⚙️ Golang (Service 1)  
- 🐍 Python + Flask (Service 2)  
- ⚡ uv (for Python dependency management)

---

## 📁 Project Structure

```
.
├── docker-compose.yml
├── nginx/
│   ├── nginx.conf
│   └── Dockerfile
├── service_1/         # Go service
│   ├── main.go
│   ├── go.mod
│   └── Dockerfile
├── service_2/         # Python service
│   ├── app.py
│   └── Dockerfile
└── README.md
```

---

## 🚀 Getting Started

### 1️⃣ Prerequisites

- Docker Desktop installed
- Internet connection to pull base images

---

### 2️⃣ Run the System

From the root directory of the project:

```bash
docker-compose up --build
```

That’s it! 🎉 All services (Go, Python, and Nginx) will be built and started.

---

## 🌐 Available Endpoints

### ✅ Go Service (Service 1)
- `GET /service1/ping` → `{"status": "ok", "service": "1"}`
- `GET /service1/hello` → `{"message": "Hello from Service 1"}`

### ✅ Python Flask Service (Service 2)
- `GET /service2/ping` → `{"status": "ok", "service": "2"}`
- `GET /service2/hello` → `{"message": "Hello from Service 2"}`

> Access these endpoints via:

- [http://localhost:8080/service1/ping](http://localhost:8080/service1/ping)
- [http://localhost:8080/service2/ping](http://localhost:8080/service2/ping)

---

## 🌐 How Routing Works

- Nginx listens on **localhost:8080**
- Routes:
  - `/service1/*` → Go backend on port `8001`
  - `/service2/*` → Python backend on port `8002`
- All routing is based on **URL path prefixes**

---

## 📝 Key Features

- ✅ Reverse proxy setup with clean routing
- ✅ Logs for every request via Docker logs
- ✅ Modular Docker setup with separate Dockerfiles
- ✅ Uses `uv` in Python service as required
- 🔄 Easily extensible with health checks or CI/CD in the future

---

## 🧹 Stopping the System

To stop and clean up all containers:

```bash
docker-compose down
```

---

