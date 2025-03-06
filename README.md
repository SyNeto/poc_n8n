# n8n - Proof of Concept (PoC)

This document describes how to set up **n8n** in a local environment using **Docker**. This is a proof of concept (PoC) focused on evaluating the integration of n8n in cloud environments and Kubernetes.

## 📌 Prerequisites

Before getting started, ensure you have installed:

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)

## 🚀 Installation and Execution

### 1️⃣ Clone Repository or Create a Directory

```sh
mkdir n8n-poc && cd n8n-poc
```

### 2️⃣ Create a `docker-compose.yml` File

```yaml
version: "3.8"

services:
  n8n:
    image: n8nio/n8n
    restart: always
    ports:
      - "5678:5678"
    environment:
      - N8N_BASIC_AUTH_ACTIVE=true
      - N8N_BASIC_AUTH_USER=admin
      - N8N_BASIC_AUTH_PASSWORD=admin
    volumes:
      - ./n8n_data:/home/node/.n8n
```

### 3️⃣ Start the Container

```sh
docker-compose up -d
```

### 4️⃣ Access **n8n**

- **URL:** [http://localhost:5678](http://localhost:5678)
- **User:** `admin`
- **Password:** `admin`

## 🔄 Stop and Restart

To stop **n8n**:

```sh
docker-compose down
```

To restart **n8n**:

```sh
docker-compose up -d
```

## 📦 Data Persistence

**n8n** data is stored in `./n8n_data`, ensuring that workflows and configurations are not lost when restarting the container.

## ⚙️ Additional Configuration

If you need to expose **n8n** on a different network or adjust environment variables, modify the `docker-compose.yml` file accordingly.
