# 🚀 AstroETL: Automating NASA Data Pipelines with Airflow

A complete end-to-end ETL pipeline that extracts daily data from NASA's **Astronomy Picture of the Day (APOD)** API, transforms it, and loads it into a PostgreSQL database — fully automated using **Apache Airflow (Astro Runtime)**.

---

## 📊 Table of Contents

- [Project Overview](#project-overview)
- [Tech Stack](#tech-stack)
- [Architecture Diagram](#architecture-diagram)
- [Setup Instructions](#setup-instructions)
- [Airflow Configuration](#airflow-configuration)
- [Postgres Database Table](#postgres-database-table)
- [Pipeline Flow](#pipeline-flow)
- [Future Improvements](#future-improvements)
- [Demo Screenshot](#demo-screenshot)
- [License](#license)

---

## 🌟 Project Overview

This project demonstrates a real-world data engineering workflow:

- Connects with NASA’s public **Astronomy Picture of the Day (APOD)** API.
- Extracts image metadata and descriptions.
- Transforms raw API response into structured data.
- Loads data into PostgreSQL database.
- Fully orchestrated & scheduled using Apache Airflow (Astro Runtime).

---

## 🛠 Tech Stack

| Tool           | Purpose                       |
| -------------- | ----------------------------- |
| Apache Airflow | Workflow orchestration        |
| Astro Runtime  | Simplified Airflow deployment |
| Python         | Core programming language     |
| PostgreSQL     | Data storage                  |
| NASA APOD API  | Public data source            |
| Docker         | Containerization              |
| DBeaver        | DB management & validation    |

---

## 🛠 Architecture Diagram

```mermaid
flowchart LR
    NASA_API[Create_table] --> Airflow_ETL[extract_apod]
    Airflow_ETL --> PostgresDB[transform_apod_data]
    PostgresDB --> DBeaver[load_data_to_postgres]
```

---

## 🚀 Setup Instructions

### 1⃣ Clone the repository

```bash
git clone https://github.com/your-username/AstroETL-Automating-NASA-Data-Pipelines-with-Airflow.git
cd AstroETL-Automating-NASA-Data-Pipelines-with-Airflow
```

### 2⃣ Initialize Astro Runtime (Airflow)

```bash
astro dev init
```

### 3⃣ Install Astro CLI (if not installed)

```bash
brew install astro
# or follow https://docs.astronomer.io/astro/install-cli
```

### 4⃣ Start Airflow locally

```bash
astro dev start
```

### 5⃣ Access Airflow UI

Navigate to: [http://localhost:8080](http://localhost:8080)

Default credentials:

- Username: `admin`
- Password: `admin`

---

## ⚙ Airflow Configuration

#### 1⃣ Add NASA API Connection

- **Connection ID:** `nasa_api`
- **Connection Type:** `HTTP`
- **Host:** `https://api.nasa.gov/`
- **Extras:**

```json
{"api_key": "YOUR_NASA_API_KEY"}
```

#### 2⃣ Add Postgres Connection

- **Connection ID:** `my_postgres_connection`
- **Connection Type:** `Postgres`
- **Host:** `postgres`
- **Schema:** `postgres`
- **Login:** `postgres`
- **Password:** `postgres`
- **Port:** `5432`

---

## 📄 PostgreSQL Database Table

The pipeline creates a table named `apod_data` with:

| Column      | Type               |
| ----------- | ------------------ |
| id          | SERIAL PRIMARY KEY |
| title       | VARCHAR(255)       |
| explanation | TEXT               |
| url         | TEXT               |
| date        | DATE               |
| media\_type | VARCHAR(50)        |

---

## 🔄 Pipeline Flow

1⃣ **Extract:**\
Fetch data from NASA APOD API using `SimpleHttpOperator`.

2⃣ **Transform:**\
Clean & filter required fields using `PythonTask`.

3⃣ **Load:**\
Insert data into PostgreSQL using `PostgresHook`.

---

## 🔧 Future Improvements

- Add error handling and retries.
- Store images locally or on cloud storage.
- Build data quality checks.
- Add email or Slack alerts on DAG failures.
- Extend to multiple NASA APIs.

---

## 📸 Demo Screenshot


![Screenshot 2025-06-19 080830](https://github.com/user-attachments/assets/ca9173a6-961e-4e66-a1b0-9ac80f22e0fd)
![Screenshot 2025-06-19 081150](https://github.com/user-attachments/assets/449d6502-e78f-4710-b537-efab11255406)

---

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

---

## ✨ Credits

Made with ❤️ by Sadab Ali.

