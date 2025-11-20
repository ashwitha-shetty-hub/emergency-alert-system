
Emergency Alert System (EAS)

A real-time emergency alert broadcasting platform built using **Spring Boot**, **Kafka**, **Docker**, and **React**.
This system allows administrators to send alerts to users instantly while tracking the status of each message (SENT, DELIVERED, FAILED).

---

 Project Structure

```
emergency-alert-system/
│
├── backend/
│   ├── common/                # Shared utilities, DTOs, exceptions
│   ├── services/              # Core backend microservices
│   ├── ai-service/            # Optional AI-based enhancements
│   ├── spring-boot/           # Main Spring Boot application
│   └── docker-compose.yml     # Kafka + Zookeeper setup
│
├── devops/
│   ├── ci-cd/                 # GitHub Actions / Jenkins pipelines
│   ├── docker/                # Dockerfiles for all services
│   ├── configs/               # App config, environment files
│   └── k8s/                   # Kubernetes deployment files
│
└── docs/                      # Architecture, diagrams, API docs
```

---

 Features

 **Core Features**

* User registration & status tracking
* Admin can send emergency alerts
* Alerts delivered via Kafka message queue
* Real-time message status (SENT → DELIVERED)
* Store message logs
* Microservice-ready backend

 **Tech Stack**

* **Backend:** Spring Boot
* **Queue:** Apache Kafka
* **Orchestration:** Docker / Docker Compose
* **Frontend:** React (planned)
* **Database:** (Add your DB later—PostgreSQL recommended)
* **CI/CD:** GitHub Actions (planned)

---

Local Setup Guide

 Clone the Repository

```
git clone https://github.com/<username>/emergency-alert-system.git
cd emergency-alert-system
```

---

Start Kafka Using Docker

Go inside backend folder:

```
cd backend
docker compose up -d
```

This starts:

* **Zookeeper**
* **Kafka Broker**

Check logs:

```
docker logs kafka
```

---

 Run Backend (Spring Boot)

```
cd backend/spring-boot/demo
mvn spring-boot:run
```

Backend will start at:

```
http://localhost:8080
```

---

 API Endpoints (Sample)

➤ **POST /api/users/register**

Register a new user.

 ➤ **POST /api/messages/send**

Send alert message via Kafka.

➤ **GET /api/messages/status/{id}**

Get message delivery status.

*(You can update this section as your project grows.)*

---

# 🔀 Git Branching Rules (Short Version)

Use **feature branches**, never commit to main directly.

Examples:

```
ash/backend-alerts
yash/auth-service
feat/kafka-producer
fix/user-status-bug
```

Workflow:

```
git checkout main
git pull origin main
git checkout -b ash/new-feature
git add .
git commit -m "feat: added alert API"
git push origin ash/new-feature
```

Create Pull Request → Review → Merge.

---

# 🧪 Running Tests

```
mvn clean test
```

---

# 🐳 Docker Build Commands (For CI/CD)

### Build backend microservice:

```
docker build -t eas-backend ./backend/spring-boot/demo
```

### Build AI service:

```
docker build -t eas-ai ./backend/ai-service
```

---

# 📘 Documentation

All architecture (Kafka flow, ERD, sequence diagrams) will be added in the **docs/** directory.

---

# 👥 Contributors

| Name                | Role           |
| ------------------- | -------------- |
| **Ashwitha Shetty** | Developer |
| **Yash**            | Developer      |

---

# 🛡️ License

This project is licensed under the **MIT License**.
Feel free to use, modify, and distribute.

---

# 🎯 Next Improvements

* Add database support
* Integrate React dashboard
* Deploy to cloud (Render / AWS / Railway)
* Add CI/CD pipeline
* Kubernetes deployment

---

