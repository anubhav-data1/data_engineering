# System Design


## Chapter 1: Scale from Zero to Millions of Users

### What key things to consider when scaling simple system incrementally to support millions of users?
- Single-server architecture → multi-tier scalable architecture
- Vertical vs. Horizontal scaling
- Load balancer for high availability
- Database replication (master-slave)
- Caching: improves response times, reduces DB load
- CDN: serves static content closer to users
- Stateless web tier: session stored externally (Redis, DB)
- Multi-data center setup with geo-routing
- Message queue decouples system components
- Sharding: horizontal scaling for databases
- Logging, Monitoring, Metrics, Automation


- System Requies super-low-latency
- 


single server setup to a globally distributed architecture


Level 1. Single Server Setup i.e. one each of web app, database, cache, storage.
Level 2. Vertical Scaling
Level 3. Add a database (RDBMS or NoSql)
Level 4. Horizontal Scaling (add server with equal load distribution)
Level  . Horizontal Scaling with load balancer
Level  . Database Replication (Master - Slave Architecture)
Level  . Adding Cache (Store data intermediate layer for faster reads for common type query)
Level  . Add CDN(Content Delivery Network) for distributing static content
Level  . 
Level  . 

---

## 2. Start Simple: Single Server Setup (Fig 1-1, 1-2)
- **All-in-one server**: web app, database, cache, storage.
- **Request flow**:
  1. User → DNS resolves to IP.
  2. Request goes to server.
  3. Server returns HTML or JSON.
- **Limitations**: no redundancy, single point of failure.

---

## 3. Separate the Database (Fig 1-3)
- Split into **Web tier** (logic) and **Data tier** (storage).
- Database choices:
  - **Relational (SQL)**: MySQL, PostgreSQL.
  - **NoSQL**: MongoDB, Redis, Cassandra.

---

## 4. Vertical vs. Horizontal Scaling
- **Vertical**: add CPU/RAM to one server. Simple but limited.
- **Horizontal**: add more servers. Better for growth and failover.

---

## 5. Add a Load Balancer (Fig 1-4)
- Distributes traffic across web servers.
- Uses private IPs internally.
- **Benefits**: fault tolerance, easy scaling.

---

## 6. Database Replication (Fig 1-5)
- **Master-slave** setup:
  - Master for writes.
  - Slaves for reads.
- **Benefits**: improved read performance, availability, disaster recovery.

---

## 7. Add a Cache Layer (Fig 1-6, 1-7)
- Use cache (Redis/Memcached) for frequent reads.
- **Read-through caching**: check cache → on miss, fetch DB → update cache.
- **Considerations**: expiration, eviction policies (LRU), SPOF mitigation.

---

## 8. Use a CDN (Fig 1-10, 1-11)
- Delivers static assets (images, CSS, JS) from servers close to users.
- **Workflow**:
  1. User requests asset.
  2. CDN checks cache or origin.
  3. Returns asset.
- **Best practices**: proper TTL, versioning, fallback strategies.

---

## 9. Make Web Servers Stateless (Fig 1-13, 1-14)
- Store sessions in external stores (Redis, DB).
- Any server can handle any request → easy auto-scaling.

---

## 10. Multi-Data Centers (Fig 1-15, 1-16)
- GeoDNS routes users to the nearest data center.
- Failover by rerouting if one center goes down.
- **Challenges**: data replication, consistency, deployment.

---

## 11. Decouple with a Message Queue (Fig 1-17, 1-18, 1-19)
- Use message queues (Kafka, RabbitMQ) for background tasks.
- **Benefits**: asynchronous processing, decoupling producers and consumers.

---

## 12. Monitoring & Automation (Fig 1-19)
- Implement logging, metrics, dashboards.
- Automate CI/CD (build → test → deploy).
- Monitor system health (CPU, memory, traffic, errors).

---

## 13. Database Sharding (Fig 1-20, 1-21, 1-22, 1-23)
- Split large databases into **shards** based on keys (e.g., `user_id % N`).
- **Challenges**: sharding key choice, hotspots, re-sharding, cross-shard joins.

---

## Final Architecture Checklist
- Load Balancer
- Stateless Web Servers
- Cache (Redis)
- CDN
- Master-Slave DB Replication
- DB Sharding
- Message Queue
- Multi-Data Centers
- Monitoring & Automation

---

> Designing for scale combines **modularity**, **redundancy**, **caching**, and **distribution**.