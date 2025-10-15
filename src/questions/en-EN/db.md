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

<!-- <details>
<summary><span><b></b></span></summary>
<br />

</details>

--- -->
