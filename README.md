# CNS-10: Compact Naming Standard for LLM Chats

*A minimal, scalable naming convention for LLM conversation titles (≤10 characters).*

---

## 1. Overview

LLM chat histories quickly become difficult to search, organize, and revisit. Most users end up with inconsistent titles such as:

* “distributed systems notes”
* “raft question”
* “debugging today”
* “kafka thing”

These titles are not sortable, not searchable at scale, and tend to drift over time.

**CNS-10 (Compact Naming Standard)** defines a short and structured naming format for LLM conversations that is:

* **Compact** (≤10 chars)
* **Consistent**
* **Sortable**
* **Readable**
* **Scalable**
* **Tool-agnostic** (works for any LLM chat platform)

---

## 2. Design Goals

CNS-10 is built around the following principles:

### 2.1 Compactness

The title must fit in limited UI space and remain readable.

### 2.2 Sortability

Names must sort naturally in file systems, note apps, or chat lists.

### 2.3 Searchability

Users should be able to search by topic code or type code quickly.

### 2.4 Consistency Over Creativity

The standard optimizes for long-term organization rather than descriptive natural language.

### 2.5 Human-Friendly Encoding

A human should understand the category instantly.

---

## 3. Canonical Format

### CNS-10 Canonical Title Format

```
TTT K NN
```

Written without spaces:

```
TTT K NN  ->  TTTKNN
```

Where:

| Field | Length  | Description             |
| ----- | ------- | ----------------------- |
| `TTT` | 3 chars | Topic Code              |
| `K`   | 1 char  | Chat Type Code          |
| `NN`  | 2 chars | Sequence Number (01–99) |

Total: **6 characters**.

---

## 4. Example Titles

| Title    | Meaning                            |
| -------- | ---------------------------------- |
| `DSYQ01` | Distributed Systems – Question #01 |
| `NETD03` | Networking – Design #03            |
| `CRYR07` | Cryptography – Research #07        |
| `DBSB02` | Databases – Debug #02              |
| `K8SO05` | Kubernetes – Ops #05               |
| `TSTI01` | Testing – Interview Prep #01       |

---

## 5. Chat Type Codes (K)

The chat type code indicates the intent of the conversation.

| Code | Name        | Meaning / Use Case                   |
| ---- | ----------- | ------------------------------------ |
| Q    | Question    | Q&A, concept discussion              |
| D    | Design      | architecture, design decisions       |
| B    | Bug         | debugging, incident investigation    |
| P    | Performance | profiling, latency/throughput tuning |
| S    | Summary     | condensed notes, cheatsheets         |
| R    | Research    | reading papers, deep dives           |
| I    | Interview   | interview preparation                |
| C    | Code Review | review/refactor discussions          |
| T    | Tutorial    | step-by-step guides                  |
| M    | Migration   | upgrades, transitions, compatibility |
| O    | Ops         | runbooks, on-call notes              |
| L    | Learning    | learning roadmap/planning            |

---

## 6. Sequence Number (NN)

### Rule

Always use **2 digits**.

Correct:

* `DSYQ01`
* `DSYQ09`
* `DSYQ10`

Incorrect:

* `DSYQ1`
* `DSYQ9`

### Reason

Two-digit numbering preserves lexical ordering across tools.

---

## 7. Topic Code System (TTT)

Topic codes are exactly **3 characters** and must be:

* Unique
* Memorable
* Stable over time

### Topic Code Creation Rules

Recommended approach:

1. Use a meaningful abbreviation (usually 3 letters)
2. Avoid ambiguity where possible
3. If a collision occurs, assign one canonical meaning and rename the other

---

## 8. Topic Code Dictionary (Extended)

This dictionary is meant to be broad enough to cover most CS/CE/SWE topics while staying minimal and memorable.

---

# A) Distributed Systems

| Code | Topic                          |
| ---- | ------------------------------ |
| DSY  | Distributed Systems (General)  |
| CST  | Consistency Models             |
| QRM  | Quorum Systems                 |
| REP  | Replication                    |
| SHD  | Sharding                       |
| PAR  | Partitioning                   |
| CAP  | CAP Theorem                    |
| ELE  | Leader Election                |
| GSP  | Gossip Protocols               |
| MBR  | Membership / Cluster Discovery |
| FLT  | Fault Tolerance                |
| SPL  | Split Brain                    |
| RET  | Retries / Backoff              |
| IDP  | Idempotency                    |
| RFT  | Raft                           |
| PAX  | Paxos                          |
| BYZ  | Byzantine Faults               |
| BFT  | Byzantine Fault Tolerance      |
| CDT  | CRDT                           |
| SGA  | Saga Pattern                   |
| CQS  | CQRS                           |
| EVT  | Event-Driven Systems           |

---

# B) Concurrency / Parallelism

| Code | Topic              |
| ---- | ------------------ |
| CON  | Concurrency        |
| THR  | Threads            |
| ASY  | Async Programming  |
| ATM  | Atomics            |
| RCE  | Race Conditions    |
| DDL  | Deadlocks          |
| LCK  | Locks / Mutex      |
| PRL  | Parallelism        |
| MEM  | Memory Models      |
| FUT  | Futures / Promises |

---

# C) Networking / Protocols

| Code | Topic                |
| ---- | -------------------- |
| NET  | Networking (General) |
| TCP  | TCP                  |
| UDP  | UDP                  |
| IP4  | IPv4                 |
| IP6  | IPv6                 |
| DNS  | DNS                  |
| NAT  | NAT                  |
| ARP  | ARP                  |
| ICM  | ICMP                 |
| HTP  | HTTP                 |
| H2P  | HTTP/2               |
| H3P  | HTTP/3               |
| TLS  | TLS                  |
| PKI  | PKI / Certificates   |
| RPC  | RPC / gRPC           |
| CDN  | CDN / Edge           |
| QOS  | QoS                  |
| L4B  | L4 Load Balancing    |
| L7B  | L7 Load Balancing    |
| MTU  | MTU                  |
| RTT  | RTT / Latency        |

---

# D) Databases / Storage Engines

| Code | Topic                |
| ---- | -------------------- |
| DBS  | Databases (General)  |
| SQL  | Relational / SQL     |
| NOS  | NoSQL                |
| TXN  | Transactions         |
| ISO  | Isolation Levels     |
| WAL  | Write-Ahead Logging  |
| RCV  | Recovery             |
| IDX  | Indexing             |
| QRY  | Query Optimization   |
| PLN  | Query Planning       |
| JON  | Joins                |
| NOR  | Normalization        |
| KVL  | Key-Value Stores     |
| DOC  | Document Databases   |
| COL  | Column Stores / OLAP |
| LSM  | LSM Trees            |
| BTR  | B-Trees              |
| SST  | SSTables             |
| CMP  | Compaction           |
| BAK  | Backup / Restore     |
| TTL  | TTL / Expiration     |
| OBJ  | Object Storage       |
| BLK  | Block Storage        |

---

# E) Caching / Messaging / Streaming

| Code | Topic               |
| ---- | ------------------- |
| CAC  | Caching (General)   |
| CMI  | Cache Invalidation  |
| CSH  | Cache Strategies    |
| RED  | Redis               |
| MCD  | Memcached           |
| MSG  | Messaging (General) |
| KAF  | Kafka               |
| RBT  | RabbitMQ            |
| PLS  | Pulsar              |
| STM  | Streaming (General) |
| BKP  | Backpressure        |
| ORD  | Ordering Guarantees |
| ALO  | At-Least-Once       |
| AMO  | At-Most-Once        |
| EON  | Exactly-Once        |

---

# F) Operating Systems / Low-Level Systems

| Code | Topic                       |
| ---- | --------------------------- |
| OSY  | Operating Systems           |
| LNX  | Linux                       |
| KRN  | Kernel                      |
| SYC  | Syscalls                    |
| SCH  | Scheduling                  |
| IPC  | Inter-Process Communication |
| PAG  | Paging                      |
| HEA  | Heap / Allocators           |
| STK  | Stack                       |
| IOF  | I/O Fundamentals            |
| FSY  | File Systems                |
| VFS  | Virtual File System         |
| DMA  | DMA                         |
| NUM  | NUMA                        |

---

# G) Infrastructure / Cloud / Containers

| Code | Topic                  |
| ---- | ---------------------- |
| CLD  | Cloud (General)        |
| AWS  | AWS                    |
| GCP  | GCP                    |
| AZR  | Azure                  |
| CNT  | Containers             |
| DKR  | Docker                 |
| K8S  | Kubernetes             |
| HLM  | Helm                   |
| IST  | Istio / Service Mesh   |
| PRX  | Proxy                  |
| VPC  | VPC / Virtual Networks |
| IAM  | IAM                    |
| TFM  | Terraform              |
| ANS  | Ansible                |
| GIT  | Git / GitOps           |
| CIC  | CI/CD                  |

---

# H) SRE / Reliability / Observability

| Code | Topic                        |
| ---- | ---------------------------- |
| SRE  | Site Reliability Engineering |
| RLB  | Reliability                  |
| SLA  | SLA/SLO/SLI                  |
| SLO  | SLO Engineering              |
| INC  | Incident Response            |
| RCA  | Root Cause Analysis          |
| CPL  | Capacity Planning            |
| OBS  | Observability                |
| MET  | Metrics                      |
| TRC  | Tracing                      |
| LGG  | Logging                      |
| ALT  | Alerting                     |
| DSH  | Dashboards                   |
| RUN  | Runbooks                     |
| ONC  | On-call                      |

---

# I) Security / Cryptography

| Code | Topic                        |
| ---- | ---------------------------- |
| SEC  | Security (General)           |
| CRY  | Cryptography                 |
| ENC  | Encryption                   |
| HSH  | Hashing                      |
| SIG  | Digital Signatures           |
| MAC  | MAC / HMAC                   |
| KDF  | Key Derivation               |
| RNG  | Randomness                   |
| PKI  | PKI                          |
| TLS  | TLS                          |
| JWT  | JWT                          |
| OAU  | OAuth                        |
| OID  | OpenID Connect               |
| AUT  | Authentication/Authorization |
| ACL  | Access Control               |
| TMD  | Threat Modeling              |
| XSS  | XSS                          |
| CSF  | CSRF                         |
| INJ  | Injection (SQL/Command)      |
| MIT  | MITM                         |

---

# J) Programming / Runtime / Compilers

| Code | Topic                       |
| ---- | --------------------------- |
| PRG  | Programming (General)       |
| API  | API Design                  |
| OOP  | Object-Oriented Programming |
| FPX  | Functional Programming      |
| TYP  | Type Systems                |
| CMP  | Compilers                   |
| JIT  | JIT Compilation             |
| JVM  | JVM                         |
| CLR  | .NET CLR                    |
| GCX  | Garbage Collection          |
| CPP  | C++                         |
| CSH  | C#                          |
| JVA  | Java                        |
| KOT  | Kotlin                      |
| GOL  | Go                          |
| RST  | Rust                        |
| PYT  | Python                      |
| JSC  | JavaScript                  |
| TSC  | TypeScript                  |

---

# K) Algorithms / Data Structures / Math

| Code | Topic               |
| ---- | ------------------- |
| ALG  | Algorithms          |
| DST  | Data Structures     |
| GRF  | Graphs              |
| TRE  | Trees               |
| HEA  | Heaps               |
| DPX  | Dynamic Programming |
| GRE  | Greedy              |
| DNC  | Divide & Conquer    |
| SRH  | Searching           |
| SRT  | Sorting             |
| BIT  | Bit Manipulation    |
| MTH  | Math                |
| PRB  | Probability         |
| STA  | Statistics          |
| LIN  | Linear Algebra      |
| OPT  | Optimization        |

---

# L) ML / Data Engineering

| Code | Topic            |
| ---- | ---------------- |
| MLL  | Machine Learning |
| DTA  | Data Engineering |
| ETL  | ETL              |
| DWH  | Data Warehousing |
| NLP  | NLP              |
| LLM  | LLMs             |
| CVN  | Computer Vision  |
| MOP  | MLOps            |
| EVA  | Evaluation       |

---

# M) Software Engineering / Architecture Patterns

| Code | Topic                         |
| ---- | ----------------------------- |
| ARC  | Architecture                  |
| DES  | Design Patterns               |
| SOL  | SOLID                         |
| DDD  | Domain Driven Design          |
| ADR  | Architecture Decision Records |
| MOD  | Modularity                    |
| DEP  | Dependency Management         |
| MSV  | Microservices                 |
| MON  | Monolith                      |
| INT  | Integration                   |
| SEC  | Secure Design                 |

---

# N) Testing / Quality / Release

| Code | Topic               |
| ---- | ------------------- |
| TST  | Testing             |
| UTG  | Unit Testing        |
| ITG  | Integration Testing |
| E2E  | End-to-End Testing  |
| FUZ  | Fuzzing             |
| PRP  | Property Testing    |
| LNT  | Linting             |
| COV  | Coverage            |
| BLD  | Build Systems       |
| RLS  | Release Engineering |
| QUA  | Quality Engineering |

---

# O) Performance / Scalability

| Code | Topic                 |
| ---- | --------------------- |
| PRF  | Performance (General) |
| LAT  | Latency               |
| THP  | Throughput            |
| CPU  | CPU Performance       |
| IOX  | I/O Performance       |
| NDX  | Network Performance   |
| HOT  | Hotspots              |
| BTL  | Bottlenecks           |
| SCL  | Scalability           |

---

# P) Product / Engineering Management (Optional)

| Code | Topic                |
| ---- | -------------------- |
| PRD  | Product Requirements |
| PLG  | Planning             |
| OKR  | OKRs                 |
| EST  | Estimation           |
| RSK  | Risk                 |
| REV  | Review               |
| RET  | Retrospectives       |

---

## 9. Collision Policy (Mandatory Rule)

Because `TTT` is only 3 characters, collisions are inevitable.

### Canonical Collision Rule

Each code must map to **exactly one canonical meaning**.

If a collision occurs:

1. keep the most widely used meaning
2. rename the other topic using an alias

### Recommended Canonical Resolutions

| Collision | Canonical Meaning | Alternate                 |
| --------- | ----------------- | ------------------------- |
| `MEM`     | Memory Model      | Membership → `MBR`        |
| `LOG`     | DB Logging        | App Logging → `LGG`       |
| `CAP`     | CAP Theorem       | Capacity Planning → `CPL` |
| `DOC`     | Document DB       | Docker → `DKR`            |

---

## 10. Recommended Usage Rules

### Rule 1: Always Use 2-Digit Counters

Use `01` instead of `1`.

### Rule 2: Do Not Rename Codes Retroactively

Once a code is used, keep it stable.

### Rule 3: Prefer General Topics First

Use `DSY` instead of `RFT` unless the chat is specifically about Raft.

### Rule 4: Use Type Codes Consistently

If the chat is about designing something, use `D` even if questions exist.

---

## 11. Extensions (Optional)

CNS-10 is designed to fit within 10 characters.

### Extension A: 3-digit numbering

```
TTTKNNN
```

Example:

* `DSYQ103`

### Extension B: Two-type encoding

```
TTT KK NN
```

Example:

* `DSYDP01`
  (Distributed Systems – Design + Performance)

This variant is still within 7 characters.

---

## 12. Reference Examples

| Title    | Decoding                        |
| -------- | ------------------------------- |
| `DSYQ01` | Distributed Systems Question 01 |
| `CSTD02` | Consistency Design 02           |
| `NETP03` | Networking Performance 03       |
| `DBSQ04` | Databases Question 04           |
| `LSMD01` | LSM Trees Design 01             |
| `K8SO02` | Kubernetes Ops 02               |
| `SREC01` | SRE Code Review 01              |
| `CRYR07` | Cryptography Research 07        |
| `AUTB03` | Authentication Debug 03         |
| `TSTI02` | Testing Interview Prep 02       |

---

## 13. Official Definition (Publishable)

### CNS-10 Standard Definition

A conversation title is CNS-10 compliant if and only if it matches:

```
[TopicCode:3][TypeCode:1][Sequence:2]
```

Where:

* `TopicCode` is a 3-character canonical topic identifier.
* `TypeCode` is a 1-character intent identifier.
* `Sequence` is a 2-digit decimal number from `01` to `99`.

Example valid identifiers:

* `DSYQ01`
* `NETD12`
* `CRYR09`
