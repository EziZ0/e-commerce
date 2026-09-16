# 🛒 SB-Ecom — Spring Boot E-Commerce REST API

A monolithic **Spring Boot 3 / Java 21** REST API for an e-commerce platform, featuring JWT-based authentication, role-based authorization (User / Seller / Admin), product & category management, shopping cart operations, order placement, and image uploads — backed by **PostgreSQL** and containerized via **Docker Compose**.

---

## ✨ Features

- 🔐 **JWT Authentication & Authorization** — stateless, cookie-based JWT auth with role-based access control (`ROLE_USER`, `ROLE_SELLER`, `ROLE_ADMIN`)
- 📦 **Product Management** — create, update, delete, search (by keyword), paginate & sort products, upload product images
- 🗂️ **Category Management** — CRUD operations for product categories
- 🛍️ **Shopping Cart** — add/update/remove items, fetch user-specific cart
- 📬 **Address Book** — manage multiple shipping addresses per user
- 📑 **Order Placement** — checkout flow with payment method capture
- 💳 **Payments** — payment record linked 1:1 with each order
- 🖼️ **File/Image Uploads** — dedicated service for handling product image uploads
- ⚠️ **Global Exception Handling** — consistent API error responses
- 🐘 **PostgreSQL + pgAdmin** — via Docker Compose for local development

---

## 🧰 Tech Stack

| Layer | Technology |
|---|---|
| Language | Java 21 |
| Framework | Spring Boot 3.5.3 |
| Security | Spring Security + JWT |
| Persistence | Spring Data JPA / Hibernate |
| Database | PostgreSQL 16 |
| Build Tool | Maven |
| Boilerplate | Lombok |
| Containerization | Docker Compose (Postgres + pgAdmin) |

---

## 📁 Project Structure

```
ecommerce/
├── docker-compose.yml
├── pom.xml
└── main/
    ├── java/com/ecommerce/project/
    │   ├── SbEcomApplication.java
    │   ├── config/            # App constants & config beans
    │   ├── controller/        # REST controllers (Auth, Product, Category, Cart, Order, Address)
    │   ├── exceptions/        # Global exception handler & custom exceptions
    │   ├── model/             # JPA entities (User, Product, Cart, Order, Payment, etc.)
    │   ├── payload/           # Request/response DTOs
    │   ├── repositories/      # Spring Data JPA repositories
    │   ├── security/          # JWT filters, providers & security config
    │   ├── service/           # Business logic (Product, Cart, Order, Address, File services)
    │   └── util/               # Auth utility helpers
    └── resources/
        └── application.properties
```

---

## 🚀 Getting Started

### Prerequisites

- Java 21+
- Maven 3.9+
- Docker & Docker Compose (for PostgreSQL/pgAdmin)

### 1. Clone the repository

```bash
git clone https://github.com/<your-username>/sb-ecom.git
cd sb-ecom
```

### 2. Start PostgreSQL & pgAdmin

```bash
docker-compose up -d
```

This spins up:
- **PostgreSQL** on `localhost:5432` (db: `myapp`, user: `postgres`, password: `postgres`)
- **pgAdmin** on [http://localhost:5050](http://localhost:5050) (login: `admin@gmail.com` / `admin`)

> ⚠️ Note: `docker-compose.yml` creates a database named `myapp`, while `application.properties` currently points to a database named `ecommerce`. Make sure both are aligned (see [Configuration](#-configuration) below) before running the app.

### 3. Configure the application

Update `main/resources/application.properties` with your local DB credentials and a secure JWT secret.

### 4. Build & run

```bash
mvn clean install
mvn spring-boot:run
```

The API will be available at `http://localhost:8080`.

---
