# cpp-task-queue-scheduler
“High-performance C++ backend task queue &amp; job scheduler with REST/gRPC API, worker pool, persistence, and Azure deployment.”

# TaskQueue — High-Performance C++ Job Queue & Scheduler

**TaskQueue** is a lightweight backend system written in **C++17** that allows jobs (tasks) to be queued, scheduled, and executed asynchronously by a worker pool.  

It is inspired by distributed systems like **Celery** or **RabbitMQ**, but built from scratch in C++ to showcase **backend architecture, multithreading, persistence, APIs, and deployment**.  

This project is designed to be **real-world applicable** while also serving as a **portfolio-quality showcase** of backend software engineering.

---

## Key Features (Final Vision)

- **Core Engine**
  - Job struct with unique IDs, payload (JSON), status, priority, retries
  - Thread-safe job queue (supports priorities & delayed jobs)
  - Worker pool with dynamic thread management
  - Dispatcher loop to schedule jobs

- **Persistence**
  - SQLite (local development)
  - PostgreSQL (production-ready)
  - Track job lifecycle (queued → running → completed/failed)

- **API Layer**
  - gRPC service (`Submit`, `Status`, `List`)
  - REST gateway (optional)
  - Auth with JWT

- **Advanced Scheduling**
  - Retry policies (exponential backoff)
  - Cancel jobs in queue
  - Execute after `X` delay
  - Priority boosting

- **Cloud & CI/CD**
  - Dockerized service
  - GitHub Actions CI/CD pipeline
  - Azure deployment (App Service or AKS)

---

## 🛠️ Tech Stack

- **Language**: C++17
- **Build System**: CMake
- **Database**: SQLite (local), PostgreSQL (prod)
- **Networking**: gRPC (primary), REST (optional)
- **Libraries**:
  - `nlohmann/json` → JSON payloads
  - `uuid` → Job IDs
  - `libpqxx` → PostgreSQL client
  - `sqlite3` → Local persistence
- **Testing**: GoogleTest
- **Deployment**: Docker, GitHub Actions, Azure

---

## 📂 Project Structure

task-queue/
├─ src/
│ ├─ core/ # Job model, queue, thread pool
│ ├─ persistence/ # SQLite + PostgreSQL storage
│ ├─ api/ # gRPC + optional REST
│ └─ main.cpp # Entry point
├─ tests/ # Unit + integration tests
├─ cmake/ # CMake configs
├─ docker/ # Dockerfile + scripts
├─ .github/workflows/ # CI/CD pipelines
├─ CMakeLists.txt
└─ README.md



---

## Getting Started

### 1. Prerequisites

Install:

- **CMake ≥ 3.16**
- **C++17 compiler** (g++/clang)
- **SQLite3** + `libsqlite3-dev`
- **PostgreSQL client** (`libpqxx-dev`)
- **GoogleTest** (`libgtest-dev`)
- **pkg-config`, `uuid-dev`
- **Docker** (for deployment)

Ubuntu quick install:

```bash
sudo apt update
sudo apt install -y build-essential cmake libsqlite3-dev uuid-dev \
                    libpqxx-dev libgtest-dev libnlohmann-json-dev \
                    pkg-config docker.io

