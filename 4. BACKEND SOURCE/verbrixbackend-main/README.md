# 📘 Verbrix - Backend

Backend service for **Verbrix: Intermediary Platform for Global Healthcare Communication**, built using **Spring Boot (Java 21)**.

This service provides secure APIs, real-time communication, and financial workflows to connect international patients with verified interpreters.

---

## 🧭 Overview

Verbrix backend is a **production-ready monolithic system** that integrates:

- Authentication & security  
- Interpreter onboarding & verification  
- Relationship lifecycle management  
- Real-time chat & video communication  
- Secure payment processing  

It exposes REST APIs and WebSocket endpoints used by the Angular frontend.

---

## 🚀 Core Features

### 🔐 Authentication & Security
- OTP-based email verification  
- JWT-based authentication (access + refresh tokens)  
- Google social login  
- Device/session management  
- Role-based access control (Client, Interpreter, Admin)  

### 👤 User & Role Management
- Multi-role system  
- Role transition (Client → Interpreter)  
- Admin-controlled verification  

### 🧾 Interpreter Onboarding
- Application submission  
- Document upload (Cloudinary)  
- Admin approval workflow  

### 🔄 Relationship Lifecycle
- REQUESTED → ACCEPTED → ACTIVE → TERMINATED  
- Controls access to services (chat, video, payment)  
- Prevents duplicate or invalid connections  

### 💬 Real-Time Chat
- WebSocket (STOMP) based messaging  
- Persistent chat storage (MongoDB)  
- Access control based on relationship state  

### 📹 Video Communication
- LiveKit integration  
- Secure token generation  
- Session-based communication  

### 💳 Payment System
- Razorpay integration  
- Idempotent order creation  
- Payment signature verification  
- Automatic refund mechanism  

### 🛠️ Admin Module
- Interpreter verification  
- Document review  
- Platform monitoring  

---

## 🏗️ Architecture

The backend follows a **layered architecture**:

### Controller Layer
- Handles HTTP requests  
- Defines REST endpoints  

### Service Layer
- Business logic  
- Workflow handling (auth, payments, relationships)  

### Repository Layer
- Database access (JPA + MongoDB)  

### Security Layer
- JWT authentication  
- Spring Security integration  

---

## 🗄️ Database Design

### PostgreSQL
Stores:
- Users  
- Roles  
- Interpreter profiles  
- Relationships  
- Payments  

### MongoDB
Stores:
- Chat messages  
- Logs  

---

## 🔗 External Integrations

- Razorpay — payment gateway  
- LiveKit — video calling  
- Cloudinary — file storage  
- Firebase — social authentication  
- Resend — email OTP delivery  

---

## 📡 API Endpoints

| Module        | Endpoint           |
|--------------|-------------------|
| Auth         | `/auth`            |
| Interpreter  | `/interpreters`    |
| Client       | `/clients`         |
| Relationship | `/relationships`   |
| Chat         | `/chat`            |
| Payment      | `/payments`        |
| Video        | `/video`           |

All endpoints are:
- JWT secured  
- Role-based  
- REST-compliant  

---

## ⚡ Real-Time Communication

### WebSocket Configuration
- Endpoint: `/ws`  
- Protocol: STOMP  

### Chat Topic
```

/topic/chat/{relationshipId}

```

### Flow
1. Validate relationship  
2. Store message  
3. Broadcast to subscribers  

---

## 🔒 Security

- JWT-based authentication  
- BCrypt password hashing  
- Role-based authorization  
- Device/session tracking  
- Secure API endpoints  

---

## ⚙️ Prerequisites

- Java 21  
- Maven or Gradle  
- PostgreSQL  
- MongoDB  

---

## ⚙️ Configuration

### Application Properties

Configure database and services in:

```

src/main/resources/application.yml

````

Example (simplified):

```yaml
spring:
  datasource:
    url: jdbc:postgresql://localhost:5432/verbrix
    username: postgres
    password: password

  data:
    mongodb:
      uri: mongodb://localhost:27017/verbrix

jwt:
  secret: your_secret_key

razorpay:
  key: your_key
  secret: your_secret
````

---

## ⚙️ Running the Application

```bash
./mvnw spring-boot:run
```

or

```bash
mvn spring-boot:run
```

Server runs on:

```
http://localhost:8080
```

---

## 📦 Build

```bash
mvn clean package
```

---

## 🐳 Docker (Optional)

```bash
docker build -t verbrix-backend .
docker run -p 8080:8080 verbrix-backend
```

---

## 🚀 Deployment

* Docker containerization
* CI/CD using GitHub Actions
* Deployment on Render

---

## 🧪 Testing Summary

* API testing using Postman
* Unit testing (Spring Boot)

### Performance

* API response: ~200–500 ms
* Efficient database queries using JPA

### Payment Reliability

* No duplicate transactions
* Auto-refund mechanism verified

---

## ⚠️ Limitations

* Load testing not performed
* Payment gateway tested in sandbox mode

---

## 🔮 Future Scope

* Multi-factor authentication
* Fraud detection system
* Subscription model
* Advanced analytics dashboard
* Multi-currency support

---

## 👨‍💻 Authors

* Raihan Alam
* Sameer Saifi
* Nancy Goyal
* Stuti

B.Tech Computer Science & Engineering
Sanskar College of Engineering & Technology

---

## 📄 License

Academic project.


