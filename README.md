# Containerized Web Application with PostgreSQL using Docker Compose and Macvlan/Ipvlan

## 📌 Project Overview

This project demonstrates the containerization and deployment of a web application using Docker.
It includes a Node.js + Express backend connected to a PostgreSQL database and orchestrated using Docker Compose.

The project showcases key DevOps concepts such as containerization, multi-stage Docker builds, container networking (Macvlan/Ipvlan), persistent storage, and service orchestration.

---

## 🛠 Technology Stack

* **Backend:** Node.js + Express
* **Database:** PostgreSQL
* **Containerization:** Docker
* **Orchestration:** Docker Compose
* **Networking:** Macvlan / Ipvlan
* **Volume Storage:** Docker Named Volumes

---

## 🏗 Architecture Overview

Client (Browser / Postman)
↓
Backend Container (Node.js + Express)
↓
PostgreSQL Container

The backend communicates with the PostgreSQL database using environment variables.
Both containers are connected through a custom Docker network with static IP addresses.

---

## 📁 Project Structure

```
containerized-app/
│
├── backend/
│   ├── src/
│   │   └── server.js
│   ├── package.json
│   ├── Dockerfile
│   └── .dockerignore
│
├── database/
│   ├── Dockerfile
│   └── init.sql
│
├── docker-compose.yml
└── README.md
```

---

## ⚙️ Features

* REST API with Express
* PostgreSQL database integration
* Automatic table creation on startup
* Multi-stage Docker build for optimized images
* Custom PostgreSQL Docker image
* Docker Compose orchestration
* Static IP assignment for containers
* Persistent data storage using named volumes
* Healthcheck endpoint

---

## 📡 API Endpoints

### 🔹 Health Check

```
GET /health
```

Response:

```
{
  "status": "OK"
}
```

---

### 🔹 Insert User

```
POST /users
```

Body:

```
{
  "name": "Narayan",
  "email": "narayan@email.com"
}
```

---

### 🔹 Fetch Users

```
GET /users
```

Response:

```
[
  {
    "id": 1,
    "name": "Narayan",
    "email": "narayan@email.com"
  }
]
```

---

## 🐳 Docker Implementation

### Backend Container

* Uses **multi-stage Docker build**
* Based on **Node.js Alpine image**
* Runs using **non-root user for security**
* Optimized build layers

### Database Container

* Custom PostgreSQL image
* Initialization script to create database schema
* Persistent storage using named volumes

---

## 🌐 Networking

This project uses **Macvlan / Ipvlan networking** to assign static IP addresses to containers.

Example configuration:

| Service    | IP Address    |
| ---------- | ------------- |
| Backend    | 172.20.224.51 |
| PostgreSQL | 172.20.224.50 |

📌 Note: Macvlan introduces host isolation, meaning the host machine cannot directly access containers via localhost. Therefore, API testing was performed from inside the container.

---

## 💾 Persistent Storage

Docker named volumes ensure PostgreSQL data persists even after container restarts.

Volume used:

```
pgdata
```

---

## 🚀 Running the Project

### 1️⃣ Clone Repository

```
git clone https://github.com/YOUR_USERNAME/containerized-app.git
cd containerized-app
```

---

### 2️⃣ Build and Run Containers

```
docker compose up --build
```

---

### 3️⃣ Stop Containers

```
docker compose down
```

---

## 📊 Docker Commands Used

```
docker compose up --build
docker compose down
docker ps
docker network inspect mymacvlan
docker exec backend_container
```

---

## 📷 Project Demonstration

Screenshots included:

* Docker containers running
* Network inspection proof
* API endpoints working
* Persistent volume verification

---

## 📚 Key Concepts Demonstrated

* Containerization
* Docker multi-stage builds
* Docker Compose orchestration
* Container networking (Macvlan / Ipvlan)
* Persistent volumes
* REST API development

---

## 👨‍💻 Author

**Narayan Vyas**
B.Tech Computer Science Engineering
