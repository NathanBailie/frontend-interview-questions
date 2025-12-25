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

---

<details>
<summary><span>28. <b>Database Types</b> and Their Purpose</span></summary>
<br />

| Database Type           | Popular Examples                  | Best Use Case                                                                                                                                 |
| ----------------------- | --------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| **Relational (SQL)**    | PostgreSQL, MySQL, Oracle         | Data with a strict structure where **transactions (ACID)** and complex relationships are important. Ideal for financial systems and accounts. |
| **Document**            | MongoDB, CouchDB                  | Storing data with a weak structure (JSON-like). Suitable for product catalogs, user profiles, and rapid development iteration.                |
| **Search Engines**      | Elasticsearch, Solr, Meilisearch  | Full-text search, complex filtering, autocomplete, and log analytics.                                                                         |
| **Key-Value (K-V)**     | Redis, Memcached, etcd, Tarantool | **Caching**, session storage, queues, or configurations. Work as fast as possible (often in RAM).                                             |
| **Columnar (OLAP)**     | ClickHouse, Cassandra, Vertica    | **Big data analytics**. They read only the necessary columns, which speeds up report generation across billions of rows.                      |
| **Graph**               | Neo4j, Memgraph                   | Data with a vast number of connections. Social networks (finding friends), recommendation systems, fraud detection.                           |
| **Time Series**         | InfluxDB, VictoriaMetrics         | Time-stamped data. System metrics, stock quotes, sensor data (IoT).                                                                           |
| **Blob Store (Object)** | Amazon S3, MinIO, Ceph            | Storing **unstructured files**: videos, photos, backups, website static assets.                                                               |

---

### **Quick Selection Cheat Sheet:**

1. **Need clear relationships and money guarantees?** — Use **Postgres**.
2. **Need to quickly search for text like "blue jacket"?** — Use **Elasticsearch**.
3. **Need to build a "sales over 5 years by region" report?** — Use **ClickHouse**.
4. **Need to quickly retrieve a user's cart by ID?** — Use **Redis**.
5. **Need to understand how many handshakes apart two people are?** — Use **Neo4j**.

</details>

---

<details>
<summary><span>29. <b>Search Engines</b> - are they a DB or an add-on?</span></summary>
<br />

### **1. Technically — it is a full-fledged database**

Search engines (e.g., **Elasticsearch**, **Solr**, **Meilisearch**) possess all the characteristics of a DBMS:

- **Storage:** They write data to disk in their specific format (inverted index).
- **Interface:** They have an API (usually REST) or their own query language for inserting, deleting, and searching data.
- **Scalability:** They support clustering, sharding (splitting data into parts), and replication (copies for reliability).

### **2. Architecturally — it is most often an "add-on"**

In most systems, a search engine is not the primary storage ("Source of Truth"). It is used as a **secondary store** alongside a relational DB (PostgreSQL/MySQL):

- **Why:** Relational DBs excel at transactions and relationships but are very slow and poor at text searching (especially considering typos, synonyms, or weights).
- **How it works:** Data is first written to the primary DB and then synchronized with the search engine.

---

### **Internal Structure: Inverted Index**

The main "magic" that makes a search engine what it is, is the way data is organized.

- **In a regular DB (Row-based):** Data is stored in rows. To find the word "Apple" in a description column, the database needs to scan all rows (or use a limited B-Tree index).
- **In a search engine (Inverted Index):** A table is created where the key is the **word** and the value is a **list of IDs of documents** where it occurs.
  > _Example:_
  > "Apple" -> [ID: 1, ID: 5, ID: 102]
  > "Smartphone" -> [ID: 5, ID: 20]
  > Search becomes instantaneous because the engine immediately knows where to look.

---

### **When to use as the only DB?**

Sometimes search engines are used without a primary DB. The most prominent example is the **ELK Stack (Elasticsearch, Logstash, Kibana)** for working with logs:

- Logs are written directly to Elasticsearch.
- They are stored, indexed, and analyzed there.
- Transactions or complex relationships are not important here, so Elasticsearch handles it on its own.

</details>

---

<details>
<summary><span>30. What does the <b>database choice</b> depend on?</span></summary>
<br />

### **1. Transactions (ACID vs BASE)**

- If data integrity is critical (e.g., money transfers), a DB with full **ACID** transaction support is necessary (usually relational DBs).
- If high availability and scalability are more important, NoSQL solutions operating under the **BASE** model can be considered.

### **2. Nature and Format of Data**

- **Data Format:** How structured is the data? For rigid schemas, SQL is suitable; for flexible (JSON-like) ones, document-oriented DBs.
- **Frequency of Format Changes:** If the data schema changes constantly (dynamic product attributes), it is better to choose a **Schemaless** solution (e.g., MongoDB) to avoid heavy table migrations during every code update.

### **3. Nature of Data Access (Workload)**

- Do we need many small writes and reads by key (OLTP)?
- Or will we be creating heavy analytical reports across billions of rows (OLAP)?
- This determines whether the database will be **row-based** (Postgres) or **columnar** (ClickHouse).

### **4. Expertise and Community**

- **Skill in working with the technology:** How familiar is the team with the tool? Even the fastest DB can become a bottleneck if no one knows how to properly configure and optimize indexes.
- **Community and Maturity of Technology:** How time-tested is the database? Does it have a developed community, ready-made driver libraries, and is it easy to find answers to emerging errors on Stack Overflow?

---

### **Summary for an Architect**

When choosing a DB, ask yourself three questions:

1. Is data loss or temporary inconsistency acceptable?
2. How often will the document structure change?
3. Do we have the resources (people and time) to support this specific technology?

</details>

---

<details>
<summary><span>31. What are the <b>classes of databases?</b></span></summary>
<br />

### **1. By Load Type (OLTP vs OLAP vs HTAP)**

- **OLTP (Online Transactional Processing):** Oriented toward a huge number of short transactions (reading/writing a single row).

  > _Example:_ PostgreSQL, MySQL. Used for real-time user interaction with an application.

- **OLAP (Online Analytical Processing):** Optimized for complex analytical queries over large data volumes (aggregations, reports).

  > _Example:_ ClickHouse, BigQuery. Store data in columns.

- **HTAP (Hybrid Transactional/Analytical Processing):** "Two in one." They allow analytical queries to be performed directly on transactional data without delays for copying.
  > _Example:_ TiDB, MemSQL.

---

### **2. By Deployment and Operation Method**

- **Embedded:** They run inside the application process itself and do not require a separate server.

  > _Example:_ SQLite, H2. Ideal for mobile apps or local caching.

- **Single File Database:** The entire database physically exists as a single file on the disk.

  > _Example:_ SQLite. Convenient for portability and simple applications.

- **Distributed:** Data is physically spread across many servers (nodes), providing scalability and fault tolerance.
  > _Example:_ Cassandra, CockroachDB.

---

### **3. By Storage Medium**

- **In-memory:** All data is stored in the Random Access Memory (RAM). This provides extreme speed, but data may be lost if the power is turned off (unless there is a disk snapshot mechanism).

  > _Example:_ Redis, Memcached, SAP HANA.

- **Persistent:** Data is stored on non-volatile media (HDD/SSD). The main priority is data safety during reboots.
  > _Example:_ Most classic DBs (Oracle, MSSQL).

---

### **Summary for Selection:**

| If you need...                        | Choose class...            |
| ------------------------------------- | -------------------------- |
| **Maximum RPS and low Latency**       | **In-memory**              |
| **Build a report on a billion sales** | **OLAP**                   |
| **Store data in a mobile app**        | **Embedded / Single file** |
| **Process orders in an online store** | **OLTP / Persistent**      |

</details>

---

<details>
<summary><span>32. <b>Indexes:</b> what are they, why are they needed, and what are their features?</span></summary>
<br />

### **What is it?**

An **index** is an auxiliary data structure (usually a tree or hash table) that stores the values of one or more table columns and links to the corresponding rows. Instead of going through a million records in order, the database refers to the index and finds the necessary result in a few steps.

---

### **Why are they needed?**

The main and only goal is to **speed up reading**. Without an index, the database is forced to perform a **Full Table Scan**, which takes a critically long time on large data volumes.

---

### **Key Features and the "Cost" of Use**

Indexes are not "free" speedups. They have three important features that must be considered when designing:

1. **Speed up reading:** They allow searching, filtering (`WHERE`), and sorting (`ORDER BY`) to be performed orders of magnitude faster.
2. **Slow down writing:** This is the main downside. With every `INSERT`, `UPDATE`, or `DELETE` operation, the database must not only modify the table itself but also **update all related indexes**. The more indexes on a table, the slower data is written to it.
3. **Use additional memory:** Indexes are separate objects that take up space on disk and (ideally) in RAM. In some cases, the size of all indexes can exceed the size of the data in the table itself.

---

### **When to use (Best Practices):**

- Create indexes for columns that are frequently involved in search conditions (`WHERE`).
- Index columns that are frequently used for joining tables (`JOIN`).
- Avoid creating indexes for columns with very low selectivity (e.g., gender "male/female"), as it will be easier for the database to read the whole table.
- Delete unused indexes so as not to slow down writing for nothing.

</details>

---

<details>
<summary><span>33. What are the <b>types of indexes?</b></span></summary>
<br />

### **1. B-Tree (Balanced Tree)**

The most universal and default index type in most DBs.

- **How it works:** Data is stored as a balanced tree where nodes contain values and leaves contain links to rows.
- **What for:** Comparison operations (`=`, `>`, `<`, `>=`) and range searches (`BETWEEN`).
- **Feature:** Supports data sorting.

---

### **2. Hash Index**

- **How it works:** Applies a hash function to a column value and maps it to a row address.
- **What for:** Only for exact match searches (`=`, `IN`).
- **Pros:** Works faster than B-Tree when searching for a specific value.
- **Cons:** Cannot search ranges and does not support sorting.

---

### **3. Bitmap Index**

- **How it works:** Creates a bitmask (0 and 1) for each unique value in a column.
- **What for:** Columns with low selectivity (where there are few unique values: gender, order status, region).
- **Pros:** Takes up very little space and allows for instant combining of conditions via logical `AND`/`OR`.

---

### **4. GIST and GIN (Specialized)**

- **GIN (Generalized Inverted Index):** "Inverted index". Ideal for searching inside composite objects (arrays, JSONB, full-text search).
- **GiST (Generalized Search Tree):** Used for indexing geometric data (coordinates) and "nearest neighbor" searches.

---

### **5. Other Types (by application logic)**

- **Clustered Index:** Determines the physical order of row storage in a table. A table can have only one such index (usually the Primary Key).
- **Covering Index:** An index that contains all the fields requested in the `SELECT`. The database doesn't need to refer to the table itself; it takes everything from the index.
- **Composite Index:** An index on several columns at once. Order is important: a `(A, B)` index will help when searching for `A` or `A+B`, but will be useless when searching only for `B`.
- **Partial Index:** An index not on the whole table, but based on a condition.
  > _Example:_ Index only active orders `WHERE status = 'active'`. This saves memory.

**Cheat Sheet:**

- Need to search by number or date? — **B-Tree**.
- Need to search by coordinates on a map? — **GiST**.
- Need to search tags in JSON? — **GIN**.
- Need to quickly find by exact ID? — **Hash**.

</details>

---

<details>
<summary><span>34. What are <b>transactions?</b></span></summary>
<br />

**A transaction** is a logical unit of database work representing a sequence of operations (read, write) that is performed as a single whole.

### **Main principle: "All or nothing"**

If even one operation within a transaction fails, all previous changes are canceled (**rollback**), and the database returns to its original state. If everything succeeds, the changes are permanently recorded (**commit**).

---

### **Why is this needed?**

Transactions solve two main problems:

1. **Fault tolerance:** They guarantee that in the event of a failure (e.g., a bank transfer), money doesn't get "stuck" in mid-air.
2. **Concurrency:** They allow thousands of users to simultaneously change the same data without the risk of corrupting it.

</details>

---

<details>
<summary><span>35. <b>ACID</b> Properties</span></summary>
<br />

### **1. Atomicity — ("All or nothing")**

A transaction is an indivisible unit.

- If there are 10 steps in a transaction and 9 succeed but the 10th fails — **all 10 are canceled**.
- The system will never commit a "halfway" result.
- Implementation tool: **Undo Log**.

### **2. Consistency**

A transaction transitions the database from one valid state to another.

- All rules (Constraints), such as unique keys, Foreign Keys, and Checks, must be respected.
- If a transaction violates database logic (e.g., inserting a row without a required field), the database will reject it.

### **3. Isolation**

Parallel transactions must not affect each other.

- If two users change the same balance at the same time, the result should be as if they did it strictly one after another.
- Isolation is regulated by **isolation levels** (from the weakest to the strictest — Serializable).
- Implementation tool: **Locks** and **MVCC** (Multi-Version Concurrency Control).

### **4. Durability**

Once a user receives a `COMMIT` confirmation, the data is written "forever."

- Even if the server loses power or the OS crashes immediately after clicking "Pay," the data will be there after a reboot.
- Implementation tool: **Redo Log** or **WAL** (Write-Ahead Logging).

---

### **Cheat sheet for memorization:**

- **A** — Don't do half the job.
- **C** — Don't break database rules.
- **I** — Don't peek at others.
- **D** — Don't lose what you saved.

</details>

---

<details>
<summary><span>36. What are <b>Constraints</b> and why are <b>Deferrable Transactions</b> needed?</span></summary>
<br />

### **1. Constraints**

These are rules that prevent incorrect data from being written to the database. They directly provide the **Consistency** property in ACID.

- **NOT NULL:** prohibits empty values.
- **UNIQUE:** guarantees the uniqueness of values in a column.
- **PRIMARY KEY:** a unique identifier for a row (Unique + Not Null).
- **FOREIGN KEY:** verifies that a link points to an existing record in another table.
- **CHECK:** verifies a condition (e.g., `age > 18` or `price > 0`).

---

### **2. Deferrable Constraints**

Usually, a database checks constraints **immediately** after each line of code is executed. But in complex transactions, this can cause an error.

**The problem:** You need to swap values in a column with a unique index. During the replacement, a duplicate will momentarily exist, and the database will throw an error, preventing the transaction from completing.

**The solution: Deferrable Transactions**
You can mark a constraint as `DEFERRABLE`. This allows moving rule checks from the command execution time to the very **end of the transaction** (before `COMMIT`).

### **Check modes:**

- **Immediate:** check after each command (standard behavior).
- **Deferred:** check all rules only at the moment of transaction commitment. If data still violates the rules at the end of the transaction, a rollback occurs.

---

### **Why combine them?**

Using **deferred constraints** inside transactions is critical for:

1. **Circular dependencies:** when Table A references B, and B references A. You cannot insert data into either without temporarily disabling checks.
2. **Bulk updates:** when data is temporarily inconsistent in the middle of a process but returns to normal by the end of the transaction.

</details>

---

<details>
<summary><span>37. What <b>transaction anomalies</b> exist?</span></summary>
<br />

### **1. Lost Update**

Occurs when two transactions simultaneously read the same value, modify it, and write it back. As a result, the second transaction simply "overwrites" the changes of the first.

- **Example:** Balance is $100. User A wants to add $50, User B wants to add $20. Both read "100". User A writes "150", and User B follows by writing "120". The $50 from User A is simply lost.

### **2. Dirty Read**

A transaction reads data that has been modified by another transaction that has not yet been **committed**.

- **Example:** User A transfers money and updated the balance (but hasn't confirmed yet). User B reads this "new" balance. User A cancels the transaction (Rollback). Now User B has data that officially never existed in the database.

### **3. Non-repeatable Read**

Inside a single transaction, you read **the same row** twice, but between the reads, another transaction manages to **modify or delete** it.

- **Example:** You read the price of an item ($100). While you were thinking, another transaction changed it to $200. You read the same row again, and the price is different. The data "drifted" right while you were working.

### **4. Phantom Read**

Inside a single transaction, you perform a range query (e.g., "all orders for today"), and meanwhile, another transaction performs an **INSERT** of a new row that fits your condition.

- **Example:** You counted the number of orders (there were 10). While you were generating the report, someone added another order. You recount, and there are now 11. A "phantom" appeared that wasn't there at the start.

---

### **Summary Table of Anomalies:**

| Anomaly            | Core Problem                       | Object Affected     |
| ------------------ | ---------------------------------- | ------------------- |
| **Lost Update**    | Writing over someone else's record | Row (record)        |
| **Dirty Read**     | Reading uncommitted data           | Row (state)         |
| **Non-repeatable** | Value change between reads         | The same exact row  |
| **Phantom Read**   | New rows appearing in the result   | Set of rows (range) |

</details>

---

<details>
<summary><span>38. Transaction <b>Isolation Levels</b></span></summary>
<br />

### **1. Read Uncommitted**

The weakest level. Transactions can see changes that have not yet been committed (`commit`) by other transactions.

- **Allows anomalies:** Dirty Read, Non-repeatable Read, Phantom Read.
- **Pros:** Maximum speed.
- **Application:** Where accuracy is not critical (e.g., an approximate like counter).

### **2. Read Committed**

The default level in many DBs (e.g., PostgreSQL). A transaction only sees data that was committed before the read began.

- **Protects against:** Dirty Read.
- **Allows anomalies:** Non-repeatable Read, Phantom Read.
- **How it works:** Each `SELECT` query within a transaction sees a fresh "snapshot" of committed data.

### **3. Repeatable Read**

Guarantees that if you read a row, it will be exactly the same upon re-reading.

- **Protects against:** Dirty Read, Non-repeatable Read.
- **Allows anomalies:** Phantom Read (in some DBs, like MySQL/InnoDB, this level also protects against phantoms).
- **How it works:** The transaction sees a "snapshot" of the data at the moment it **started**.

### **4. Serializable**

The strictest level. Transactions are executed as if they were occurring strictly one after another.

- **Protects against:** All anomalies (including Phantom Read).
- **Cons:** Lowest performance. Locking errors (Deadlocks) or serialization errors requiring transaction retry often occur.

---

### **Mapping Summary Table:**

| Isolation Level      | Dirty Read    | Non-repeatable Read | Phantom Read  |
| -------------------- | ------------- | ------------------- | ------------- |
| **Read Uncommitted** | Allowed       | Allowed             | Allowed       |
| **Read Committed**   | **Protected** | Allowed             | Allowed       |
| **Repeatable Read**  | **Protected** | **Protected**       | Allowed       |
| **Serializable**     | **Protected** | **Protected**       | **Protected** |

In practice, most developers stick with **Read Committed**, as it is the sweet spot between speed and integrity.

</details>

---

<details>
<summary><span>39. DB Mechanisms: <b>2PL, MVCC, and WAL</b></span></summary>
<br />

### **1. 2PL (Two-Phase Locking)**

This is the classic way to ensure **Isolation** through locks.

- **Essence:** A transaction cannot simply change data. It must first acquire a "lock" on the row.
- **Two phases:**

1. **Expanding Phase:** The transaction only acquires locks and does not release them.
2. **Shrinking Phase:** The transaction begins to release locks (usually at the very end) and can no longer take new ones.

- **Minus:** Readers wait for writers, and writers wait for readers. This significantly slows down the system.

---

### **2. MVCC (Multi-Version Concurrency Control)**

A modern and faster approach to isolation (used in Postgres, MySQL InnoDB).

- **Essence:** Instead of locking a row, the database creates a **new version** of it.
- **Main plus:** Readers never block writers, and writers never block readers.
- **How it works:** When transaction "A" changes a row, it creates a copy. Transaction "B," which is reading data at the same time, sees the old version of the row (a "snapshot") until transaction "A" performs a `commit`.

---

### **3. WAL (Write-Ahead Logging)**

A mechanism for ensuring **Durability**.

- **Problem:** Writing data directly to table files is slow (need to find disk space, update indexes). If the server crashes during the process, data will be corrupted.
- **Solution:** First, all changes are written sequentially to a simple text log file (WAL) (this is very fast).
- **Result:** Even if the database "crashes" before it manages to update the main tables, upon rebooting, it simply reads the WAL and "replays" all confirmed transactions.

---

### **How do they work together?**

1. **MVCC** allows us to read and write simultaneously without slowdowns.
2. **2PL** (or elements of it) is used where it's necessary to guaranteed avoidance of conflicts when writing to a single row.
3. **WAL** guarantees that even in the event of a severe crash, the results of MVCC and 2PL work will not be lost.

</details>

---

<details>
<summary><span>40. What is <b>BASE</b> (for NoSQL DBs)?</span></summary>
<br />

**BASE** is a database design model that is the opposite of strict **ACID**. It is used in distributed NoSQL systems where ensuring availability and speed over huge volumes of data is more important than instantaneous accuracy.

### **Acronym Breakdown:**

- **Basically Available:**
  The system guarantees a response to any request, but it might be unsuccessful or contain stale data. The main thing is that the database continues to work even if part of the nodes is unavailable.
- **Soft-state:**
  The state of the data can change over time on its own (without new requests) due to background synchronization between servers.
- **Eventually Consistent:**
  Data on different servers may differ right now, but the system guarantees that over time they will synchronize and become identical (if writing stops).

---

### **Comparison: ACID vs BASE**

| Characteristic  | ACID (SQL)                       | BASE (NoSQL)                    |
| --------------- | -------------------------------- | ------------------------------- |
| **Priority**    | Integrity and accuracy.          | Speed and scalability.          |
| **Consistency** | Immediate (Strong Consistency).  | Delayed (Eventual Consistency). |
| **Complexity**  | Hard to scale across many nodes. | Easy to scale horizontally.     |
| **Example**     | Bank transfer, warehouse.        | Social media feed, likes, logs. |

---

### **Why is this needed?**

In giant systems (Amazon, Facebook), it is impossible to force thousands of servers to agree on the value of every record instantly — it would "hang" the internet. Therefore, they choose **BASE**: a user might see an old comment or an incorrect number of likes for a fraction of a second, but the site will work lightning-fast.

</details>

---

<details>
<summary><span>41. Database Objects: <b>Procedures, Triggers, View, Watch API</b></span></summary>
<br />

### **1. Stored Procedures**

These are code fragments (functions) that are stored and executed directly inside the database.

- **Why:** To avoid moving large volumes of data back and forth to the application. Logic is executed as close to the data as possible.
- **Pros:** Reduction in network traffic and the ability to centrally change logic for all applications at once.

### **2. Triggers**

Special procedures that are **automatically** launched when a specific event occurs in a table.

- **Events:** `INSERT`, `UPDATE`, `DELETE`.
- **Example:** When a user is deleted, a trigger automatically records this information in a log table or deletes all their associated orders.

### **3. Materialized Views**

Unlike a regular View (which is just a saved query), a materialized view **physically saves the result** of the query to disk.

- **Why:** For heavy analytical reports. Instead of calculating the sum across a million rows every time, the database saves the result once and provides it instantly.
- **Minus:** Data in the "materialization" becomes stale. It needs to be periodically updated (`REFRESH`).

### **4. Watch API (Change Data Capture)**

A mechanism (typical for K-V stores like **etcd** or **Redis**, as well as modern SQL DBs) that allows an application to "subscribe" to changes in a key or table.

- **How it works:** The application opens a connection, and as soon as data changes, the database itself sends a notification (push).
- **Example:** In a configuration system (etcd), a microservice "waits" for setting changes and applies them instantly without a reboot.

---

### **Application Summary Table:**

| Object                | When to use?                                                         |
| --------------------- | -------------------------------------------------------------------- |
| **Procedure**         | Need to perform a complex calculation inside the DB.                 |
| **Trigger**           | Need to automatically maintain integrity or logging.                 |
| **Materialized View** | Need to instantly open a report that takes a long time to calculate. |
| **Watch API**         | Need to know immediately that data has changed (reactivity).         |

</details>

---

<details>
<summary><span>42. <b>Message Brokers:</b> why are they needed?</span></summary>
<br />

Message Brokers are intermediate software that allows different services to communicate with each other, even if they are written in different languages or operate at different speeds.

### **Main tasks and advantages**

- **Buffering (Smoothing):**
  The broker acts as a "buffer." If a sudden flood of requests hits the system, the broker saves them in a queue, allowing processing services to pick up tasks gradually without crashing from overload.
- **Asynchronous Communication:**
  The sender does not need to wait for the recipient to process the message. It just "fires" the data into the broker and moves on. This is critical for interface responsiveness.
- **Decoupling:**
  Services know nothing about each other; they only know about the broker. This allows for changing, updating, or scaling one service without breaking the work of the others.
- **Scalability:**
  It is easy to add more "consumers" (workers) who will process the queue from the broker in parallel.
- **Fault Tolerance:**
  If the recipient service "crashes," the messages won't disappear. They will sit in the broker until the service comes back up and picks them up.
- **Understanding Data Flows:**
  Brokers allow for building complex processing chains (Data Pipelines), where data passes through several stages of transformation and analysis.

---

### **Real-life example:**

Imagine placing an order in an online store.

1. You clicked "Buy."
2. The main service quickly saved the order and replied "Ok" to you.
3. It threw a message into the broker.
4. And from the broker, other services pick up the task **asynchronously**: one sends an email, another deducts the item from the warehouse, a third prepares the receipt.

</details>

---

<details>
<summary><span>43. How <b>Kafka</b> and <b>RabbitMQ</b> are built: main differences</span></summary>
<br />

While both tools work with messages, they do it differently: RabbitMQ is a classic "smart" queue, while Kafka is a distributed "log" of events.

### **1. Apache Kafka Architecture**

Kafka works on the principle of a distributed transaction log. Messages are not deleted immediately after reading but are stored for a set time.

- **Producer:** Sends data into the system.
- **Consumer:** Retrieves data. Consumers themselves track where they left off in the log.
- **Broker:** A single node (server) of a Kafka cluster.
- **Topic:** A logical queue or category into which messages are grouped.
- **Partition:** A physical part of a queue. A topic is divided into parts for parallel processing and scalability.

---

### **2. RabbitMQ Architecture**

RabbitMQ is a broker that handles all the message routing logic.

- **Producer:** Sends a message to the **Exchange**.
- **Exchange:** The "brain" of the system. It receives messages and, based on rules (routing keys), decides which queue to direct them to.
- **Queue:** Storage where messages lie until the moment of reading.
- **Consumer:** Receives messages from the queue (often via a **Push** model, where the broker "pushes" data to the consumer).

---

### **3. Key Differences**

| Characteristic    | RabbitMQ                                                                        | Apache Kafka                                                               |
| ----------------- | ------------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| **Working Model** | **Smart broker / Dumb consumer**. Broker tracks message state.                  | **Dumb broker / Smart consumer**. Reader manages its own pointer (offset). |
| **Data Storage**  | Messages are deleted immediately after processing confirmation by the consumer. | Messages are stored in logs for a long time (even after reading).          |
| **Priority**      | Complex routing and guaranteed delivery.                                        | Huge throughput and real-time data stream processing.                      |
| **Re-reading**    | Impossible (message is gone).                                                   | Possible (can "rewind" time and re-read the log).                          |

### **What to choose?**

- **RabbitMQ:** If complex routing logic is needed (e.g., different services need different parts of the data) or if instantaneous processing of individual tasks is important.
- **Kafka:** If you need to process millions of events per second, build analytics on the fly, or have the ability to re-read data history.

</details>

---

<details>
<summary><span>44. <b>Push</b> and <b>Pull</b> models in brokers</span></summary>
<br />

**Push** and **Pull** models determine who initiates the data transfer: the broker, which "pushes" the message to the service, or the service, which "comes" to get the data itself.

### **1. Push Model (Initiator — Broker)**

The broker itself sends messages to Consumers as soon as they appear in the queue.

- **How it works:** The consumer establishes a connection, and the broker "pushes" data into it as it arrives.
- **Pros:** Minimal latency — data is delivered instantly.
- **Cons:** Risk of overloading the consumer (flooding with data) if it cannot keep up with the broker's pace. A flow control mechanism (Backpressure) is required.
- **Example:** **RabbitMQ** uses the Push model (though it supports Pull as well).

---

### **2. Pull Model (Initiator — Consumer)**

The consumer itself requests (polls) the broker for new messages.

- **How it works:** The consumer sends a request: "Give me the next 100 messages." If there is no data, it can wait or come back later.
- **Pros:** The consumer itself controls the processing speed and will never be overloaded. Easy to implement batching.
- **Cons:** Latency may occur if the consumer polls the broker too infrequently.
- **Example:** **Kafka** works on the Pull model.

---

### **Short comparison for Kafka and RabbitMQ:**

| Broker       | Model    | Logic                                                                            |
| ------------ | -------- | -------------------------------------------------------------------------------- |
| **RabbitMQ** | **Push** | The broker "cares" for the consumer and sends it tasks itself.                   |
| **Kafka**    | **Pull** | The consumer is "smart": it decides when and how much data to take from the log. |

</details>

---

<details>
<summary><span>45. Reliability in Brokers: <b>Data Retention</b> and <b>Delivery Guarantees</b></span></summary>
<br />

### **1. Data Retention**

This is the policy determining how long messages remain in the broker.

- **In RabbitMQ:** By default, a message is deleted immediately after the consumer sends an acknowledgment (`Ack`) of successful processing.
- **In Kafka:** Messages are stored for a set amount of time (e.g., 7 days) or until a disk volume limit is reached. This allows for re-reading data.

---

### **2. Delivery Guarantees (Delivery Semantics)**

When we send a message through a broker, there are three main scenarios for how it reaches the recipient:

- **At most once:**
  The message is sent once. If a network or service failure occurs, it is lost.

  > _Result:_ Either 0 or 1 delivery. No duplicates, but losses are possible.

- **At least once:**
  The most common mode. The sender will keep sending the message until it receives an acknowledgment. If the acknowledgment is lost, the message will come again.

  > _Result:_ 1 or more deliveries. Data is not lost, but **duplicates are possible**, which the system must be able to handle.

- **Exactly once:**
  The most difficult and expensive level to implement. The system guarantees that the message will be processed by the consumer exactly once, despite failures.
  > _Result:_ Strictly 1 delivery. This requires complex coordination (transactions) between the broker and the application.

---

### **Summary for selection:**

| Guarantee         | Data Loss | Duplicates | Application                                              |
| ----------------- | --------- | ---------- | -------------------------------------------------------- |
| **At most once**  | Possible  | Excluded   | Log collection, metrics (where 1% loss is not critical). |
| **At least once** | Excluded  | Possible   | Payment, orders (processing must be idempotent).         |
| **Exactly once**  | Excluded  | Excluded   | Critical financial real-time calculations.               |

</details>

---

<details>
<summary><span>46. Alternative storage methods: <b>Client-side</b> and <b>CDN</b></span></summary>
<br />

### **1. Client-side Storage**

Instead of requesting everything from the server, some data can be stored directly in the user's browser.

- **Cookies:** Small amounts of data (up to 4 KB). Usually used to store session IDs and authorization tokens.
- **Local Storage:** Allows storing up to 5-10 MB of data without an expiration date. Data persists even after the browser is closed. Suitable for theme settings, drafts, or a shopping cart.
- **Session Storage:** Similar to Local Storage, but data is erased when the tab is closed.
- **IndexedDB:** A full-featured built-in NoSQL database in the browser for storing large amounts of structured data and files.

**Why is this needed:**

1. **Offline mode:** The application can work without the internet.
2. **Speed:** Instant access to data without network delays.
3. **Economy:** Reduction in the number of requests to your API.

---

### **2. CDN (Content Delivery Network)**

**CDN** is a geographically distributed network of servers designed for fast delivery of "heavy" static content.

- **What is stored:** Images, videos, style files (CSS), scripts (JS), fonts.
- **How it works:** When a user requests a file, the CDN provides it from the server closest to them (Edge Server). If you are in Moscow, the file will come from a Moscow data center, not from the USA.
- **Caching:** The CDN caches content. You don't need to serve the same image a million times — the CDN will do it for you.

**Why is this needed:**

1. **Faster loading:** The physical distance the data travels is reduced (ping is lowered).
2. **Load reduction:** The main server (Origin) only handles business logic, not serving images.
3. **Fault tolerance:** If one CDN server goes down, traffic is picked up by another nearby node.

---

### **Comparison of methods:**

| Method          | Where do we store?           | What do we store?           | Main goal                  |
| --------------- | ---------------------------- | --------------------------- | -------------------------- |
| **Client-side** | User's browser               | Tokens, settings, API cache | UX and offline work        |
| **CDN**         | Network of servers worldwide | Images, video, statics      | Loading speed for everyone |
| **Database**    | Your server / Cloud          | Business data, users        | Integrity and search       |

</details>

---

<details>
<summary><span>47. What <b>delivery guarantees</b> exist for messages?</span></summary>
<br />

In distributed systems and message brokers, three main levels of guarantees are identified:

### **1. At most once**

This is the simplest and highest-performing model, but the least reliable.

- **Essence:** A message is sent once and not resent in case of an error.
- **Result:** The message is either delivered once or **lost**.
- **Application:** Collection of metrics or logs, where the loss of a single message is not critical for the system.

### **2. At least once**

The most popular model in modern architectures.

- **Essence:** The sender waits for an acknowledgment (ACK) from the recipient. If the acknowledgment does not arrive due to a failure, the message is sent **again**.
- **Result:** The message will be delivered at least once, but **duplicates are possible**.
- **Application:** Financial transactions, orders. Requires _idempotency_ on the recipient side (so that repeat processing of the same order does not lead to double charging).

### **3. Exactly once**

The most difficult to implement and "expensive" model in terms of resources.

- **Essence:** The system guarantees that the message will be delivered and processed **strictly once**.
- **Result:** Both losses and duplicates are excluded.
- **Application:** Critically important systems where duplication is unacceptable and idempotency is hard to implement at the code level.

</details>

---

<details>
<summary><span>48. <b>Replication</b> vs <b>Backup</b></span></summary>
<br />

### **1. Replication**

This is the process of copying data from one server (Master) to another (Slave/Replica) in real-time or with minimal delay.

- **Why it's needed:**
- **High Availability:** If the main server crashes, the system quickly switches to a replica, and users won't notice the failure.
- **Read Scaling:** Heavy `SELECT` queries can be moved to replicas, offloading the main server.
- **Main Downside:** If you accidentally execute a `DROP TABLE` or a `DELETE` without a filter on the master, this error is **instantly applied to all replicas**. Replication copies all changes, including harmful ones.

---

### **2. Backup**

This is a "snapshot" of the database state at a specific point in time (e.g., yesterday at 02:00), stored separately.

- **Why it's needed:**
- **Recovery from Human Error:** If data was accidentally deleted or corrupted by code, a backup is the only way to go back in time.
- **Protection against Ransomware:** Backups allow for system recovery after a cyberattack.
- **Audit and History:** You can see what the data looked like a month ago.
- **Main Downside:** Restoring from a backup takes time (from minutes to hours), during which the system may be unavailable.

---

### **Difference: Summary Table**

| Feature              | Replication                    | Backup                              |
| -------------------- | ------------------------------ | ----------------------------------- |
| **Goal**             | Availability (uptime).         | Preservation (data safety).         |
| **Timeliness**       | Data "right now."              | Data at the moment of the snapshot. |
| **Error Protection** | No (error copies immediately). | Yes (you can roll back).            |
| **Load**             | Constant on network and disk.  | One-time (during archive creation). |

### **Why need a backup if there is replication?**

Replication saves you from **hardware failure** (a burnt-out disk), but it is helpless against **logical errors**. If a programmer runs a buggy script that zeros out all user balances, replication will obediently zero them out on all servers. A backup is your only "chance of survival," allowing you to restore data to the moment before that script was run.

> **Golden Rule:** Replication is for business; Backup is for life. You need to have both.

</details>

---

<details>
<summary><span>49. Roles in Replication: <b>Master-Slave, Master-Master, Leaderless</b></span></summary>
<br />

### **1. Master-Slave (Single Leader)**

The most popular scheme. There is one main node (Master) that accepts writes, and several subordinate nodes (Slaves/Replicas) that only serve data for reading.

- **Advantages:**
- Simplicity: No write conflicts since there is only one "owner."
- Easy read scaling (just add more replicas).
- **Disadvantages:**
- Difficulty when the master fails: A new one must be chosen (Election), during which time writing is impossible.
- Replication lag: Data on the slave may be slightly older than on the master.
- **When to use:** Most web applications (social networks, blogs) where reads significantly outnumber writes.
- **Examples:** PostgreSQL, MySQL (standard configuration).

---

### **2. Master-Master (Multi-Leader)**

In the system, there are several equal nodes, each of which can accept both writes and reads. Changes are synchronized between them.

- **Advantages:**
- High availability: If one master fails, writing continues on another.
- Proximity to the user: You can place one master in Europe and another in the US to reduce latency.
- **Disadvantages:**
- **Write Conflicts:** Two users may simultaneously change the same row on different masters. A complex conflict resolution strategy is required.
- Complexity in configuration and integrity maintenance.
- **When to use:** Geographically distributed systems where write availability is critical.
- **Examples:** Oracle GoldenGate, complex MySQL clusters.

---

### **3. Leaderless (Master-less)**

The "no leader" concept. The client sends a write request to several nodes (or a coordinator) simultaneously, and the request is considered successful if a majority (quorum) confirms it.

- **Advantages:**
- Maximum fault tolerance: The system continues to work even if a significant portion of the nodes fails.
- No single point of failure.
- **Disadvantages:**
- Reading might return stale data (you need to read from multiple nodes to check for the latest version).
- Very complex logic for ensuring consistency.
- **When to use:** Systems with enormous loads where work cannot be interrupted for even a second.
- **Examples:** Cassandra, DynamoDB, Riak.

---

### **Summary Table:**

| Type              | Writing              | Conflicts        | Complexity |
| ----------------- | -------------------- | ---------------- | ---------- |
| **Master-Slave**  | Only to 1 node       | None             | Low        |
| **Master-Master** | To any leader        | **High**         | High       |
| **Leaderless**    | To all nodes at once | Version handling | Very High  |

</details>

---

<details>
<summary><span>50. Fault Tolerance: <b>Failover, Hot Standby, Split Brain</b></span></summary>
<br />

### **1. Failover**

This is the automatic (or manual) process of moving the load from the main server to a standby server when a failure is detected.

- **How it works:** The monitoring system realizes the Master has stopped responding. It selects the most up-to-date replica (Slave) and promotes it to the new Master. All application traffic is redirected to this new address.
- **Goal:** Minimize downtime.

---

### **2. Hot Standby**

This is a standby server mode where it is kept in a "warm" state.

- **Essence:** The standby server doesn't just store a copy of the data; it constantly receives a stream of changes from the main server and applies them immediately.
- **Features:**
- The database on Standby is running.
- It is ready to take over the load almost instantly (seconds).
- Often, only read-only queries are allowed on Hot Standby.
- **Other types:** _Warm Standby_ (database is running but not immediately ready) and _Cold Standby_ (database is turned off, requires time to start).

---

### **3. Split Brain**

This is a dangerous situation in a cluster where, due to a network failure, nodes lose connection with each other, and **two masters appear simultaneously** in the system.

- **The Problem:** Each part of the cluster "thinks" the other part has failed and elects its own master. Users start writing data to both servers.
- **Consequences:** Data on the nodes starts to diverge. Merging them later without loss is practically impossible.
- **Mitigation:**
- **Quorum:** Decisions are made by a majority vote (requires at least 3 nodes).
- **STONITH (Shoot The Other Node In The Head):** A drastic mechanism where one node physically cuts the power to another via a managed power outlet to eliminate competition.

---

### **Summary:**

| Term            | Role                                                     |
| --------------- | -------------------------------------------------------- |
| **Failover**    | The process of saving the system when the leader fails.  |
| **Hot Standby** | The ideal candidate for replacement, always ready.       |
| **Split Brain** | An admin's nightmare—two leaders and a mess in the data. |

</details>

---

<details>
<summary><span>51. <b>Replication Conflicts</b> and Quorum Formulas (W, R, N)</span></summary>
<br />

In distributed systems where writing can happen in parallel on different nodes (Master-Master or Leaderless), data conflicts are inevitable. Special algorithms and mathematical models are used to solve them.

### **1. Conflict Resolution Methods**

When two nodes receive different values for the same key, the database must decide which one to keep:

- **LWW (Last Write Wins):** The system compares timestamps and keeps the record made later. This is the simplest but dangerous method, as clock desynchronization between servers can lead to losing important data.
- **Replica Priority:** Each node is assigned a priority. In a conflict, data from the node with the higher rank is chosen.
- **Client-side Resolution:** The database saves all versions of conflicting data and gives them to the application during reading. The developer writes the logic for how to merge them (e.g., Amazon’s shopping cart).
- **CRDT (Conflict-free Replicated Data Types):** Special data structures designed so that when merging from any nodes, they always automatically reach the same result without conflicts.

---

### **2. Which data types are not prone to conflicts?**

These are **CRDTs**. They allow data to be updated independently and simultaneously on different nodes.

- **Counters:** E.g., number of likes. It doesn't matter in what order you add "+1"; the final sum will be the same.
- **Sets:** Adding unique elements.
- **Registers:** Store values with metadata for automatic merging.

---

### **3. Quorum Formula ()**

To ensure consistency in leaderless systems, quorum parameters are used:

- **N** — Total number of nodes storing a copy of the data.
- **W** — Number of nodes that must confirm a **write** for it to be successful.
- **R** — Number of nodes to poll during a **read**.

**Main Scenarios:**

1. **$W + R > N$:** **Strict consistency** is guaranteed. The write and read sets overlap on at least one node, so you always read the latest data.
2. **$W + R \leq N$:** Strict consistency is **not guaranteed**. A "dirty read" of old data is possible.
3. **$R = 1, W = N$:** Optimized for **fast reading** (read from any node), but writing will be slow and fragile (requires all nodes).
4. **$W = 1, R = N$:** Optimized for **fast writing**, but reading requires polling the entire network.

</details>

---

<details>
<summary><span>52. Replication Types: <b>Sync, Async, Semisync, Loss-less</b></span></summary>
<br />

### **1. Strong Consistency (Synchronous Replication)**

The master writes the data and waits for confirmation from the replica before responding "Success" to the user.

- **Pros:** Guarantees strong consistency. If the master fails, the replica is guaranteed to have all the data.
- **Cons:** Lowest speed. If a replica lags or the network goes down, writes on the master will stall.
- **When to use:** In mission-critical financial systems.

---

### **2. Eventual Consistency (Asynchronous Replication)**

The master writes the data locally, responds to the user immediately, and then sends the data to replicas in the background.

- **Replication Lag:** The time it takes for changes to reach the replica. If you read data from a replica immediately after a write, you might see an old value.
- **Pros:** Maximum write speed. The master does not depend on the state of the replicas.
- **Cons:** Risk of data loss. If the master crashes before it manages to send the log to the replica, that data is lost forever.
- **When to use:** Social networks, analytics, most web projects.

---

### **3. Semisynchronous Replication (Semisync)**

A compromise option. The master waits for confirmation from at least **one** replica that it has received the data (written it to its Relay Log) but does not wait for the actual write to the database to complete.

- **Essence:** We are certain that the data has left the master and physically exists somewhere else in the network.
- **Pros:** Faster than full synchronization but much more reliable than asynchronous.

---

### **4. Loss-less Semi-sync**

An improved version of semisynchronous replication.

- **In regular Semisync:** First, a `Commit` occurs on the master, then it waits for the replica. If the replica doesn't respond and the master fails, other users might have seen data that eventually disappears.
- **In Loss-less:** The master first waits for confirmation from the replica and **only then** performs the `Commit` locally.
- **Result:** It eliminates the situation where data is visible on the master but missing on replicas after a failure.

---

### **Summary Table:**

| Type             | Speed  | Data Reliability | Consistency |
| ---------------- | ------ | ---------------- | ----------- |
| **Synchronous**  | Low    | Maximum          | Strong      |
| **Asynchronous** | High   | Low              | Eventual    |
| **Semisync**     | Medium | High             | Compromise  |
| **Loss-less**    | Medium | Very High        | Enhanced    |

</details>

---

<details>
<summary><span>53. Subtle Consistency Errors (Replication Anomalies)</span></summary>
<br />

When data is transferred from a master to followers with a delay (replication lag), users may encounter logical paradoxes. Here are three classic examples and ways to solve them:

### **1. Read-Your-Writes Consistency**

**Problem:** A user submits data (e.g., a comment), the page refreshes, but the user doesn't see it because the read request went to a follower where the data hasn't "arrived" yet. This looks like data loss.

**Solution:** \* Track the user's last update time.

- If the update was recent (e.g., within the last minute), direct read requests to the **Master node**.

### **2. Monotonic Reads**

**Problem:** A user reads data and sees it, but upon refreshing the page, it disappears.

- This happens when the first request hits an "up-to-date" follower, and the second hits one that lags further behind the master. It creates the impression that time in the system has moved backward.

**Solution:** Bind the user to a specific follower (e.g., by ID or session hash) so they always read from the same node.

### **3. Consistent Prefix Reads**

**Problem (Twitter Example):** Violation of causality.

- User A posts a photo of a dog.
- User B replies with a compliment.
- Due to delays in different partitions or nodes, a third user might see User B's reply first ("What a cute dog!") but not see User A's photo yet. As a result, the reply makes no sense.

**Solution:** Ensure that any causally related data is written to and read from the same partition or in strict chronological order.

---

### **Anomaly Summary Table:**

| Anomaly               | Essence of the Problem                    | How to fix?                      |
| --------------------- | ----------------------------------------- | -------------------------------- |
| **Read-Your-Writes**  | "I just wrote this, but I don't see it."  | Read "own" data from the Master. |
| **Monotonic Reads**   | "It was just there, now it's gone."       | Sticky Sessions (node binding).  |
| **Consistent Prefix** | "There's an answer, but no question yet." | Maintain causal consistency.     |

</details>

---

<details>
<summary><span>54. Replication Technologies: <b>Formats, Methods, and Logic</b></span></summary>
<br />

### **1. Source and Transfer Model**

There are two main approaches to how a replica learns about changes:

- **Push Model (e.g., PostgreSQL):** The master "pushes" changes toward replicas as soon as they occur. This minimizes lag.
- **Pull Model (e.g., MySQL):** The replica periodically polls the master: "Do you have new records in the binary log?". If yes, it retrieves them.

---

### **2. Binary Log Formats (Binlog Formats)**

Depending on what exactly is recorded in the log and transmitted over the network, three types are distinguished:

| Format                    | Essence (What is transmitted)                                                                      | Pros                                                         | Cons                                                                                                                                                        |
| ------------------------- | -------------------------------------------------------------------------------------------------- | ------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Statement-based (SBR)** | The **SQL query** itself is transmitted (e.g., `UPDATE users SET status='active' WHERE age > 18`). | Very compact, creates little data in logs.                   | Problems with **non-deterministic functions** (`NOW()`, `RAND()`). They will return different values on the master and replica, leading to data divergence. |
| **Row-based (RBR)**       | Specific **changed rows** are transmitted (value was "A", became "B").                             | The most reliable method. Guarantees **100% data identity**. | If one query updates a million rows, a million records go into the log. This creates **huge load on the network and disk**.                                 |
| **Mixed-based**           | **Automatic mode**: the database chooses between SBR and RBR.                                      | Optimal balance of performance and reliability.              | The database uses _Statement_ but switches to _Row_ if it sees a dangerous function (like `UUID()`).                                                        |

---

### **3. Physical vs Logical Replication**

| Type         | How it works                                | Features                                                                                                                   |
| ------------ | ------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| **Physical** | Copies data byte-by-byte (disk blocks).     | Very fast. Cannot replicate between different DB versions or just a single table.                                          |
| **Logical**  | Transmits a stream of object (row) changes. | Flexible. Allows data transfer between different DB versions (e.g., from Pg 12 to Pg 15) or changing structure on the fly. |

---

### **4. Replication Filtering**

Sometimes we don't need to copy the entire database (e.g., analytics needs only orders, and logs are unnecessary).

- **Master-side:** You can specify which databases or tables should NOT go into the binary log.
- **Replica-side:** The replica downloads everything but applies only the changes that match the filter (e.g., `replicate-do-table`).

> **Why do this:** Save disk space on replicas and create specialized nodes (separately for warehouse, separately for users).

</details>

---

<details>
<summary><span>55. CAP Theorem: <b>Consistency, Availability, Partition Tolerance</b></span></summary>
<br />

The CAP theorem is a fundamental principle of distributed systems which states that at any given time, a database can only provide two out of three properties.

### **The Three Pillars of CAP**

1. **Consistency:**
   After a successful write to any node, a read from any other node will return that same updated data. All users see the same version of the data at the same time.
2. **Availability:**
   Every request to a working node in the system receives a successful response (without error), even if some nodes in the cluster have failed.
3. **Partition Tolerance:**
   The system continues to operate even if communication between nodes is lost (network partition). **In distributed systems, this property is mandatory.**

---

### **The Choice: Why not all three?**

Since failures are inevitable in real networks, **P (Partition Tolerance)** must always be present. Thus, the choice boils down to two options when a network failure occurs:

- **CP (Consistency + Partition Tolerance):**
  If connection between nodes is lost, the system **refuses to respond** to requests to avoid serving stale data. We sacrifice availability for accuracy.
- _Examples:_ **MongoDB, Redis, etcd.**
- **AP (Availability + Partition Tolerance):**
  If connection is lost, nodes continue to respond to users with whatever they have. Data on nodes may diverge. We sacrifice accuracy so that the system "stays alive."
- _Examples:_ **Cassandra, CouchDB, DynamoDB.**

> **Important Note (CA):** **CA** systems are only possible in an ideal environment where the network never fails (e.g., a database on a single server). In distributed systems, **CA does not exist**.

---

### **Strategy Comparison**

| Type   | What is more important? | What happens during network failure? | Typical Application                        |
| ------ | ----------------------- | ------------------------------------ | ------------------------------------------ |
| **CP** | Accuracy                | Error (Timeout)                      | Bank transactions, configs.                |
| **AP** | Operation               | Serves stale data                    | Social networks, counters, shopping carts. |

</details>

---

<details>
<summary><span>56. <b>Partitioning</b>: Vertical and Horizontal</span></summary>
<br />

Partitioning is a database optimization method where one large table is physically split into several smaller parts (partitions), yet logically remains a single entity for the user and application.

### **Why is partitioning needed?**

1. **Performance Boost:** Searching in a small subset of data (e.g., only for the current month) is much faster than searching through a whole table covering 10 years.
2. **Simplified Maintenance:** You can quickly delete old data by simply dropping one partition (`DROP PARTITION`) instead of a heavy `DELETE`.
3. **Effective Disk Management:** Different parts of a table can be stored on different disks (e.g., fresh data on fast SSDs, and archives on slow HDDs).

---

### **Types of Partitioning**

#### **1. Vertical Partitioning**

This is splitting a table by **columns**.

- **Essence:** Columns of a table are distributed across different physical storages. Often, the table is split into "frequently used" data and "rarely used" data (e.g., huge `blob` or `text` fields).
- **Example:** In a `Users` table, we move `id` and `email` to one table, and `biography` and `avatar_blob` to another.
- **When to use:** When a table has too many columns, but in 90% of cases, you only query two or three of them.

#### **2. Horizontal Partitioning**

This is splitting a table by **rows**.

- **Essence:** All columns remain the same, but rows are distributed across different parts based on a specific rule (partitioning key).
- **Example:** An `Orders` table is divided into partitions by year: `orders_2023`, `orders_2024`, `orders_2025`.
- **When to use:** When a table contains millions/billions of rows and searching it becomes too slow.

---

### **Approach Comparison**

| Feature               | Vertical                          | Horizontal                              |
| --------------------- | --------------------------------- | --------------------------------------- |
| **What do we split?** | Columns (object properties).      | Rows (object instances).                |
| **Result**            | Tables with different field sets. | Tables with the same field sets.        |
| **Goal**              | Reduce row width (I/O).           | Reduce the number of rows in the index. |

</details>

---

<details>
<summary><span>57. <b>Sharding</b>: Scaling Stateful Services</span></summary>
<br />

### **What is Sharding and why is it needed?**

**Sharding** is a database architecture strategy where data is broken into parts (shards) and distributed across **different physical servers** (nodes).

- **Scaling Stateful Services:** Unlike Stateless services (which you can spawn indefinitely), databases store state. Sharding is the primary way to **horizontally scale** such systems.
- **Why:** To distribute CPU, RAM, and disk load across several machines, overcoming the limits of a single powerful server (Vertical Scaling).

---

### **Sharding Methods**

#### **1. Range-based**

Data is distributed across shards based on a range of values of a specific key (e.g., ID or date).

- **Example:** Shard #1 stores users with IDs from 1 to 100,000, Shard #2 — from 100,001 to 200,000.
- **Pros:** Easy to implement, convenient for range queries.
- **Cons:** Risk of "hotspots". If all new users are active, the load will hit only the last shard.

#### **2. Key-based / Hash-based**

A hash function is applied to the sharding key, and the result determines the server number.

- **Example:** `hash(user_id) % number_of_shards`.
- **Pros:** Even distribution of data and load across all servers.
- **Cons:** Difficult to add new servers. Changing the total number of shards (N) causes the hash function to point to different servers, requiring a full data rebalance (solved via _Consistent Hashing_).

#### **3. Directory-based**

There is a separate service or lookup table that indicates which key resides on which shard.

- **Example:** A request goes to a "Directory Service," which says: "User Ivan's data is on Server B."
- **Pros:** Maximum flexibility. You can move data between shards manually without changing the algorithm.
- **Cons:** The directory service becomes a single point of failure and a performance bottleneck.

---

### **Method Comparison**

| Method         | Uniformity      | Range Queries            | Scaling Complexity     |
| -------------- | --------------- | ------------------------ | ---------------------- |
| **Range**      | Poor (Hotspots) | Excellent                | Medium                 |
| **Key (Hash)** | Excellent       | Poor                     | High (without hashing) |
| **Directory**  | Configurable    | Implementation dependent | Low (flexible)         |

</details>

---

<details>
<summary><span>58. Routing in Sharded Systems: <b>Client, Proxy, Coordinator</b></span></summary>
<br />

There are three main architectural approaches to where the decision on choosing the correct shard is made.

### **1. Client-side Routing**

The sharding logic resides directly within the client library or the application.

- **How it works:** The application knows the total number of shards and the algorithm (e.g., hash function). It calculates which server to go to and establishes a direct connection.
- **Pros:** No extra network hops, minimal latency.
- **Cons:** Difficulty in updating. If you add a new server, you must update configs or code in all copies of your application.
- **Example:** Client libraries for **Redis** or **Kafka**.

---

### **2. Proxy-based Routing**

An intermediate layer (Load Balancer / Proxy) stands between the application and the database to handle all logic.

- **How it works:** The application sends a request to a single proxy server address. The proxy analyzes the request (e.g., user ID) and redirects it to the appropriate shard.
- **Pros:** The application knows nothing about the cluster structure. It's easy to add/remove servers by changing settings only in the proxy.
- **Cons:** The proxy is an extra link that introduces slight latency and can become a bottleneck or a single point of failure.
- **Example:** **Vitess** (for MySQL), **PgBouncer** (with routing logic).

---

### **3. Broker / Coordinator**

A request hits any random node in the cluster, and that node decides what to do next.

- **How it works:** Every node in the cluster knows the topology of the entire system. If you sent a request to the wrong server, the coordinator node will forward the request to the correct neighbor or tell the client where to go.
- **Pros:** Convenience for the client (can connect to any IP). High fault tolerance.
- **Cons:** Internal traffic between cluster nodes can heavily load the network.
- **Example:** **Cassandra**, **Elasticsearch**, **ClickHouse**.

---

### **Routing Method Comparison**

| Feature                 | Client-side         | Proxy-based           | Coordinator              |
| ----------------------- | ------------------- | --------------------- | ------------------------ |
| **Where is the logic?** | In application code | In a separate service | Inside the DB itself     |
| **Client Complexity**   | High                | Low (simple SQL)      | Medium                   |
| **Extra Network Hop**   | No                  | Yes                   | Yes (sometimes internal) |
| **Flexibility**         | Low                 | High                  | High                     |

</details>

---

<details>
<summary><span>59. <b>Rebalancing</b> and the <b>Virtual Buckets</b> Concept</span></summary>
<br />

Rebalancing is the process of redistributing data between nodes in a sharded cluster. It is necessary when new servers are added to the system or when existing nodes become full.

### **1. The Problem with Simple Rebalancing**

If you use simple hashing (e.g., `hash(key) % N`, where N is the number of servers), then adding even one new server changes the modulo result for almost all keys.

- **Result:** You would have to move almost **all** data from one server to another. This creates a huge network load and can take the database down for a long time.

---

### **2. The Solution: Virtual Buckets (Sections)**

To avoid mass data movement, modern databases (e.g., Redis Cluster, Couchbase, Cassandra) use an abstraction layer — **virtual buckets**.

**How it works:**

1. **Fixed Number of Buckets:** Instead of binding a key directly to a server, the system divides the entire address space into a fixed (and large) number of logical bins — buckets (e.g., exactly 16,384 buckets).
2. **Key -> Bucket Mapping:** Every key is strictly bound to its bucket via a hash function: `hash(key) % 16384`. This link never changes.
3. **Bucket -> Server Mapping:** Servers own sets of these buckets. For example:

- Server A: buckets 0–5000
- Server B: buckets 5001–10000
- Server C: buckets 10001–16383

---

### **3. Rebalancing Process with Buckets**

When you add a new **Server D**:

- The system simply takes a portion of buckets from servers A, B, and C and transfers them to server D.
- Only the data belonging to those specific buckets is moved.
- The remaining 75% of data stays in place and does not participate in the move.

---

### **Advantages of Virtual Buckets:**

- **Minimal Data Movement:** Exactly as much data as the new node should store is transferred.
- **Management Simplicity:** It is easier for the database to operate with large logical blocks (buckets) than with billions of individual keys.
- **Flexibility:** You can assign more buckets to a powerful server and fewer to a weak one.

| Feature           | Regular Hash (`% N`)       | Virtual Buckets                              |
| ----------------- | -------------------------- | -------------------------------------------- |
| **Adding a Node** | Must move almost all data. | Only a small portion of data is moved.       |
| **Complexity**    | Low.                       | Requires a routing table (bucket -> server). |
| **Uniformity**    | Good.                      | Excellent (can balance with weights).        |

</details>

---

<details>
<summary><span>60. Resharding, Consistent Hashing, and Rendezvous Hashing</span></summary>
<br />

### **1. Resharding**

**Resharding** is the process of changing the sharding architecture: changing the sharding key, splitting one overloaded shard into two, or global data redistribution.

#### **Difference from Rebalancing:**

- **Rebalancing:** This is a "cosmetic" process. We just move existing data blocks (buckets) between nodes without changing the logic of how data is assigned to those blocks.
- **Resharding:** This is "major surgery." We change the structure itself. For example, if we had `Range-based` by year and decided to switch to `Hash-based` by `user_id`. This requires a complete overhaul of all data in the cluster.

#### **Resharding Problems:**

1. **Performance Hit:** Moving terabytes of data saturates the network and loads disks, slowing down core user requests.
2. **Consistency:** It's hard to ensure write availability while data is "migrating" from one server to another.
3. **Rollback Complexity:** If something goes wrong during resharding, returning everything to its original state is extremely difficult.

---

### **2. Consistent Hashing**

An algorithm that minimizes the volume of moved data when the number of nodes changes.

- **Principle:** All possible hash values are represented as a ring (from 0 to ). Both servers and data are mapped onto this ring. An object belongs to the server that appears first when moving clockwise.
- **Problem — Cascading Failure:** If one node fails, its entire load immediately transfers to the **single** next node on the ring. That node might not withstand the double load and fails too, triggering a chain reaction.
- **Solution — Virtual Shards (Vnodes):** Each physical server is represented on the ring by hundreds of "virtual" points. Now, if a server fails, its data (and load) is distributed **evenly across all** other nodes in the cluster, rather than falling on a single neighbor.

---

### **3. Rendezvous Hashing (Highest Random Weight)**

An alternative to consistent hashing used in systems like _Google Maglev_.

- **Principle:** For every key and every server, a weight is calculated: `weight = hash(key + server_id)`. The key is sent to the server that yielded the **maximum** weight.
- **Pros over Consistent Hashing:**

1. **No Ring Needed:** No need to store and update a complex "ring" structure and virtual nodes.
2. **Ideal Distribution:** When adding or removing a server, only the necessary minimum of data (`1/N`) is moved, and the load is distributed perfectly evenly immediately.
3. **Easy Weight Management:** If one server is more powerful than another, you can simply multiply its hash result by a coefficient.

---

### **Algorithm Comparison:**

| Feature               | Consistent Hashing                   | Rendezvous Hashing                       |
| --------------------- | ------------------------------------ | ---------------------------------------- |
| **Structure**         | Hash ring                            | Weight comparison (HRW)                  |
| **Search Complexity** | (binary search on ring)              | (must check every server)                |
| **On Node Failure**   | Load goes to neighbor (needs vnodes) | Load is split among everyone immediately |
| **Application**       | Cassandra, Memcached, Akamai         | Load balancers (Maglev), caching         |

</details>

---

<details>
<summary><span>61. <b>CDC (Change Data Capture)</b>: Kafka Connect and Libslave</span></summary>
<br />

These technologies work together to solve the problem: "How to immediately know that something in the database has changed and pass it to other systems?".

### **1. CDC (Change Data Capture)**

This is a concept (approach). Instead of periodically polling the database with a query like `SELECT * FROM table WHERE updated_at > ...` (which is heavy and slow), CDC listens to the **change logs** of the database itself (Binlog in MySQL or WAL in Postgres).

- **Why:** To update caches, search indexes (Elasticsearch), or stream data into an analytical warehouse in real-time.

---

### **2. Libslave**

This is a low-level library (often used in the MySQL ecosystem).

- **Essence:** It acts as a "fake replica" (slave). It connects to the master, presents itself as a regular Slave server, and starts receiving the Binlog event stream.
- **Role:** It is the "probe" that extracts raw data from the database's binary log. It parses the records (e.g., Row-based format) and turns them into understandable software events (Insert/Update/Delete).

---

### **3. Kafka Cluster and CDC**

**Apache Kafka** acts as the "transport backbone" and storage for these changes.

- **How it works together:**

1. **Connector (based on Libslave or Debezium):** Reads the DB Binlog.
2. **Producer:** Sends each change as a separate message to a Kafka topic.
3. **Kafka Cluster:** Reliably stores these messages.
4. **Consumers:** Any other services subscribe to the topic and immediately learn that a row in the database has been updated.

---

### **Role Summary Table:**

| Component         | Role in the Process                 | Analogy                          |
| ----------------- | ----------------------------------- | -------------------------------- |
| **Database**      | Primary data source.                | Newspaper author.                |
| **Libslave**      | Library for reading DB logs.        | Reader who rewrites the article. |
| **CDC (Process)** | Change tracking technology.         | News delivery system.            |
| **Kafka Cluster** | Data bus for delivering these news. | Newsstand/Post office.           |

---

### **Why is this cool?**

- **Minimal Master Load:** Reading the log is much lighter than executing heavy SQL queries.
- **Real-time:** The delay between writing to the DB and data appearing in Kafka is usually milliseconds.
- **Decoupling:** The database doesn't need to know who consumes its data. It just writes logs, and Kafka distributes them to whoever wants them.

</details>

---

<details>
<summary><span>62. Deployment Strategies: <b>Rolling, Blue/Green, Canary</b></span></summary>
<br />

These terms describe Deployment Strategies — methods of updating an application that minimize or completely eliminate system downtime and the risk of failure for all users at once.

### **1. Rolling Release (Incremental Update)**

The most common method in Kubernetes. A new version of the application is installed on servers one by one.

- **How it works:** The system shuts down one node (or group) of the old version (**V1**), replaces it with the new version (**V2**), and moves to the next one only after the new node successfully passes a health check.
- **Pros:** Does not require doubling server resources.
- **Cons:** During the update process, both old and new versions run in the cluster simultaneously (data compatibility issue).
- **Risk:** If there is a critical bug in **V2**, it will affect some users before the deployment is stopped.

---

### **2. Blue/Green Release (Blue-Green Deployment)**

A method that provides instantaneous switching between versions.

- **How it works:** Two identical environments run in parallel. **Blue** is the current (production) version, **Green** is the new version. When **Green** is fully ready and tested, the traffic load balancer redirects all users from Blue to Green with a single click.
- **Pros:** Zero downtime. Instant rollback — if a bug is found in Green, simply switch traffic back to Blue.
- **Cons:** Expensive, as it requires **twice the capacity** (servers) to maintain two copies of the system.

---

### **3. Canary Release (Canary Deployment)**

The name comes from the practice of miners taking a canary with them: if it stopped singing, it meant there was gas in the mine.

- **How it works:** The new version is rolled out to a very small group of users (e.g., 5%). We monitor errors and metrics for this group. If everything is fine, the percentage is gradually increased to 100%.
- **Pros:** The safest method. If there is a bug in the code, only a small part of the audience is affected. New features can be tested on real traffic.
- **Cons:** Complex configuration of traffic routing and monitoring.
- **Example:** Facebook first rolls out a feature to employees, then to New Zealand, and only then to the rest of the world.

---

### **Summary Comparison Table**

| Characteristic     | Rolling             | Blue/Green        | Canary      |
| ------------------ | ------------------- | ----------------- | ----------- |
| **Downtime**       | Zero                | Zero              | Zero        |
| **Resource Cost**  | Low (100% + buffer) | **High (200%)**   | Low         |
| **Rollback Speed** | Medium              | **Instantaneous** | Fast        |
| **Safety**         | Medium              | High              | **Maximum** |

</details>

---

<details>
<summary><span>63. Where to store static files and architectural diagrams (MVP and beyond)</span></summary>
<br />

### **1. Where to store static files? (From simple to complex)**

| Method                                           | Essence                                                                                                                          | When to use                                                                                                                                    |
| ------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| **Locally in the repository (Asset Pipeline):**  | Files are located directly in the project code folder.                                                                           | Only for critical CSS/JS and icons. Bad for user images, as files will be lost or duplicated during each deployment or scaling (new instance). |
| **Dedicated server storage (Local Disk / NAS):** | A separate folder on the disk served by Nginx.                                                                                   | **MVP** or small internal projects. Cheap, but difficult to scale across multiple servers.                                                     |
| **Object Storage (S3-like):**                    | Services like AWS S3, Google Cloud Storage, or MinIO. Files are stored as objects with unique URLs rather than in a file system. | **Standard for modern systems**. Unlimited volume, high reliability, easy to integrate.                                                        |
| **CDNs (Content Delivery Network):**             | A network of servers around the world (Cloudflare, Akamai) that caches your static files as close to the user as possible.       | When the project expands beyond one country or there is a lot of static content.                                                               |

---

### **2. Architectural Diagrams**

#### **A. MVP (Minimum Viable Product)**

Usually, this is a **two-tier** architecture or a simplified three-tier one.

1. **Client:** Browser or mobile application.
2. **Monolith (App + DB):** A single server where the code and database run, and static files are stored on the same disk.

- _Pros:_ Maximum development speed, zero infrastructure cost.
- _Cons:_ If the server goes down, everything goes down. Difficult to update.

#### **B. Classic Three-Tier Architecture**

Separation of concerns into three levels:

1. **Presentation Tier:** Web server (Nginx) or frontend framework. Handles display and static file distribution.
2. **Logic Tier:** Backend server (API) where the business logic resides.
3. **Data Tier:** A separate database server.

- _Advantage:_ Tiers can be scaled independently (e.g., adding more API servers without touching the DB).

#### **C. N-Tier Architecture (N-Tier / Microservices)**

The modern standard for large systems.

- **Client** -> **CDN** (for static files) -> **API Gateway** -> **Microservices** -> **Caches (Redis)** -> **DB Clusters**.
- Static files here are fully offloaded to S3 + CDN to avoid loading the main compute servers.

---

### **Comparison of Static File Strategies**

| Method                    | Complexity | Scalability | Speed for user    |
| ------------------------- | ---------- | ----------- | ----------------- |
| **Inside project folder** | Low        | Zero        | Depends on server |
| **S3 Storage**            | Medium     | Infinite    | High              |
| **S3 + CDN**              | High       | Infinite    | **Maximum**       |

</details>

---

<details>
<summary><span>64. Data Exchange Methods: <b>Polling, Streaming, WebSocket, Pub/Sub</b></span></summary>
<br />

The choice of method depends on how critical latency is and how often data is updated.

### **1. Polling**

- **Short Polling:** The client asks every N seconds: "Any news?". The server immediately answers "Yes" or "No".
- _Minus:_ Many unnecessary empty requests.
- **Long Polling:** The client asks, but the server **holds the connection open** until data appears (or a timeout occurs).
- _When it's better:_ When data is updated infrequently and an instantaneous reaction is not required.

### **2. Streaming vs WebSockets**

- **WebSockets:** A two-way (Full-duplex) channel. Ideal for chats and games.
- **Streaming (SSE - Server-Sent Events):** A one-way channel from server to client. Easier to implement than sockets.
- **Comparison:** **Polling** is about periodicity (discreteness). **Streaming** is when there is no periodicity and data flows as it becomes available.

### **3. Pub/Sub (Publisher/Subscriber)**

A pattern for exchanging messages between services via a broker (e.g., Redis, RabbitMQ).

- A publisher sends a message to a "topic" without knowing who will receive it.
- Subscribers receive a copy of the message. This allows for maximum "decoupling" of system components.

---

### **4. Service Discovery**

In a dynamic environment (Docker, K8s), the IP addresses of services are constantly changing.

- **Service Discovery** is a "phone book" (e.g., Consul, Eureka) where each service registers its address so that others can find it.

</details>

---

<details>
<summary><span>65. Resilience: <b>Retries, Backoff, Circuit Breaker, Idempotency</b></span></summary>
<br />

If Service B does not respond to Service A, we must be able to handle this error correctly.

### **1. Idempotency and Retries**

- **Retry:** Re-sending a request upon error.
- **Problem:** If a payment request was successful but the response was lost, a retry will charge the money a second time.
- **Solution:** **Idempotency Key** (Idempotency Key / Request ID). The client generates a unique ID. The server checks: "Have I processed this ID already?". If yes, it simply returns the old result without repeating the action.

### **2. Backoff and Backpressure**

- **Exponential Backoff:** You cannot retry every second. You need to increase the pause: 1s, 2s, 4s, 8s... so as not to "finish off" an already failing service.
- **Backpressure:** When the receiver cannot keep up with processing data, it tells the sender: "Slow down!". This prevents queue overflows and memory crashes.

### **3. Circuit Breaker**

Protects the system from cascading failures. States:

1. **Closed:** Everything is fine, requests go through.
2. **Open:** Too many errors. Requests are immediately rejected with an error without reaching the service. We give it time to "rest".
3. **Half-Open:** We allow one trial request. If it is successful, we close the circuit breaker.

---

### **4. Graceful Degradation and Fallback**

- **Graceful Degradation:** The ability of a system to function partially (e.g., if the recommendation service fails, the main page will simply show a list of popular products but will not crash entirely).
- **Fallback:** A backup plan. "If data could not be retrieved from the cache and DB, return an empty list or data from a static file."

</details>

---

<details>
<summary><span>66. Data Patterns: <b>CQRS, MapReduce, Caching</b></span></summary>
<br />

### **1. CQRS (Command Query Responsibility Segregation)**

Separation of the **Write** model (Command) and the **Read** model (Query).

- _Why:_ Data often needs to be read in a completely different form than it is written. You can use a fast DB for writing (e.g., Postgres) and Elastic for search (reading).

### **2. Cache Tagging and Versioning**

- **Versioning:** Adding a version to the key (`user_v1_123`). When the data schema changes, simply change the version in the code, and the old cache is ignored.
- **Tagging:** Assigning tags to cache entries. Allows you to clear (invalidate) all entries with the `articles` tag at once without touching the rest of the cache.

### **3. MapReduce**

A model for processing huge volumes of data on a cluster:

1. **Map:** Divide the task into parts and distribute them to worker nodes.
2. **Reduce:** Collect results from all nodes into a single final answer.

</details>

---

<details>
<summary><span>67. Background Task Execution</span></summary>
<br />

### **The Problem of Load Variability**

Example with YouTube: today a video uploads in 1 hour, and tomorrow in 3 hours.

- **Reason:** The load on the video encoding cluster is uneven.
- **Solution:** Task queues. We don't make the user wait for the processing to finish. We say: "Accepted," put the task in a queue, and worker nodes (Workers) process it as they are able.
- **User Experience:** If the queue grows, processing time increases, but the system does not crash and continues to accept new files.

</details>

---

<details>
<summary><span>68. Interaction in Microservices: <b>Aggregator</b> and <b>Chaining</b></span></summary>
<br />

When functionality is broken down into many small services, the question arises: how to collect data for the user if it resides in different places?

### **1. Aggregator Pattern**

This is a service (or API Gateway) that receives a single request from a client, makes parallel requests to several microservices, combines their responses, and returns a single result to the client.

- **Example:** A product page. The aggregator goes to `Service A` for the description, `Service B` for the price, and `Service C` for stock availability.
- **Pros:** The client makes only one network request. The merging logic is hidden inside.
- **Cons:** The aggregator can become a bottleneck and a single point of failure.

### **2. Chaining Pattern**

Services are called sequentially: Client -> Service A -> Service B -> Service C.

- **Example:** Order placement. `Order Service` creates an order, then calls `Payment Service` for payment, which in turn calls `Inventory Service` to reserve the item.
- **Pros:** Direct and clear sequence of actions.
- **Cons:** Long chains increase response time (latency adds up). If even one link in the middle fails, the entire chain is broken.

</details>

---

<details>
<summary><span>69. Event-Driven Architecture (EDA): <b>3 Interaction Types</b></span></summary>
<br />

Instead of direct calls (REST/gRPC), services communicate via a message bus (Kafka/RabbitMQ). Martin Fowler identifies several key approaches in EDA:

### **1. Event Notification**

A service sends a minimal message: "Event X occurred with object ID=123".

- **How it works:** The recipient, upon learning of the change, must itself go to the source service via API to retrieve the details.
- **Pros:** Messages are very lightweight. High degree of independence (Decoupling).
- **Cons:** Increased load on the source, as all subscribers will come to it for details.

### **2. Event-Carried State Transfer**

A service sends **all data** that changed in the message.

- **How it works:** "User 123 changed email to new@mail.com". The recipient does not need to go anywhere; it simply updates its local copy of the data (cache).
- **Pros:** Maximum autonomy. The recipient can work even if the source service is unavailable.
- **Cons:** Data duplication across the system. It is necessary to ensure that data in all services does not "diverge".

### **3. Event Collaboration**

In this approach, there is no central "controller" of the business process. Services simply react to each other's actions.

- **Example:** Order created -> Warehouse sees the event and reserves the item -> Delivery sees the reservation event and assigns a courier.
- **Pros:** Flexibility — it is easy to add a new participant to the process simply by subscribing them to events.
- **Cons:** It is very difficult to understand the overall process logic ("what follows what") just by looking at the code of one service.

### **Summary Comparison of EDA Strategies:**

| Pattern            | What's inside the message? | Dependence on source             | Network load           |
| ------------------ | -------------------------- | -------------------------------- | ---------------------- |
| **Notification**   | Only ID and event type.    | **High** (extra request needed). | Low (small messages).  |
| **State Transfer** | Full object (Snapshot).    | **Zero**.                        | High (heavy messages). |
| **Collaboration**  | Command/Fact of action.    | Depends on implementation.       | Medium.                |

</details>

---

<details>
<summary><span>70. Call Optimization: <b>Throttling</b> and <b>Debouncing</b></span></summary>
<br />

| Method         | Essence                                                                                        | How it works                                                                                                                                                                                                                  | Analogy                                                                                 | Where to use                                                                                                |
| -------------- | ---------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| **Throttling** | Guarantees that a function will be called **no more than once in a specified period of time**. | If we set a limit of 1 second and the user performs 10 actions, the function will execute at the start of the second, and all other clicks during that second will be ignored. The next call is possible only after 1 second. | A water tap that releases exactly one drop per second, no matter how hard you press it. | - Tracking page scrolling (`onScroll`) — to avoid recalculating element positions 100 times per second.<br> |

<br>- Window resizing (`onResize`).<br>

<br>- Processing game events (e.g., shooting in a shooter). |
| **Debouncing** | Postpones the function call until a certain amount of time has passed **since the last action**. | Every time an event occurs, the "waiting timer" is reset. The function will execute only when the user takes a pause. | An elevator in a high-rise. It doesn't move immediately as soon as the first person enters. It waits 5-10 seconds: if someone else enters, the timer resets. The elevator moves only when people stop entering. | - Live search (Autocomplete) — to avoid sending a request to the server after every typed letter, but wait until the user finishes writing the word.<br>

<br>- Form submit button — to prevent a double click and creating two orders. |

---

### **Comparison of Throttling and Debouncing**

| Characteristic       | Throttling                         | Debouncing                       |
| -------------------- | ---------------------------------- | -------------------------------- |
| **Main Goal**        | Limit frequency (constant rhythm). | Wait for silence (pause).        |
| **When it triggers** | Regularly during the process.      | Only at the end (after a pause). |
| **Execution**        | Once per X milliseconds.           | X ms after the last event.       |
| **Best Example**     | Page scrolling.                    | Search input field.              |

[Image showing Throttling vs Debouncing timelines comparison]

---

### **Why is this important for System Design?**

These mechanisms are used not only on the frontend but also at the API level (Rate Limiting) and in distributed systems:

1. **Resource Protection:** We don't allow a client to "spam" the backend with heavy requests.
2. **Cost Savings:** Fewer requests mean lower costs for traffic, CPU, and cloud computing.

</details>

---

<details>
<summary><span>71. Distributed Transactions: <b>2PC, Saga, Outbox/Inbox</b></span></summary>
<br />

In distributed systems, data is spread across different databases, making it difficult to ensure **ACID**.

### **1. Two-Phase Commit (2PC)**

This is a classic protocol for ensuring atomicity.

- **Phase 1 (Prepare):** The coordinator asks all nodes: "Are you ready to write the data?". Nodes check conditions and lock resources.
- **Phase 2 (Commit/Abort):** If **all** answered "Yes," the coordinator gives the command to write. If at least one answered "No" or remained silent, an abort command is sent to all.
- **Minus:** Low performance due to locks. If the coordinator fails between phases, the system "hangs."

### **2. Saga Pattern**

Instead of locks, a chain of local transactions is used.

- For every action, there is a **compensating action** (rollback).
- If an error occurs at step #3, the Saga sequentially performs rollbacks for steps #2 and #1.
- _Types:_ **Orchestration** (control center) and **Choreography** (services react to events).

### **3. Transactional Outbox / Inbox**

A pattern for reliable message transfer between a DB and a broker (Kafka).

- **Outbox:** In one transaction, we write data to the entity table and to a special `outbox` table. A separate process (Relay) reads the `outbox` table and sends messages to the broker. This guarantees that the event is not lost if the broker is down.
- **Inbox:** Similarly on the receiver side — first save the incoming event in the DB, and then process it to avoid duplicates during redeliveries.

</details>

---

<details>
<summary><span>72. Consensus and Coordination: <b>Raft, Paxos, Leaders</b></span></summary>
<br />

Consensus is when multiple nodes must agree on a single value (e.g., who is currently the Master).

### **1. Leader Election**

In a cluster, there must be a main node that coordinates writing.

- **Bully Algorithm:** When a node notices the leader has failed, it sends a request to all nodes with an ID higher than its own. If no one responds, it declares itself the leader. If "senior" nodes respond, they begin their own elections. The "strongest" (with the highest ID) wins.

### **2. Raft and Paxos**

These are modern consensus protocols.

- **Paxos:** The first theoretically correct protocol. Very difficult to implement.
- **Raft:** Designed as a more understandable alternative to Paxos. It uses three states: _Follower, Candidate, Leader_. It is built on log replication.
- **Where they are used:** **etcd** (the basis of Kubernetes) uses Raft; **Zookeeper** uses ZAB (similar to Paxos).

### **3. Distributed Locks**

Needed so that different processes do not modify the same resource simultaneously.

- Usually implemented via **Redis (Redlock)** or **Zookeeper/etcd**.
- It is important to use a **TTL** (Time To Live) so that if the lock owner "dies," the resource does not remain locked forever.

</details>

---

<details>
<summary><span>73. System Design: <b>Functional and Non-Functional Requirements</b></span></summary>
<br />

Before drawing a diagram in System Design, you need to clearly outline the boundaries of the task.

### **1. Functional Requirements (FR)**

_What should the system do?_ These are specific features.

- _Example (for YouTube):_ A user can upload videos. A user can like videos. The system must support searching by titles.

### **2. Non-Functional Requirements (NFR)**

_How should the system work?_ These are constraints and qualities.

- **Scalability:** The system must handle 100 million users.
- **Availability:** 99.9% of the time (three nines).
- **Latency:** Video should start playing in no more than 200 ms.
- **Durability:** An uploaded video must not be lost under any circumstances.

> **Why separate them?** FRs determine the code architecture (logic), while NFRs determine the infrastructure architecture (sharding, replication, CDN).

</details>
