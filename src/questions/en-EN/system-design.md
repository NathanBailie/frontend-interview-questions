<a href="../../../README.md">← Back</a>

<div align="center">
<img src="../../assets/icons/icons-for-titles/system-design.png">
<h2>System Design</h2>
</div>
<br />

<details>
<summary><span>1. What are the types of <b>IS architectures</b>?</span></summary>
<br />

1. **File-server** — a simple architecture where the server only stores files, while data processing occurs on the user's PC.

   > _Examples:_ Local networks in small offices with shared folders, old versions of "1C:Enterprise 7.7", simple databases based on Microsoft Access.

2. **Client-server** — a division into service providers (servers) and service consumers (clients).

   > _Examples:_ Modern websites, banking systems, online games (e.g., World of Warcraft), corporate ERP systems (SAP, Oracle).

3. **Peer to Peer (P2P)** — a decentralized network where each participant acts as both a client and a server simultaneously.
   > _Examples:_ BitTorrent network for file sharing, blockchain networks (Bitcoin, Ethereum), messengers with end-to-end encryption (certain features of Signal or Briar).

</details>

---

<details>
<summary><span>2. What are the main <b>system criteria</b>?</span></summary>
<br />

- **Availability** — the proportion of time during which the system is in a working state and ready to respond to user requests (often measured in "nines," e.g., 99.9%).
- **Efficiency** — the system's ability to perform tasks with minimal resource consumption (CPU time, memory, traffic).
- **Reliability** — the system's ability to operate without failure under specified conditions for a certain period of time.
- **Scalability** — the system's ability to handle increasing load by adding resources without changing the architecture.
- **Security** — a complex of measures to protect data from theft, distortion, or blocking of access.
- **Manageability** — the ease of monitoring, configuring, and updating the system during operation.
- **Performance** — a quantitative characteristic of how quickly the system performs operations and what volume of data it can process.

</details>

---

<details>
<summary><span>3. What types of <b>scaling</b> are there?</span></summary>
<br />

- **Vertical Scaling (Scale-up)** — increasing system performance by boosting the power of a single node (increasing RAM, CPU cores, or disk speed).

  > _Example:_ Buying a more powerful server for a database.

- **Horizontal Scaling (Scale-out)** — increasing performance by adding new nodes (servers) to the system that work in parallel.
  > _Example:_ Adding ten standard servers to a cluster to distribute web traffic.

Vertical scaling is easier to implement but has a physical "ceiling," while horizontal scaling is nearly limitless but requires a more complex software architecture.

</details>

---

<details>
<summary><span>4. What are <b>SLA / SLO / SLI?</b></span></summary>
<br />

- **SLI (Service Level Indicator)** — a specific quantitative metric that we measure here and now. It is the "thermometer" of the system.

  > _Example:_ Server latency or the percentage of successful requests (error rate).

- **SLO (Service Level Objective)** — a target value or range of values for a chosen SLI that we want to maintain. This is the internal goal of the engineering team.

  > _Example:_ "99.9% of requests must be processed faster than 200 ms."

- **SLA (Service Level Agreement)** — an external commitment (contract) to the client, outlining what happens if the SLO is not met. It is a legal document with financial consequences (fines, refunds).
  > _Example:_ "If service availability falls below 99%, we will return 10% of the subscription cost to clients."

**Important nuance:** Engineers usually try to make the **SLO slightly stricter than the SLA**. This creates an "Error Budget" to fix the system before financial penalties apply to clients.

</details>

---

<details>
<summary><span>5. What is <b>Stateless / Stateful</b>?</span></summary>
<br />

- **Stateless** — an architecture where the server does not store information about previous client requests. Every request must contain all the data necessary for its processing.

  > _Example:_ Google search. Each of your search queries is autonomous. If you close the tab and open it again, the server won't "remember" what you searched for a minute ago until you send a new request.

- **Stateful** — an architecture where the server "remembers" the context of interaction with the client. The state (session) is stored on the server side and affects the processing of subsequent requests.
  > _Example:_ An old online store with session-based carts. You add an item to the cart on one server, and that server stores the list of items in its memory. If the next request goes to a different server (without synchronization), the cart will appear empty.

---

**Brief Comparison:**

| Criterion             | Stateless                                           | Stateful                                                |
| --------------------- | --------------------------------------------------- | ------------------------------------------------------- |
| **Scalability**       | High (any server can handle any request)            | Complex (requires data synchronization between servers) |
| **Fault Tolerance**   | High (server failure doesn't lose client data)      | Lower (server failure results in loss of user session)  |
| **Data Transmission** | Heavier requests (must send tokens/data every time) | Lighter requests (server already knows who you are)     |

</details>

---

<details>
<summary><span>6. What are <b>Latency, Response Time, and Throughput?</b></span></summary>
<br />

- **Latency** — the time it takes for a data packet or request to travel from the sender to the receiver. This is the pure "delay in transit."

  > _Example:_ The time it takes for an electrical signal to travel from your PC to a game server.

- **Response Time** — the total time a user waits for a response after sending a request. It includes _Latency_ + the time the server spends processing the task.

  > _Example:_ You click "Buy," the request reaches the server (latency), the server checks the balance and deducts money (processing), and the response returns to you. All of this combined is the response time.

- **Throughput** — the number of requests or volume of data a system can process over a specific period.
  > _Example:_ A web server processing 5000 requests per second (RPS) or a communication channel with a speed of 100 Mbps.

---

**Simple Analogy:**
Think of a road.

- **Latency** — how fast a single car travels from City A to City B (speed).
- **Throughput** — how many cars can pass through this road in one hour (number of lanes).

These metrics are closely related: if **Throughput** reaches its limit, requests start queuing up, which immediately increases **Response Time**.

</details>

---

<details>
<summary><span>7. Load types: <b>Data-intensive vs. Compute-intensive?</b></span></summary>
<br />

- **Data-intensive** — systems where the primary challenge is the volume of data, its complexity, or the speed at which it changes, rather than computations.

  > _Example:_ Social networks (Facebook, Instagram) or databases where you need to quickly save and search through billions of posts.

- **Compute-intensive** — systems where CPU load is the primary concern. There may be little data, but the processing algorithms are very complex.
  > _Example:_ Video editing services, 3D graphics rendering, cryptocurrency mining, or training neural networks.

</details>

---

<details>
<summary><span>8. What is the <b>Read / Write Ratio?</b></span></summary>
<br />

- **Read / Write Ratio** — an indicator that determines which operation predominates in the system. This influences the choice of database architecture and caching strategy.
- **Read-heavy** — users read data much more often than they create new data.

  > _Example:_ A news portal or Wikipedia (one article is written once but read millions of times). **Caching** is critical here.

- **Write-heavy** — the system receives a massive stream of incoming data that must be recorded quickly.
  > _Example:_ Log collection systems, Internet of Things (IoT) sensors, or stock market quotes. **High DB write throughput** is essential here.

**Why is this important for an architect?**
If you understand that a system is **Read-heavy**, you will add **Read-replicas** for the database. If it is **Compute-intensive**, you will think about vertical CPU scaling or using GPUs.

</details>

---

<details>
<summary><span>9. What are the types of <b>backend architecture?</b></span></summary>
<br />

- **Monolith** — an architecture in which all application components (logic, DB interaction, interface) are bundled into a single executable file or project.

  > _Example:_ A small online store written in Django or Ruby on Rails, where all code lives in one repository and is deployed as a whole.

- **Microservices** — an approach where an application is broken down into a set of small, independent services, each responsible for its own business function and communicating with others over a network (API).
  > _Example:_ Netflix or Amazon. One service handles authorization, another recommendations, a third payment. If the recommendation service "goes down," users can still pay for their subscription.

**Important advice:** It is usually recommended to start with a **monolith** to quickly validate an idea (MVP) and move to **microservices** only when the team and load grow to the point where the monolith becomes "cramped."

</details>

---

<details>
<summary><span>10. Pros and cons of Monolithic and Microservice architecture</span></summary>
<br />

### **1. Monolithic Architecture**

Suitable for small teams, startups, and systems with low business logic complexity.

| Characteristic  | Pros (+)                                                                                   | Cons (−)                                                                                               |
| --------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------ |
| **Development** | **Simplicity:** single code base, shared data models, and easy project navigation.         | **Tangled:** over time, code turns into a "big ball of mud" that is hard to change.                    |
| **Testing**     | **Ease:** the entire application can be launched for end-to-end tests.                     | **Risk:** a small change in one module can unexpectedly break another part of the system.              |
| **Performance** | **Speed:** function calls within memory happen instantly, without delays.                  | **Growth Barrier:** you cannot scale just one heavy function — you must replicate the entire monolith. |
| **Deployment**  | **Convenience:** only one artifact (file or container) needs to be delivered and launched. | **Long Wait:** building and launching a huge project can take tens of minutes.                         |

---

### **2. Microservice Architecture**

Justified for large projects with hundreds of developers and a need for flexible scaling.

| Characteristic      | Pros (+)                                                                                            | Cons (−)                                                                                      |
| ------------------- | --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| **Scaling**         | **Granularity:** you can add power only to the payment or search service without touching the rest. | **Complexity:** requires complex infrastructure setup (Kubernetes, Service Mesh).             |
| **Fault Tolerance** | **Isolation:** if the recommendation service "falls," the catalog and cart continue to work.        | **Network Failures:** network calls can drop, hang, or arrive with delays.                    |
| **Tech Stack**      | **Flexibility:** different languages can be used (Go for speed, Python for ML) for specific tasks.  | **Tech Zoo:** hard to maintain unified quality and security standards across different teams. |
| **Teamwork**        | **Autonomy:** teams work independently without interfering or waiting for others' changes.          | **Consistency:** hard to keep data current across different DBs (integrity issue).            |

> _Example choice:_ If you are making an MVP for a food delivery app — choose a **monolith**. If you are building a giant like Uber or Amazon — you cannot do without **microservices**.

</details>

---

<details>
<summary><span>11. Where can <b>load balancing</b> occur?</span></summary>
<br />

- **Client-side balancing** — the client knows the server addresses and chooses which one to contact.

  > _Example:_ A client application receives a list of IP addresses from Service Discovery and decides where to send the request.

- **Server-side balancing** — an intermediary (Load Balancer) stands between the client and the servers, receiving all requests and distributing them.

  > _Example:_ Nginx or HAProxy standing in front of a server cluster.

- **DNS / GeoDNS balancing** — distribution at the level of domain name resolution. GeoDNS directs the user to the data center closest to them.
  > _Example:_ A request from Europe is directed to a server in Frankfurt, while one from Asia goes to Singapore.

</details>

---

<details>
<summary><span>12. What are the <b>load distribution algorithms?</b></span></summary>
<br />

- **Random** — choosing a random server. Simple, but can lead to uneven load.
- **Round Robin (RR)** — requests are passed to servers in turn (1st, 2nd, 3rd, and back to 1st).
- **Weighted Round Robin (WRR)** — the same, but considering the server's capacity (weight).

  > _Example:_ A powerful server receives 3 requests, while a weak one receives only 1.

- **Least Connections / Response Time / Bandwidth** — the request goes to the server with the fewest active connections, the fastest response, or the most free bandwidth.
- **Power of Two Choices** — two random servers are selected, and the request goes to the one that is less loaded. This is more efficient than pure Random.
- **Sticky Sessions** — pinning a specific user to a specific server (usually via Cookie).
  > _Example:_ Needed in **Stateful** architectures so that a user's cart isn't "lost" when moving to another server.

</details>

---

<details>
<summary><span>13. What are the <b>load balancing layers (OSI)?</b></span></summary>
<br />

- **L4 (Transport Layer)** — balancing based on IP and ports. Very fast, as it does not read the packet content.
- **L7 (Application Layer)** — balancing based on request content (URL, headers, Cookies). Allows for smart routing.
  > _Example:_ Sending `/api/video` requests to one set of servers and `/api/images` to another.

</details>

---

<details>
<summary><span>14. What are the <b>types of proxying?</b></span></summary>
<br />

- **Forward Proxy** — a server that stands between a group of clients and the internet. It hides the client's identity from the server and controls outgoing traffic.

  > _Example:_ A corporate proxy in an office that blocks employees from social media or hides their real IP addresses from external sites.

- **Reverse Proxy** — a server that stands in front of one or a group of web servers. It accepts requests from the internet and distributes them among internal servers. The client doesn't even know they aren't communicating directly with the target server.

  > _Example:_ **Nginx** or **HAProxy** standing at the "entry point" of a system. They handle load balancing, encryption (SSL termination), and static content caching.

---

**Key Difference:**

- **Forward Proxy** protects and anonymizes the client.

- **Reverse Proxy** protects and optimizes the server.

The **Reverse Proxy** is the "heart" of any modern architecture. It not only distributes load but can also act as an **API Gateway**.

</details>

---

<details>
<summary><span>12. What are the <b>load distribution algorithms?</b></span></summary>
<br />

- **Random** — selecting a random server. Simple, but can lead to uneven load.
- **Round Robin (RR)** — requests are passed to servers in turn (1st, 2nd, 3rd, and back to 1st).
- **Weighted Round Robin (WRR)** — the same, but considering the capacity (weight) of the server.

  > _Example:_ A powerful server receives 3 requests, while a weak one receives only 1.

- **Least Connections / Response Time / Bandwidth** — the request goes to the server with the fewest active connections, the fastest response, or the most free bandwidth.
- **Power of Two Choices** — two random servers are selected, and the request goes to the one that is less loaded. This is more efficient than pure Random.
- **Sticky Sessions** — pinning a specific user to a specific server (usually via Cookie).
  > _Example:_ Needed in **Stateful** architectures so that a user's cart isn't "lost" when moving to another server.

</details>

---

<details>
<summary><span>13. What are the <b>load balancing layers (OSI)?</b></span></summary>
<br />

- **L4 (Transport Layer)** — balancing based on IP and ports. Very fast, as it does not read the packet content.
- **L7 (Application Layer)** — balancing based on request content (URL, headers, Cookies). Allows for smart routing.
  > _Example:_ Sending `/api/video` requests to one set of servers and `/api/images` to another.

</details>

---

<details>
<summary><span>14. What are the <b>types of proxying?</b></span></summary>
<br />

- **Forward Proxy** — a server that stands between a group of clients and the internet. It hides the client's identity from the server and controls outgoing traffic.

  > _Example:_ A corporate proxy in an office that blocks employees from social media or hides their real IP addresses from external sites.

- **Reverse Proxy** — a server that stands in front of one or a group of web servers. It accepts requests from the internet and distributes them among internal servers. The client doesn't even know they aren't communicating directly with the target server.
  > _Example:_ **Nginx** or **HAProxy** standing at the "entry point" of a system. They handle load balancing, encryption (SSL termination), and static content caching.

---

**Key Difference:**

- **Forward Proxy** protects and anonymizes the **client**.
- **Reverse Proxy** protects and optimizes the **server**.

**Reverse Proxy** is the "heart" of any modern architecture. It not only distributes load but can also act as an **API Gateway**.

</details>

---

<details>
<summary><span>15. What is the purpose of <b>caching?</b></span></summary>
<br />

**Caching** is one of the most effective ways to speed up a system and reduce database load by temporarily storing frequently requested data in fast memory (RAM).

**Why it is needed:**

1. **Faster Response:** Data from memory is delivered dozens of times faster than from a disk-based DB.
2. **Reduced DB Load:** Repeated requests do not "hit" the heavy database.
3. **Resource Savings:** Decreases CPU consumption and network traffic for repeated calculations.

---

**Key Terms:**

- **Cache Hit** — a successful situation where the requested data was found in the cache and immediately returned to the client.
- **Cache Miss** — a situation where the data was not in the cache, and the system had to fetch it from the slow database.
- **Hit Ratio** — a metric of cache effectiveness. The ratio of "hits" to the total number of requests.

  > _Example:_ If 90 out of 100 requests were served from the cache, the Hit Ratio = 90%. The higher it is, the better the cache is tuned.

- **Cache Invalidation** — the process of removing or updating outdated data in the cache so that the user does not see obsolete information.

  > _Example:_ When a product price changes in the DB, the old price in the cache must be "invalidated," otherwise the client will see the incorrect cost.

- **Cache Warm-up** — pre-filling the cache with data (usually immediately after system startup) so that the first users do not experience slowness due to a _Cache Miss_.

  > _Example:_ A script that "clicks through" the most popular pages after deployment so they end up in the cache.

- **Hot Key** — a key (data) that is accessed by an abnormally large number of users simultaneously.
  > _Example:_ A celebrity post with millions of followers or a product page on Black Friday. Hot keys can overload even the caching server itself.

</details>

---

<details>
<summary><span>16. What data should be cached?</span></summary>
<br />

The choice of data for caching is usually based on the principle of **"frequently requested, rarely changed."**

- **Static files** — images, JS/CSS scripts, fonts. This is the simplest and most effective type of caching.

  > _Example:_ A company logo on the main page that hasn't changed in years.

- **Results of heavy DB queries** — data that takes a lot of time and server resources to retrieve.

  > _Example:_ A list of the top 100 popular products, compiled from several huge tables with aggregation.

- **User profile data (sessions)** — information about whether the user is authorized and what their permissions are.

  > _Example:_ Username and avatar, which are displayed on every page of the site.

- **Responses from external APIs** — if your system requests data from third-party services that work slowly or charge for each request.

  > _Example:_ Exchange rates from a central bank updated once a day, or a weather forecast.

- **Results of complex calculations** — data requiring high CPU costs.
  > _Example:_ A generated PDF report for the past month or the result of a recommendation algorithm.

---

**What NOT to cache:**

1. **Frequently changing data:** If data updates every second, the cache will be constantly invalidated and will provide no benefit.
2. **Personal/sensitive data of other users:** An error in caching logic could lead to one user seeing another's credit card data.
3. **Data with low reuse probability:** Caching rare requests ("Long Tail") only wastes expensive RAM.

It is important to remember the **Read / Write Ratio**: the more a system is oriented toward reading (Read-heavy), the more benefit caching will bring.

</details>

---

<details>
<summary><span>17. Is <b>error caching</b> necessary?</span></summary>
<br />

Error caching (also known as **Negative Caching**) is an advanced technique that helps protect the system from a "domino effect" during failures or attacks.

**Yes, it is necessary**, but with certain conditions. Caching responses about the absence of data or temporary failures prevents system overload.

**Why it is needed:**

- **Protection against "junk" requests:** If someone (or a bot) requests non-existent data a million times, the system will not query the DB every time but will immediately return an error from the cache.
- **Reducing load during failures:** If the database is temporarily unavailable, error caching allows the server not to waste time waiting for a timeout for every new request.

---

**What exactly to cache:**

- **404 Error (Not Found)** — if a resource does not exist, it's better to remember this for a short time.

  > _Example:_ A request for a user profile that has been deleted.

- **Authorization errors (401/403)** — helps protect against brute-force attacks (password cracking).
- **Empty search results** — if nothing is found for the query "pink elephant in a space suit," there is no point in searching for it again for the next 5 minutes.

---

**Main Rules (Best Practices):**

1. **Short TTL (Time To Live):** Errors should live in the cache much less than successful responses.

   > _Example:_ Cache a successful response for 1 hour, and a 404 error for 1-2 minutes.

2. **Separation of error types:** You shouldn't cache a 500 error (Internal Server Error) for long, as it might be fixed a second later.
3. **Security:** Ensure that the cached error does not contain sensitive information about the structure of your system or DB.

Error caching is an excellent way to increase system **Availability** under load.

</details>

---

<details>
<summary><span>18. Is caching always beneficial?</span></summary>
<br />

No, caching is not always a blessing. In some scenarios, it can be not only useless but also harmful to performance or data correctness.

Caching becomes harmful or ineffective in the following cases:

- **Low Hit Ratio (Rare requests)** — if data is requested again very rarely, the cache just takes up expensive RAM without bringing benefit.

  > _Example:_ A user database is huge, but people only log into their profiles once a year. Caching all profiles is a waste of resources.

- **Write-heavy load (Frequent updates)** — if data changes more often than it is read, the system will spend more resources on constant invalidation and updating the cache than on the reading itself.

  > _Example:_ Real-time stock quotes. The cache will become obsolete a millisecond after being written.

- **Critical importance of data freshness** — in financial or medical systems, even a delay of a couple of seconds can be unacceptable.

  > _Example:_ Bank account balance. A user should not see an old amount after they have just withdrawn money.

- **Resource limitations (RAM)** — the cache lives in RAM, which is much more expensive than disk space. If you cache everything, the system won't have enough memory to run core processes.
- **Complexity of logic (Consistency problem)** — keeping the cache up to date requires complex code. Errors in cache invalidation are one of the most common causes of bugs that are hard to reproduce.
  > _Example:_ A user changed their password, but the session cache on one of the servers didn't update, and the old password still works.

---

**When the cache turns into a problem:**

1. **Cache Stampede:** When a popular key's expiration time runs out, and thousands of requests simultaneously "rush" to the database to update it, creating a cascading load.
2. **Pollution:** When "one-time" data displaces truly useful and frequently used data from memory.

This is why, before implementing a cache, it is always worth evaluating the **Read/Write Ratio** and choosing the right **data eviction strategy** (e.g., **LRU** — Least Recently Used).

</details>

---

<details>
<summary><span>19. How to <b>calculate cache efficiency</b>?</span></summary>
<br />

The primary metric is **Average Access Time**.
$$T_{avg} = (HitRate \times T_{cache}) + (MissRate \times T_{db})$$
Where:

- **$Hit Rate$** — proportion of requests found in the cache (from 0 to 1).
- **$Miss Rate$** — proportion of requests not found in the cache (1 - HitRate).
- **$T\_{cache}$** — time to retrieve data from the cache.
- **$T\_{db}$** — time to retrieve data from the primary storage (DB).

---

### **When does the cache become harmful?**

There is a "rule of thumb": if the **Cache Miss Rate > 0.8** (meaning you don't find data in the cache more than 80% of the time), the cache is considered harmful.

**Why it is bad:**

1. **Double Latency:** On a miss, you spend $T*{cache}$ + $T*{db}$ time. If misses occur 80% of the time, the system works slower for most requests than if there were no cache at all.
2. **Useless resource consumption:** You spend expensive RAM and CPU maintaining a cache structure that isn't doing its job.
3. **Churn:** With such a high Miss Rate, data in the cache is constantly being updated, creating unnecessary write load on the cache itself.

> _Example:_
> Assume cache time is 1 ms and DB time is 100 ms.
> If **Miss Rate = 0.9** (90%), then $T\_{avg}$ = (0.1 $\times$ 1) + (0.9 $\times$ 101) $\approx$ 91 ms.
> The overhead of checking the cache in 90% of cases makes the system less efficient.

---

### **How to increase efficiency (Hit Ratio)?**

- **Increase TTL:** Store data longer (if business logic allows).
- **Increase memory volume:** So that popular data isn't evicted by new data.
- **Cache Warm-up:** Fill it with data before real users arrive.

</details>

---

<details>
<summary><span>20. What are the <b>types of caching?</b> Pros and cons?</span></summary>
<br />

### **1. Internal Caching (In-memory cache)**

Data is stored directly in the RAM of the application itself (e.g., in a HashMap or specialized libraries like Caffeine/Guava).

| Pros (+)                                                                                                      | Cons (−)                                                                                                                  |
| ------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| **Extreme speed:** data is read from the process memory; this is the fastest way.                             | **Scaling issues:** during horizontal scaling, each application instance will have its own "piece" of the cache.          |
| **No network latency:** no need to contact another server.                                                    | **Synchronization difficulties:** if data in the cache is updated on Server A, Server B won't know (consistency problem). |
| **No (un)marshalling costs:** data is stored as ready language objects; no need to turn them into JSON/bytes. | **Warm-up after failure:** if the application crashes, the cache is completely cleared and must be filled from scratch.   |

> _Example:_ Storing configuration files or country directories that rarely change.

---

### **2. External Caching (Distributed cache)**

The cache is moved to a separate system (in-memory database) accessed by all application instances.

> _Example:_ Redis, Memcached.

| Pros (+)                                                                                        | Cons (−)                                                                                                                      |
| ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| **Shared state:** all servers see the same up-to-date data.                                     | **Operational speed:** lower than internal caching due to added network latency.                                              |
| **Scalability:** terabytes of data can be stored simply by adding nodes to the cache cluster.   | **Data marshalling:** data must be serialized (e.g., to JSON or Protobuf) to be sent over the network, and deserialized back. |
| **Survivability:** if the application crashes and restarts, the data in the cache is preserved. | **Single point of failure:** if Redis itself goes down, all application servers are immediately "blinded."                    |

> _Example:_ Storing user sessions or shopping carts in an online store.

---

**Summary:**

- If data is small and static — use **internal** cache.
- If the system is distributed and there is a lot of data — choose **external**.

</details>

---

<details>
<summary><span>21. What are the <b>ways to interact with the cache</b>?</span></summary>
<br />

### **Read Strategies**

- **Cache Aside** — the application first goes to the cache; if the data is not there (miss), it reads from the DB and saves it to the cache itself.

  > _Example:_ The most popular approach. The application manages the entire process, while the DB and the cache are unaware of each other.

- **Read Through** — the application always requests data only from the cache, and the cache itself goes to the DB upon a miss, updates, and returns the response.
  > _Example:_ Allows for simplifying application code by offloading the reading logic to the cache infrastructure.

### **Write Strategies**

- **Write Through** — data is written simultaneously to both the cache and the DB; the write is considered successful only after confirmation from both.

  > _Example:_ Guarantees high data relevance in the cache but slows down the write due to the double operation.

- **Write Back (or Write Behind)** — the application writes data only to the cache, and it is saved to the DB asynchronously after some time.

  > _Example:_ Very fast writing, suitable for log collection systems or counters where the loss of a few seconds of data is not critical.

- **Write Around** — data is written directly to the DB, bypassing the cache. The cache is updated only during a subsequent read (via Cache Aside).
  > _Example:_ Helps avoid cluttering the cache with data that is written frequently but read rarely.

### **Additional Techniques**

- **Refresh-ahead (Cache Ahead)** — the cache automatically updates data before its life span (TTL) expires if it is frequently requested.
  > _Example:_ The system sees that the lifespan of a popular news item expires in 10 seconds and makes a request to the DB in advance so that the user does not encounter latency.

Each of these strategies is a choice between **speed** and the **risk of data loss** or inconsistency.

</details>

---

<details>
<summary><span>22. What are the <b>data eviction algorithms?</b></span></summary>
<br />
When the cache overflows, the system needs to decide which data to delete to make room for new data. These rules are called **Eviction Policies**.

### **Basic Algorithms**

- **Random** — deletes a random object. Simple to implement but does not consider the usefulness of the data.
- **FIFO (First In, First Out)** — deletes data that was added first (like in a queue), regardless of how often it was read.
- **LIFO (Last In, First Out)** — deletes data that was added last. Rarely used.

### **Access-based Algorithms**

- **LRU (Least Recently Used)** — deletes data that has **not been requested for the longest time**. The most popular algorithm (balance of simplicity and efficiency).
- **MRU (Most Recently Used)** — deletes data that was requested **most recently**. Useful when older data is more likely to be needed again.
- **LFU (Least Frequently Used)** — deletes data that was requested **least often** (counts the number of accesses).
  > _Downside:_ old popular objects can get "stuck" in the cache forever.

### **Advanced and Combined Algorithms**

- **LRU-k** — considers the time of the k-th last access. Allows for better differentiation between popular data and random "one-off" requests.
- **SLRU (Segmented LRU)** — the cache is divided into two zones: "probationary" (for new data) and "protected" (for frequently requested data).
- **2Q (Two Queues)** — uses two queues (FIFO and LRU) to effectively filter out data requested only once (protection against cache "scanning").
- **TLRU (Time-aware LRU)** — considers not only the time of the last access but also the data's lifespan (TTL).

### **Approximations and Specialized Algorithms**

- **Second Chance** — a modification of FIFO. If an element has an "access flag," it is given a second chance and moved to the end of the queue instead of being deleted.
- **Clock** — a more efficient implementation of Second Chance, where elements are arranged in a circle and a "hand" searches for a candidate for deletion.
- **Belady’s Algorithm (OPT)** — a theoretical ideal. Deletes data that will not be needed for the **longest time in the future**.
  > _Nuance:_ Impossible in practice since we don't know the future. Used as a benchmark for comparing other algorithms.

In modern systems (e.g., in **Redis**), **LRU** or its approximations are most commonly used as they provide the best result with minimal resource costs.

</details>

---

<details>
<summary><span>23. What are the <b>types of API?</b></span></summary>
<br />

### **1. REST (Representational State Transfer)**

The most popular style for web services. Built around **resources** (entities), access to which is carried out through standard HTTP methods (**CRUD**).

- **Methods:** `GET` (read), `POST` (create), `PUT/PATCH` (update), `DELETE` (delete).
- **Pros:** Simplicity, caching, independence of client and server. Usually uses JSON.

### **2. SOAP (Simple Object Access Protocol)**

A strict protocol based on XML. Often found in banking systems and old corporate software.

- **Features:** Has a rigid standard (WSDL file), built-in error handling, and security support (WS-Security).
- **Pros:** High reliability and data strictness. **Cons:** Redundancy (heavy XML) and complexity.

### **3. RPC (Remote Procedure Call)**

The concept of "calling a remote procedure." The client calls a function on the server as if it were in its own code.

- **gRPC (Google RPC)** — a modern implementation from Google. Uses **HTTP/2** and the **Protocol Buffers** format (binary code).
- **Pros:** Extremely high speed, bidirectional data streaming, strong typing.
- **Cons:** Not human-readable (requires deserialization), difficult to test via a browser.

### **4. GraphQL**

A query language for APIs created by Facebook. Allows the client to define exactly which fields it needs.

- **Features:** The client has a single entry point (`/graphql`) where it sends a request describing the data structure.
- **Pros:** Solves the problems of **Overfetching** (excess data) and **Underfetching** (lack of data requiring new requests).
- **Cons:** Complexity of server-side implementation and difficulties with caching.

---

**Brief Comparison:**

- Need a standard for frontend? — **REST**.
- Need speed between microservices? — **gRPC**.
- Complex data and mobile applications? — **GraphQL**.
- 15-year-old banking sector? — **SOAP**.

</details>

---

<details>
<summary><span>24. What are <b>Underfetching</b> and <b>Overfetching</b> and how are they related to GraphQL?</span></summary>
<br />

These terms describe the inefficiency of data transfer between client and server.

### **1. Overfetching**

This is a situation where the client receives **more data from the server than it needs** to render a specific screen.

- **Problem:** Wastes extra mobile traffic, consumes battery power to parse heavy JSON responses, and loads the network.
- **Example in REST:** To show only the _names_ of friends in a list, you call `/api/friends`. But the server returns the full object of each friend: date of birth, address, order history, and biography. 90% of this data is not needed right now.

### **2. Underfetching**

This is a situation where a single API request is **insufficient** to get all the necessary data for a screen.

- **Problem:** The client has to make several sequential (chained) requests, which increases wait time (**Latency**) due to constant network "trips."
- **Example in REST:** You need to show a user profile and their last 3 posts. First, you make a request `/user/1`, get the post IDs, and then make a second request `/user/1/posts`. Until the first one completes, you cannot start the second.

---

### **Internal Workings (How GraphQL Solves This)**

Unlike REST, where each URL is a fixed set of data, **GraphQL** works differently:

1. **Single Entry Point (Endpoint):** Usually one URL (e.g., `/graphql`).
2. **Schema:** All possible data types and the relationships between them are described on the server (strong typing).
3. **Query:** The client writes the request structure itself, listing only the required fields.
   > _Overfetching solution:_ If you only need `name`, you write `name` in the query, and the server will send only that.

> _Underfetching solution:_ You can request both profile data and a nested list of posts in a single query. The server will collect them and provide them in one response.

</details>

---

<details>
<summary><span>25. What is <b>Observability</b> and what does it consist of?</span></summary>
<br />

**Observability** is the ability to understand the internal state of a system by analyzing the data it outputs. It consists of "three pillars" and additional methods:

- **Monitoring & Metrics** — collecting numerical data about the system's operation in real-time. Helps answer: "Is the system healthy?".
- **Logging** — recording text events. Helps answer: "What exactly happened?".
- **Tracing** — tracking the path of a specific request through all microservices. Helps answer: "Where exactly did the delay occur?".
- **Continuous Profiling** — analysis of resource consumption (CPU, RAM) at the code line level in real-time.
- **Error Analysis** — automatic collection and grouping of exceptions.

## </details>

---

<details>
<summary><span>26. Key <b>Performance Metrics</b></span></summary>
<br />

### **1. Load and Capacity Metrics (Throughput)**

- **RPS (Requests Per Second)** — the number of incoming requests to the server per second.
- **TPS (Transactions Per Second)** — the number of successfully completed business operations (e.g., payments or registrations).
- **QPS (Queries Per Second)** — the number of database queries (usually higher than RPS since one request can generate several DB queries).

### **2. Time and Quality Metrics (Latency & Reliability)**

- **Response Time** — total request processing time. It is important to look at **percentiles**:
- **p50 (Median):** average time for a typical user.
- **p99:** time seen by the 1% of users with the slowest requests (critical for SLA).
- **Error Rate** — the proportion of responses with 4xx and 5xx codes. A sharp increase in this metric is the main signal of an emergency.

### **3. Resource Metrics (Utilization)**

- **Infrastructure:** CPU load, RAM (memory), Traffic (network channel), and Disk I/O (disk read/write).
- **Runtime:** number of active processes/threads and the intensity of the Garbage Collector (GC Pause).

### **4. Queue Status and Availability**

- **Queue Depth:** the number of requests waiting to be processed. Queue growth is a precursor to an increase in _Response Time_.
- **Uptime / Downtime:** system availability and downtime as a percentage (e.g., "four nines" — 99.99%).

</details>

---

<details>
<summary><span>27. <b>Observability</b> Tool Stack</span></summary>
<br />

For each task, industry standards (De Facto) have emerged:

| Direction      | Tools (Stack)                             | Description                                                                                       |
| -------------- | ----------------------------------------- | ------------------------------------------------------------------------------------------------- |
| **Monitoring** | **Prometheus** + Grafana                  | **Prometheus** — standard for metrics collection (pull model). Grafana — for graph visualization. |
| **Logging**    | **ELK** (Elasticsearch, Logstash, Kibana) | Logstash collects, Elasticsearch stores and searches, Kibana displays logs.                       |
| **Tracing**    | **Jaeger**, Zipkin                        | Allow viewing the "tree" of calls: how a request passed through 10 microservices.                 |
| **Profiling**  | **Pyroscope**, Parca                      | Show "Flame Graphs" — which functions in the code are consuming the most CPU right now.           |

</details>

---
