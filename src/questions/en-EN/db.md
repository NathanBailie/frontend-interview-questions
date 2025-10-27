<a href="../../../README.md">← Back</a>

<div align="center">
  <img src="../../../src/assets/icons/icons-for-titles/db.png">
  <h2>Databases</h2>
</div>
<br />

<details>
<summary><span>1. <b>Types</b> of databases?</span></summary>
<br />

There are several main types of databases, each suited for different tasks:

- **Relational (SQL)** — use tables, relationships, and SQL language. Examples: PostgreSQL, MySQL, Oracle.
- **Document (NoSQL)** — store data as documents (usually JSON). Examples: MongoDB, CouchDB.
- **Key-Value** — simple structure where each key maps to a value. Examples: Redis, DynamoDB.
- **Graph** — designed for storing nodes and relationships. Examples: Neo4j, ArangoDB.
- **Columnar** — optimized for analytics, store data by columns. Examples: ClickHouse, Apache Cassandra.
- **Object-Oriented** — store objects as in OOP. Examples: db4o, ObjectDB.
- **Time-Series** — specialized for time-stamped data. Examples: InfluxDB, TimescaleDB.

Each type has its own features, advantages, and use cases.

</details>

---

<details>
<summary><span>2. <b>Difference between relational and document</b> databases?</span></summary>
<br />

**Relational databases (SQL):**

- Structure: data is stored in tables with strict schemas (columns, data types).
- Relationships: support links between tables (foreign keys).
- Query language: use SQL (Structured Query Language).
- Examples: PostgreSQL, MySQL, Oracle.

**Document databases (NoSQL):**

- Structure: data is stored as documents (usually JSON), with flexible schemas.
- Relationships: typically denormalized, no strict links.
- Query language: use custom APIs or JSON-like queries.
- Examples: MongoDB, CouchDB.

**Key difference**:  
Relational DBs enforce strict schemas and are ideal for complex relationships and transactions.  
Document DBs offer flexibility and are great for nested structures and horizontal scaling.

</details>

---

<details>
<summary><span>3. What are the <b>types of relationships</b> in databases?</span></summary>
<br />

There are three main types of relationships between tables:

- **One-to-One (1:1)**  
  Each record in one table corresponds to exactly one record in another.  
  Example: user and passport.

- **One-to-Many (1:N)**  
  One record in the first table can be linked to multiple records in the second.  
  Example: author and books.

- **Many-to-Many (M:N)**  
  Multiple records in one table can relate to multiple records in another.  
  Implemented via a junction table.  
  Example: students and courses.

These relationships are implemented using **foreign keys** and help structure data in relational databases.

</details>

---

<details>
<summary><span>4. What is a <b>composite primary key</b>?</span></summary>
<br />

A **composite primary key** is a key made up of two or more columns that together uniquely identify a row in a table.

Used when no single column can guarantee uniqueness, but their combination can.

🔹 **Example**:  
In a `student_courses` table with `student_id` and `course_id`, the pair `student_id + course_id` is unique, though each column may repeat. Together, they form a composite key.

📌 **Features**:

- Ensures uniqueness via combined values.
- Common in junction tables (e.g., many-to-many relationships).
- Can complicate indexing and foreign keys but supports strict data modeling.

</details>

---

<details>
<summary><span>5. <b>Normalization vs Denormalization</b> in SQL and NoSQL?</span></summary>
<br />

🔹 **Normalization** — structuring data to minimize duplication and ensure integrity.  
Common in **relational DBs (SQL)**.

- Split data into related tables
- Use foreign keys
- Simplifies updates and deletes
- Example: `users`, `orders`, `products` with clear links

🔸 **Denormalization** — merging data for faster reads.  
Common in **NoSQL DBs**, where speed and scalability matter.

- Duplicate data for quick access
- Reduce JOINs
- More storage, faster queries
- Example: MongoDB document with user and all orders

📌 **Depends on context**:

- Normalize for complex transactions and strict schema
- Denormalize for fast access and flexible structure

</details>

---

<details>
<summary><span>6. What are <b>normal forms</b> in databases?</span></summary>
<br />

**Normal forms** are rules that help structure relational tables to eliminate redundancy and ensure data integrity.

🔹 Key normal forms:

- **1NF (First Normal Form)**  
  All values are atomic (indivisible). No repeating groups.

- **2NF (Second Normal Form)**  
  In 1NF and all non-key attributes fully depend on the primary key.

- **3NF (Third Normal Form)**  
  In 2NF and no transitive dependencies (non-key fields don’t depend on each other).

🔸 Additional forms (less common):

- **BCNF (Boyce-Codd Normal Form)** — stricter than 3NF, resolves anomalies with composite keys.
- **4NF, 5NF** — handle more complex dependencies like multivalued attributes.

📌 **Why it matters**:  
Normalization avoids duplication, simplifies updates/deletes, and keeps the schema clean and reliable.

</details>

---

<details>
<summary><span>7. <b>GROUP BY, WHERE, HAVING, JOINs</b>?</span></summary>
<br />

- **WHERE** — filters rows before aggregation (`WHERE age > 18`)
- **GROUP BY** — groups rows by column (`GROUP BY country`)
- **HAVING** — filters groups after aggregation (`HAVING COUNT(*) > 5`)
- **JOIN** — combines tables by keys:
  - `INNER JOIN` — matching rows only
  - `LEFT JOIN` — all from left + matching from right
  - `RIGHT JOIN` — all from right + matching from left
  - `FULL JOIN` — all rows from both tables

</details>

---

<details>
<summary><span>8. What are <b>transactions</b> in databases?</span></summary>
<br />

A transaction is a database operation that is either fully completed or not executed at all.

</details>

---

<details>
<summary><span>9. Describe <b>ACID properties</b></span></summary>
<br />

- **A** — Atomicity (all or nothing)
- **C** — Consistency (data remains valid)
- **I** — Isolation (transactions don’t interfere)
- **D** — Durability (changes persist after failures)

</details>

---

<details>
<summary><span>10. What are the <b>isolation levels</b>?</span></summary>
<br />

Isolation levels define how concurrent transactions affect each other:

- **Read Uncommitted** — can read uncommitted changes
- **Read Committed** — only committed data is visible
- **Repeatable Read** — same data on repeated reads, but phantom rows may appear
- **Serializable** — strictest level, full isolation, simulates sequential execution

💡 Higher levels = more safety, less performance.

</details>

---

<details>
<summary><span>11. What is the <b>strictest isolation level</b> that enforces sequential execution?</span></summary>
<br />

**Serializable** — the strictest isolation level.  
It simulates sequential execution, preventing conflicts, phantom reads, and repeat anomalies.

💡 Used when maximum consistency is required, but may reduce performance due to locking.

</details>

---

<details>
<summary><span>12. <b>Types of locks</b> in DBMS?</span></summary>
<br />

Locks in DBMS control concurrent access to data:

- **Shared Lock** — allows reading, blocks writing
- **Exclusive Lock** — blocks both reading and writing
- **Row-level Lock** — locks individual rows
- **Table-level Lock** — locks entire table
- **Intent Lock** — signals intent to lock rows or tables
- **Deadlock** — circular wait between transactions; requires resolution or rollback

💡 Locks preserve data integrity but may impact performance.

</details>

---

<details>
<summary><span>13. Why are <b>indexes</b> needed in databases? Examples of indexes</span></summary>
<br />

**Indexes** are auxiliary structures that speed up access to data in a table.

**Why they are needed:**

- Increase speed of **search**, **sorting**, **filtering**, and `JOIN`s
- Reduce **CPU** and **I/O** load for large volumes of data
- Enable **uniqueness**, **constraints**, and **fast access** by keys

**Examples:**

- `B-tree` — universal index for range and exact queries
- `Hash` — fast access by exact match
- `GIN`, `GiST` — for `JSONB`, arrays, full-text search
- **Composite index** — index on multiple columns
- **Partial index** — index on a subset of data based on a condition

</details>

---

<details>
<summary><span>14. Why is search in a B-tree faster than a full data scan?</span></summary>
<br />

**B-tree** is a balanced structure where data is stored sorted and split into blocks.

**Why it's faster:**

- Uses **logarithmic search**: at each level, a large portion of data is eliminated
- Stores **keys** and **pointers** in nodes, allowing quick navigation to the desired range
- Optimized for **disk I/O**, minimizing read operations

</details>

---

<details>
<summary><span>15. Why are <b>transactions</b> needed?</span></summary>
<br />

**Transactions** are a set of operations executed as a single unit.

**Why they are needed:**

- Ensure **data integrity** in case of failures or errors
- Guarantee **atomicity**: either all operations succeed or none
- Support **isolation**: parallel transactions don't interfere with each other
- Ensure **consistency**: data remains in a valid state
- Allow rollback of changes via `ROLLBACK` if something goes wrong

</details>

---

<details>
<summary><span>16. What is the difference between <b>WHERE and HAVING</b>?</span></summary>
<br />

`WHERE` — filters rows **before** grouping (`GROUP BY`), applies to individual records  
`HAVING` — filters groups **after** aggregation, applies to `GROUP BY` results

**Example:**

- `WHERE age > 18` — excludes rows where age is less than or equal to 18
- `HAVING COUNT(*) > 5` — excludes groups with fewer than 6 records

</details>

---

<details>
<summary><span>17. What are examples of <b>aggregate functions</b>? In which query section can they be used to filter results?</span></summary>
<br />

**Examples of aggregate functions:**

- `COUNT()` — number of rows
- `SUM()` — sum of values
- `AVG()` — average value
- `MIN()` / `MAX()` — minimum and maximum

**Where to use for filtering:**

- In the `HAVING` section, after `GROUP BY` — to filter aggregated groups
- In `SELECT` — to display results
- In `ORDER BY` — to sort by aggregate value

</details>

---

<details>
<summary><span>18. What is a <b>trigger</b>? What is it used for?</span></summary>
<br />

**Trigger** is a special procedure that automatically executes upon a specific event in a table (`INSERT`, `UPDATE`, `DELETE`).

**What it's used for:**

- Automating **logic** at the database level
- Maintaining **data integrity**
- Tracking **audit** of changes
- Implementing **business rules** without changing the application

</details>

---

<details>
<summary><span>19. What is the difference between OLAP and OLTP databases?</span></summary>
<br />

**OLTP (Online Transaction Processing)** — for fast execution of transactions: `INSERT`, `UPDATE`, `DELETE`, `SELECT`  
**OLAP (Online Analytical Processing)** — for analyzing large volumes of data: aggregation, `JOIN`, `GROUP BY`

**Differences:**

- OLTP — high write speed, small queries, normalized data
- OLAP — complex analytical queries, denormalized data, low update frequency

</details>

---

<details>
<summary><span>20. What is <b>database replication</b> and what types are there?</span></summary>
<br />

**Replication** is the process of copying and synchronizing data between multiple database servers or nodes.

**Why it's needed:**

- Increases **availability** and **fault tolerance**
- Speeds up **data reading** by distributing the load
- Provides **backup** and **geo-distribution**

**Main types:**

- **Master-Slave** — one node writes, others read
- **Master-Master** — multiple nodes can write and read, requires synchronization
- **Peer-to-Peer** — all nodes are equal, data is replicated between them
- **Log-based** — replication via transaction log
- **Snapshot** — periodic copying of database state

</details>

---

<details>
<summary><span>21. What is <b>sharding</b> and what problems are associated with it?</span></summary>
<br />

**Sharding** is horizontal partitioning of a database into parts (**shards**), each storing a subset of data.

**Why it's needed:**

- Increases **scalability** and **performance**
- Allows processing of **large volumes of data** in parallel

**Problems:**

- Complexity of **implementation** and **maintenance**
- Difficulty with `JOIN`s across shards
- Possible **load imbalance** (`hot shards`)
- Challenges in **data redistribution**
- Complicates **backup** and **recovery**

</details>

---

<details>
<summary><span>22. What problems can arise when using indexes?</span></summary>
<br />

**Problems with using indexes:**

- Slower write operations: `INSERT`, `UPDATE`, `DELETE` — due to index updates
- Excessive **memory** and **disk** usage — especially with many or complex indexes
- Poor choice — can lead to **inefficient query plans**
- Performance degradation with **frequent data changes**
- Maintenance **complexity** — need to monitor relevance and freshness

</details>

---

<details>
<summary><span>23. Describe <b>BASE</b> properties</span></summary>
<br />

- **Basically Available** — guarantees data availability, but not necessarily in real time
- **Soft State** — the system state may change over time, even without external input, allowing adaptation and recovery
- **Eventually Consistent** — ensures that data will eventually become consistent across the system

</details>

---

<details>
<summary><span>24. Describe transactional mechanisms: <b>WAL / MVCC / 2PL / Deferrable</b></span></summary>
<br />

- **WAL (Write-Ahead Logging)** — data is first recorded in a log before changes are applied. Provides high reliability but requires more resources and slightly slows down the process
- **MVCC** — each transaction sees its own version of the data. Minimizes conflicts, requires more memory, but offers high reliability
- **2PL** — two-phase locking. The transaction locks the required data before execution and releases the lock after completion. Ensures reliability without extra memory cost, but may lead to deadlocks and delays
- **Deferrable** — constraint checks are deferred until the end of the transaction. Faster if everything goes smoothly, but harder to debug in case of errors

</details>

---

<details>
<summary><span>26. Why are <b>Constraints</b> needed? Give examples</span></summary>
<br />

Constraints are rules that help ensure data correctness in database tables. They prevent errors, maintain integrity, and simplify application logic.

- **NOT NULL** — disallows empty values. For example, the "email" field must be filled
- **UNIQUE** — ensures uniqueness. For example, "username" must not be duplicated
- **FOREIGN KEY** — links tables. For example, "user_id" in orders refers to "id" in the users table
- **CHECK** — restricts acceptable values. For example, "age > 0"
- **DEFAULT** — sets a default value. For example, order status is "new" if not specified otherwise

</details>

---

<details>
<summary><span>27. What are <b>stored procedures</b> and why are they needed?</span></summary>
<br />

Stored procedures are precompiled blocks of SQL code saved in the database and can be called multiple times when needed.

- **Pros**: speed up operations, reduce network load, and improve performance
- **Cons**: make debugging and maintenance more difficult, especially with complex logic inside the database

</details>

---

<details>
<summary><span>28. What is a <b>Materialized View</b> and why is it needed?</span></summary>
<br />

A Materialized View is a snapshot of data in the database that stores the result of a pre-executed query.

- **Pros**: speeds up complex queries, reduces computational load
- **Cons**: requires additional memory and resources for updates

</details>

<!-- <details>
<summary><span><b></b></span></summary>
<br />

</details>

--- -->
