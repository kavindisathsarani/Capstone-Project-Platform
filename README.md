# 📌 Platform - Enterprise Cloud Application (ECA) Infrastructure Layer

The **Platform layer** provides the core infrastructure required for a scalable **microservices-based Enterprise Cloud Application (ECA)**. It includes the API Gateway, Configuration Server, and Service Registry.

---

## 👩‍🎓 Student Information

| Field          | Value                                 |
| -------------- | ------------------------------------- |
| Student Name   | Kavindi Sathsarani Manimendra         |
| Student Number | 2301692042                            |
| Slack Handle   | @kavindi sathsarani                   |
| Module         | ITS 2130 Enterprise Cloud Application |
| Program        | GDSE @ IJSE                           |
| GCP Project ID | it-assignment-3                       |

---

## 📖 About

This project is part of the **Enterprise Cloud Application (ECA)** module at IJSE and focuses on building a **cloud-ready microservices infrastructure layer**.

---

## 📌 Project Description

The Platform layer consists of three core components:

### 🔹 API Gateway

* Single entry point for all client requests
* Routes requests using Spring Cloud Gateway (WebFlux)

### 🔹 Config Server

* Centralized configuration management
* Loads configs from Git repository

### 🔹 Service Registry (Eureka)

* Service registration and discovery
* Enables communication between microservices

---

## 🛠️ Technology Stack

| Technology            | Version  | Purpose              |
| --------------------- | -------- | -------------------- |
| Java                  | 25       | Programming Language |
| Spring Boot           | 4.0.3    | Backend Framework    |
| Spring Cloud          | 2025.1.0 | Microservices Tools  |
| Eureka                | -        | Service Registry     |
| Gateway               | -        | API Routing          |
| PostgreSQL            | 15+      | Database             |
| Google Cloud Platform | -        | Deployment           |
| PM2                   | -        | Process Management   |

---

## 🧩 Platform Components

### 🔹 Config Server (Port: 9000)

* Provides centralized configuration
* Must start first

---

### 🔹 Service Registry (Eureka) (Port: 9001)

### 🌐 Access Eureka Dashboard

**Local:**

```
http://localhost:9001
```

**GCP VM Instances (SSH Deployment):**

```
http://34.126.173.115:9001  
http://34.142.245.4:9001  
http://35.240.148.114:9001  
```

> These services are deployed on Google Cloud VM instances and accessed via public IPs.

---

### 🔹 API Gateway (Port: 7000)

* Routes all incoming requests
* Handles cross-cutting concerns

---

## 🏗️ Architecture

```
Client → API Gateway → Microservices
           ↓
     Service Registry
           ↓
     Config Server
```

---

## ⚙️ Setup / Getting Started

### 🔹 Prerequisites

* Java 17+ / 25
* Maven
* PostgreSQL
* Git

---

### 🔹 Clone Repository

```bash
git clone --recursive https://github.com/kavindisathsarani/Capstone-Project-Platform.git
cd Capstone-Project-Platform
```

---

### 🔹 Build

```bash
mvn clean install
```

---

### 🔹 Run Order (IMPORTANT)

1. Config Server
2. Service Registry
3. API Gateway

---

## ☁️ GCP Deployment (VM + SSH)

The platform is deployed using **Google Cloud Compute Engine (VM instances)** and managed via SSH.

### 🔹 Steps

1. Connect to VM

```bash
gcloud compute ssh <vm-name>
```

2. Clone project

```bash
git clone https://github.com/kavindisathsarani/Capstone-Project-Platform.git
```

3. Build project

```bash
mvn clean package
```

4. Run services

```bash
java -jar target/*.jar
```

5. Use PM2 for background execution

```bash
pm2 start ecosystem.config.js
pm2 save
pm2 startup
```

---

## 🧪 Verification

```bash
curl http://localhost:9001/actuator/health
curl http://localhost:7000/actuator/health
```

---

## 📊 Monitoring

* `/actuator/health`
* `/actuator/metrics`

---

## 🛠️ Troubleshooting

### Port Already in Use

```bash
lsof -i :9001
kill -9 <PID>
```

### Services Not Registering

* Ensure Config Server is running first

### 503 Errors

* Check Eureka dashboard
* Verify services are registered

---

## 📌 Status

✅ Running on GCP VM (SSH Deployment)

---
