## Structured Databases in Azure

Structured databases store data in **tables with fixed schema** (rows and columns). Best for transactional systems, banking apps, HR systems, ERP, etc.

| Azure Service                 | Type                      | Use Case                | Example                    |
| ----------------------------- | ------------------------- | ----------------------- | -------------------------- |
| Microsoft Azure SQL Database  | Relational (SQL)          | OLTP applications       | Employee management system |
| Azure SQL Managed Instance    | Managed SQL Server        | Lift-and-shift SQL apps | On-prem SQL migration      |
| Azure Database for PostgreSQL | Open-source relational DB | Web apps, analytics     | SaaS application           |
| Azure Database for MySQL      | Relational DB             | CMS/websites            | WordPress backend          |
| Azure Database for MariaDB    | Relational DB             | Lightweight apps        | Small business apps        |
| Azure Synapse Analytics       | Data warehouse            | Large-scale analytics   | BI reporting               |

### Key Characteristics

* Fixed schema
* ACID transactions
* SQL queries
* Strong consistency
* Best for structured records

### Real Example

Banking application:

* Customer table
* Account table
* Transaction table

Relationships are important, so Azure SQL Database is used.

---

## Unstructured Databases / Storage in Azure

Unstructured data has **no fixed schema**. Includes images, videos, logs, PDFs, IoT data, JSON, social media content, etc.

| Azure Service                               | Type              | Use Case                        | Example                 |
| ------------------------------------------- | ----------------- | ------------------------------- | ----------------------- |
| Azure Blob Storage                          | Object storage    | Images/videos/backups           | Website image uploads   |
| Azure Data Lake Storage Gen2                | Big data storage  | Analytics workloads             | Hadoop/Spark processing |
| Azure Cosmos DB                             | NoSQL database    | Globally distributed apps       | Chat apps, gaming       |
| Azure Table Storage                         | Key-value NoSQL   | Semi-structured data            | Device telemetry        |
| Azure Cache for Redis                       | In-memory NoSQL   | Caching/session storage         | Fast login sessions     |
| Azure Managed Instance for Apache Cassandra | Wide-column NoSQL | Large-scale distributed systems | IoT platforms           |

### Key Characteristics

* Flexible schema
* High scalability
* JSON/document/key-value storage
* Handles massive data volumes
* Best for rapidly changing data

### Real Example

Instagram-like application:

* Images → Blob Storage
* User posts/comments → Cosmos DB
* Logs → Data Lake

---

## Structured vs Unstructured

| Feature        | Structured DB   | Unstructured DB      |
| -------------- | --------------- | -------------------- |
| Schema         | Fixed           | Flexible             |
| Data Format    | Tables          | JSON, files, objects |
| Query Language | SQL             | NoSQL/APIs           |
| Scalability    | Vertical mostly | Horizontal           |
| Best For       | Transactions    | Big data/content     |
| Example        | Azure SQL DB    | Cosmos DB            |

---

## Interview One-Liner

**Structured database:**
“Stores organized data in tables with predefined schema using SQL.”

**Unstructured database:**
“Stores flexible or schema-less data like JSON, files, images, and logs using NoSQL/object storage approaches.”
