# 💳 EWallet Backend
 
A scalable, microservices-based digital wallet backend built with **Spring Boot**. The system handles user registration, wallet management, fund transfers, and transaction tracking — with asynchronous messaging via **RabbitMQ** and service discovery via **Eureka**.
 
---
 
## 🏗️ Architecture
 
The project follows a **microservices architecture**, with each service independently deployable and communicating via REST and RabbitMQ.
 
```
ewallet-backend/
├── api-gateway/           # Single entry point; routes requests to services
├── eureka-server/         # Service registry and discovery
├── auth-service/          # User authentication and JWT token management
├── user-service/          # User profile management
├── wallet-service/        # Wallet creation, balance, and top-up
├── transaction-service/   # Fund transfers and transaction history
└── notification_service/  # Async email/event notifications via RabbitMQ
```
 
---
 
## 🛠️ Tech Stack
 
| Layer               | Technology                     |
|---------------------|-------------------------------|
| Framework           | Spring Boot                   |
| Service Discovery   | Netflix Eureka                |
| API Gateway         | Spring Cloud Gateway          |
| Async Messaging     | RabbitMQ                      |
| Database            | H2 (in-memory)                |
| Build Tool          | Maven                         |
| Security            | Spring Security + JWT         |
 
---
 
## ✨ Features
 
- **User Registration & Authentication** — Secure sign-up, login, and JWT-based auth
- **Wallet Management** — Create wallets and check balances
- **Fund Transfers** — Transfer funds between wallets
- **Transaction History** — Track all credits and debits
- **Async Notifications** — RabbitMQ-powered event-driven notifications
- **Service Discovery** — All services auto-register with Eureka
- **Centralized Routing** — API Gateway handles all incoming traffic
---
 
## ⚙️ Prerequisites
 
Make sure you have the following installed:
 
- Java 17+
- Maven 3.8+
- RabbitMQ (running locally on default port `5672`)
---
 
## 🚀 Getting Started
 
### 1. Clone the repository
 
```bash
git clone https://github.com/594vinayreddy/ewallet-backend.git
cd ewallet-backend/ewallet-backend
```
 
### 2. Start RabbitMQ
 
Make sure RabbitMQ is installed and running locally on the default port `5672`. You can download it from [rabbitmq.com/download.html](https://www.rabbitmq.com/download.html).
 
Once installed, start the RabbitMQ server:
 
```bash
# On Windows
rabbitmq-server
 
# On macOS (via Homebrew)
brew services start rabbitmq
 
# On Linux
sudo systemctl start rabbitmq-server
```
 
### 3. Start the services (in order)
 
Each service is a standalone Spring Boot app. Start them in this order:
 
```bash
# 1. Eureka Server
cd eureka-server && mvn spring-boot:run
 
# 2. Auth Service
cd ../auth-service && mvn spring-boot:run
 
# 3. User Service
cd ../user-service && mvn spring-boot:run
 
# 4. Wallet Service
cd ../wallet-service && mvn spring-boot:run
 
# 5. Transaction Service
cd ../transaction-service && mvn spring-boot:run
 
# 6. Notification Service
cd ../notification_service && mvn spring-boot:run
 
# 7. API Gateway (last)
cd ../api-gateway && mvn spring-boot:run
```
 
---
 
## 🌐 Service Ports (Default)
 
| Service              | Port   |
|----------------------|--------|
| Eureka Server        | 8761   |
| API Gateway          | 8080   |
| Auth Service         | 8081   |
| User Service         | 8082   |
| Wallet Service       | 8083   |
| Transaction Service  | 8084   |
| Notification Service | 8085   |
 
> All external requests should go through the **API Gateway** at `http://localhost:8080`.
 
---
 
## 📡 API Endpoints (via API Gateway)
 
All requests go through the API Gateway at `http://localhost:8080`.
 
### Auth Service
| Method | Endpoint           | Description              |
|--------|--------------------|--------------------------|
| POST   | `/auth/register`   | Register a new user      |
| POST   | `/auth/login`      | Login and get JWT token  |
 
### User Service
| Method | Endpoint        | Description                                          |
|--------|-----------------|------------------------------------------------------|
| GET    | `/user/profile` | Get user profile (pass `X-User-Id` in request header) |
 
### Wallet Service
| Method | Endpoint                   | Description                        |
|--------|----------------------------|------------------------------------|
| GET    | `/wallet/{userId}`         | Get wallet details for a user      |
| GET    | `/wallet/{userId}/balance` | Get wallet balance                 |
| GET    | `/wallet/{userId}/history` | Get wallet transaction history     |
| POST   | `/wallet/set-pin`          | Set wallet PIN                     |
| POST   | `/wallet/verify-pin`       | Verify wallet PIN                  |
| POST   | `/wallet/update-pin`       | Update wallet PIN                  |
| POST   | `/wallet/{userId}/credit`  | Credit funds to a wallet           |
| POST   | `/wallet/{userId}/debit`   | Debit funds from a wallet          |
 
### Transaction Service
| Method | Endpoint                        | Description                          |
|--------|---------------------------------|--------------------------------------|
| POST   | `/transaction/transfer`         | Transfer funds between wallets       |
| GET    | `/transaction/history/{email}`  | Get transaction history by email     |
 
---
 
## 🗄️ Database
 
This project uses **H2 in-memory database** for development. The H2 console is available at:
 
```
http://localhost:<service-port>/h2-console
```
 
> Since the database is in-memory, data resets on each restart. To persist data, configure a database like MySQL or PostgreSQL in `application.properties`.
 
---
 
## 🔔 Messaging (RabbitMQ)
 
The **notification_service** listens to RabbitMQ queues and fires notifications whenever key events occur (e.g., successful transfer, registration). You can monitor queues at the RabbitMQ Management UI:
 
```
http://localhost:15672
Default credentials: guest / guest
```
 
---
 
## 📊 Service Discovery (Eureka)
 
All services register themselves with the Eureka Server. View all registered instances at:
 
```
http://localhost:8761
```
 
---
 
## 🔮 Future Improvements
 
- **Persistent Database** — Replace H2 in-memory database with MySQL or PostgreSQL so data survives restarts and is production-ready
- **Containerization with Docker** — Dockerize each microservice and use Docker Compose to spin up the entire stack (including RabbitMQ) with a single command, eliminating manual service startup
- **New Endpoints** — Expand the API with additional endpoints
- **Centralized Config** — Add Spring Cloud Config Server to manage properties across all services from one place
- **Distributed Tracing** — Integrate Zipkin or Micrometer Tracing for end-to-end request tracing across microservices
- **Unit & Integration Tests** — Add test coverage for service layers and REST controllers using JUnit and MockMvc
---
 
## 🤝 Contributing
 
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/your-feature`)
3. Commit your changes (`git commit -m 'Add your feature'`)
4. Push to the branch (`git push origin feature/your-feature`)
5. Open a Pull Request

 
