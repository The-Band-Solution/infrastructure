# 🧱 Infrastructure – *The Band* Project

This repository contains the Docker Compose configuration for running **Neo4j Community Edition 5.19** with **APOC** plugin support. It is part of the infrastructure stack for the **The Band** project.

---

## 📦 Services

- **Neo4j Community Edition**
  - Graph database with a web interface and Bolt protocol access.
  - **APOC Core** plugin enabled.
  - Configured with healthcheck and shared Docker network (`theband-network`).

---

## 🔐 Configuration via `.env`

Create a `.env` file in the root directory with the following:

```env
NEO4J_USERNAME=neo4j
NEO4J_PASSWORD=<password>
````

These variables will be used by the Docker Compose service to set up Neo4j authentication.

> 🛑 **Never commit this file to a public repository.** Make sure to add it to `.gitignore`.

---

## ▶️ How to Start

1. Create the `.env` file with your credentials.

2. Start the containers:

```bash
docker compose up -d
```

---

## 🌐 Accessing Neo4j

* **Web Interface:** [http://localhost:7474](http://localhost:7474)
* **Bolt Connection:** `bolt://localhost:7687`
* **Username:** from `NEO4J_USERNAME`
* **Password:** from `NEO4J_PASSWORD`

---

## 🔎 Visualization & Development

### Using Neo4j Browser

You can interact with the graph using the built-in browser:

```cypher
MATCH (n)-[r]->(m) RETURN n, r, m LIMIT 100;
```

### Using Neo4j Desktop + Bloom (trial)

1. Download Neo4j Desktop: [https://neo4j.com/download](https://neo4j.com/download)
2. Add a remote connection using:

   * `bolt://localhost:7687`
   * Your `.env` credentials
3. Enable **Neo4j Bloom** plugin in the Desktop and use the free trial.

---

## 🧼 Stopping and Cleaning

To stop and remove containers and volumes:

```bash
docker compose down -v
```

---

## 🗂 Project Structure

```
.
├── docker-compose.yml       # Neo4j infrastructure setup
├── .env                     # Authentication variables (not versioned)
└── README.md
```



## 🔗 Shared Network

All services are connected to the `theband-network`, allowing seamless integration with other project services (e.g., APIs, observability, messaging, etc.).

---

## ✅ Requirements

* Docker
* Docker Compose

---

