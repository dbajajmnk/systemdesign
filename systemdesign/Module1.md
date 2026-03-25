Below is a beginner-friendly **System Design Terms Guide** using **What, Why, When, How** plus **real-life analogies**. I’m grounding the foundation terms in the notes you shared, especially around requirements, constraints, assumptions, and trade-offs. 

# System Design Terms

Think of **system design** like planning a **city** or **running a large restaurant**, not just writing one function.

---

## 1) System Design

**What:**
System design is the process of organizing components, data, and communication so a product can solve business problems at real-world scale. 

**Why:**
Because writing code for one feature is not enough. Real products must handle users, failures, traffic spikes, data growth, and business rules.

**When:**
Before coding major features, before choosing database/tools, and before drawing architecture diagrams. 

**How:**
You identify requirements, constraints, traffic, storage, failure cases, and trade-offs—then design the system accordingly.

**Real-life analogy:**
Building a house is coding. Planning a whole apartment complex with water, electricity, parking, and safety is system design.

**Mini image in mind:**

```text
Users → App → Services → Database / Cache / Queue / Storage
```

---

## 2) Functional Requirements

**What:**
These describe **what the system should do**. 

**Why:**
Without this, you do not know the actual business problem.

**When:**
At the very beginning of design.

**How:**
Write clear actions like:

* user can sign up
* user can place an order
* admin can view reports
* customer can track delivery

**Real-life analogy:**
For a restaurant, functional requirements are:

* take orders
* prepare food
* serve customers
* generate bill

---

## 3) Non-Functional Requirements

**What:**
These describe **how well the system should perform**. Examples: speed, reliability, security, scale. 

**Why:**
These heavily influence architecture decisions. 

**When:**
Right after or alongside functional requirements.

**How:**
Define targets such as:

* response time under 200 ms
* 99.9% availability
* support 1 million users
* secure payment processing

**Real-life analogy:**
A delivery service must not only deliver food, but deliver it **fast**, **correctly**, and **safely**.

---

## 4) Constraints

**What:**
Constraints are limits or boundaries in the system. 

**Why:**
Because real engineering is never unlimited. Time, budget, people, tools, and external services all create restrictions.

**When:**
During planning and whenever making architecture decisions.

**How:**
List them clearly:

* only 2 developers
* low budget
* must use cloud provider X
* payment handled by third-party gateway
* launch needed in 1 month

**Real-life analogy:**
You want a luxury wedding, but budget allows only a medium hall and limited food menu.

---

## 5) Assumptions

**What:**
Assumptions are things you believe to be true when requirements are incomplete. 

**Why:**
Because system design problems are often incomplete and you still need to move forward.

**When:**
Whenever information is missing.

**How:**
State them explicitly:

* assuming most traffic is read-heavy
* assuming users are from one region initially
* assuming payments are asynchronous

**Real-life analogy:**
If guests have not confirmed attendance, you may assume around 70% will come and plan food accordingly.

---

## 6) Trade-offs

**What:**
Trade-offs are choices where improving one thing may worsen another. 

**Why:**
There is no perfect system. Every good design balances goals. 

**When:**
At almost every architecture decision.

**How:**
Choose deliberately:

* speed vs accuracy
* consistency vs availability
* cost vs performance
* simplicity vs scalability

**Real-life analogy:**
You can take a direct flight that is expensive, or a cheaper one with long layovers.

---

## 7) Scalability

**What:**
Scalability is the ability of a system to handle more users, more traffic, and more data without breaking.

**Why:**
Because successful products grow.

**When:**
When you expect user growth or sudden traffic spikes.

**How:**
Use:

* load balancing
* caching
* database sharding
* horizontal scaling
* queues for background work

**Real-life analogy:**
A small tea stall may serve 20 people, but a food court can serve thousands because it has more counters, staff, and organized flow.

**Mini image:**

```text
1 server  → handles small load
5 servers → share bigger load
```

---

## 8) Availability

**What:**
Availability means the system is up and usable when users need it.

**Why:**
A feature is useless if the system is frequently down.

**When:**
Very important for banking, shopping, ride booking, food delivery, healthcare, and SaaS tools.

**How:**
Improve it using:

* redundant servers
* failover
* health checks
* replication
* monitoring and alerts

**Real-life analogy:**
A hospital emergency room must stay open almost all the time.

---

## 9) Reliability

**What:**
Reliability means the system behaves correctly and consistently over time.

**Why:**
Users trust systems that produce correct results.

**When:**
Critical in payments, bookings, messaging, and data processing.

**How:**
Use:

* retries carefully
* validation
* durable storage
* backups
* idempotency
* strong testing

**Real-life analogy:**
An elevator should not only work today; it should work safely every day.

---

## 10) Latency

**What:**
Latency is the time taken for one request to get a response.

**Why:**
Users hate slow apps.

**When:**
Important in search, payments, chat, gaming, and dashboards.

**How:**
Reduce latency using:

* caching
* optimized queries
* CDN
* better algorithms
* regional deployments

**Real-life analogy:**
Latency is like how long you wait after ordering tea until it reaches your table.

---

## 11) Throughput

**What:**
Throughput is how many requests or operations the system can handle in a given time.

**Why:**
A system may be fast for one user but fail under many users.

**When:**
Important for high-traffic apps.

**How:**
Increase throughput with:

* scaling servers
* batching
* asynchronous processing
* queues
* efficient resource usage

**Real-life analogy:**
A toll booth may process 10 cars per minute, while multiple toll lanes process many more.

---

## 12) Load Balancer

**What:**
A load balancer distributes traffic across multiple servers.

**Why:**
It prevents one server from becoming overloaded.

**When:**
When you have more than one application server.

**How:**
Incoming requests first hit the load balancer, which forwards them to healthy servers.

**Real-life analogy:**
A restaurant host sends customers to different tables instead of crowding one area.

**Mini image:**

```text
          /→ Server 1
Users → LB → Server 2
          \→ Server 3
```

---

## 13) Database

**What:**
A database stores and manages application data.

**Why:**
Apps need persistent storage.

**When:**
Almost always, unless the system is extremely temporary.

**How:**
Choose based on use case:

* SQL for structured relationships
* NoSQL for flexibility and scale patterns

**Real-life analogy:**
A database is like the official record register in a school or bank.

---

## 14) Cache

**What:**
A cache stores frequently used data temporarily for faster access.

**Why:**
To reduce database load and improve speed.

**When:**
When the same data is requested repeatedly.

**How:**
Store hot data in Redis, in-memory cache, or CDN.

**Real-life analogy:**
Keeping commonly used spices near the stove instead of going to the storeroom every time.

**Mini image:**

```text
User Request → Cache?
             → Hit  = fast response
             → Miss = go to DB, then store in cache
```

---

## 15) Queue

**What:**
A queue stores tasks to be processed later or by background workers.

**Why:**
Not everything should happen in the user request path.

**When:**
For email sending, notifications, video processing, report generation, order events.

**How:**
App puts tasks into a queue; workers consume them asynchronously.

**Real-life analogy:**
Customers take tokens at a service center and are served one by one.

---

## 16) Asynchronous Processing

**What:**
Work happens in the background instead of making the user wait.

**Why:**
It improves user experience and prevents timeouts.

**When:**
For heavy or slow tasks.

**How:**
Use queues, worker services, and event-driven processing.

**Real-life analogy:**
You place an online order now, but packing and shipping happen later in the warehouse.

---

## 17) Replication

**What:**
Replication means keeping copies of data on multiple servers.

**Why:**
For availability, backups, and read scaling.

**When:**
When one database is not enough or uptime matters.

**How:**
Primary database writes data; replicas copy it and may serve read requests.

**Real-life analogy:**
Keeping photocopies of important documents in multiple places.

---

## 18) Sharding

**What:**
Sharding means splitting data across multiple databases.

**Why:**
One database machine may not handle very large scale forever.

**When:**
When dataset or traffic becomes too large.

**How:**
Split by user ID, region, tenant, or another key.

**Real-life analogy:**
Instead of one giant warehouse for all India, you create separate warehouses by region.

---

## 19) Consistency

**What:**
Consistency means users see correct and expected data.

**Why:**
Incorrect data can cause trust issues and business failures.

**When:**
Very important in banking, inventory, bookings, and payments.

**How:**
Use strong consistency when correctness matters most, or eventual consistency where slight delay is acceptable.

**Real-life analogy:**
If one cinema seat is booked, all booking counters should know it quickly to avoid double booking.

---

## 20) Fault Tolerance

**What:**
Fault tolerance means the system continues working even when some parts fail.

**Why:**
Failures are normal in distributed systems.

**When:**
Always important in real production systems.

**How:**
Use:

* retries
* redundancy
* fallback
* replication
* circuit breakers
* graceful degradation

**Real-life analogy:**
If one lift in a mall stops working, the building still runs because other lifts and escalators exist.

---

## 21) Single Point of Failure (SPOF)

**What:**
A single component whose failure can bring down the whole system.

**Why:**
It is dangerous for uptime and reliability.

**When:**
Whenever you have only one server, one database, one payment dependency, or one network path.

**How:**
Remove SPOFs using redundancy and backup options.

**Real-life analogy:**
If a shop has only one cashier and that cashier leaves, all billing stops.

---

## 22) Idempotency

**What:**
An operation is idempotent if doing it multiple times gives the same final result.

**Why:**
Very important in retries, payments, and APIs.

**When:**
When network failures may cause duplicate requests.

**How:**
Use idempotency keys or unique request IDs.

**Real-life analogy:**
Pressing the elevator button 5 times should not create 5 elevators.

---

## 23) API

**What:**
An API is a contract through which systems communicate.

**Why:**
Frontend, mobile apps, and services need standard ways to exchange data.

**When:**
Whenever one component talks to another.

**How:**
Design endpoints, request/response formats, error handling, authentication, and versioning.

**Real-life analogy:**
A waiter is the API between customer and kitchen.

---

## 24) Monitoring

**What:**
Monitoring means observing system health and behavior.

**Why:**
You cannot fix what you cannot see.

**When:**
Always in production.

**How:**
Track:

* CPU
* memory
* latency
* error rates
* traffic
* queue size
* database performance

**Real-life analogy:**
The dashboard in a car tells you fuel level, engine temperature, and speed.

---

## 25) Rate Limiting

**What:**
Rate limiting controls how many requests a user or client can make in a time period.

**Why:**
Prevents abuse, overload, and unfair usage.

**When:**
For public APIs, login endpoints, OTP systems, and expensive operations.

**How:**
Allow, for example, 100 requests per minute per user or IP.

**Real-life analogy:**
A store may allow only a limited number of people inside at once.

---

# Real-Life Analogy: Food Delivery App

This matches the foundation notes you shared. 

## Scenario: Placing a Food Order

**Functional requirements**

* customer places order
* restaurant accepts order
* rider gets assignment
* customer tracks delivery

**Non-functional requirements**

* payment should be safe
* app should work during lunch rush
* order status should be reliable
* response should be fast

**Constraints**

* third-party payment gateway
* limited number of riders
* peak traffic at lunch and dinner

**Trade-offs**

* faster order placement vs deep validation
* real-time accuracy vs lower infrastructure cost
* simple design now vs scalable design later

**System design view**

```text
Customer App
   ↓
Order Service
   ↓
Payment Service
   ↓
Restaurant Service
   ↓
Delivery Assignment Service
   ↓
Tracking / Notifications
```

---

# Quick Visual Memory Map

```text
System Design
│
├── What system should do
│   └── Functional Requirements
│
├── How well it should do
│   └── Non-Functional Requirements
│
├── Limits and beliefs
│   ├── Constraints
│   └── Assumptions
│
├── Choices to balance
│   └── Trade-offs
│
└── Architecture qualities
    ├── Scalability
    ├── Availability
    ├── Reliability
    ├── Latency
    ├── Throughput
    ├── Consistency
    └── Fault Tolerance
```

# One-line Summary

**Good system design means choosing the right structure and trade-offs to solve business problems under real-world constraints.** 

# 📘 System Design Terms – Knowledge Check (MCQ + Subjective with Answers)

---

# 🧠 MCQs (Professional & Balanced)

## 🔹 Section 1: Core Concepts

1. System design primarily focuses on:  
A. Writing functions  
B. UI design  
C. Structuring large-scale systems  
D. Debugging code  

2. Functional requirements define:  
A. Performance  
B. Features  
C. Latency  
D. Security  

3. Non-functional requirements include:  
A. Login  
B. Signup  
C. Response time  
D. CRUD operations  

4. Which is a constraint?  
A. Send message  
B. Low budget  
C. Login feature  
D. UI design  

5. Assumptions are used when:  
A. Requirements are clear  
B. Data is available  
C. Information is missing  
D. System is deployed  

6. Trade-offs involve:  
A. Perfect design  
B. No compromise  
C. Balancing decisions  
D. Ignoring constraints  

7. Scalability ensures:  
A. Better UI  
B. More features  
C. Handling growth  
D. Faster coding  

8. Availability means:  
A. Correct output  
B. System uptime  
C. UI response  
D. Data storage  

9. Reliability ensures:  
A. Speed  
B. Accuracy over time  
C. UI quality  
D. Deployment  

10. Latency measures:  
A. Throughput  
B. Speed of response  
C. Data size  
D. CPU usage  

---

## 🔹 Section 2: Performance & Scaling

11. Throughput refers to:  
A. Speed of one request  
B. Number of requests handled  
C. Data storage  
D. UI rendering  

12. Load balancer helps:  
A. Store data  
B. Distribute traffic  
C. Improve UI  
D. Cache data  

13. Cache improves:  
A. Storage  
B. Security  
C. Speed  
D. UI  

14. Queue is used for:  
A. UI  
B. Background processing  
C. Storage  
D. Styling  

15. Asynchronous processing:  
A. Blocks user  
B. Runs instantly  
C. Runs in background  
D. Deletes data  

16. Replication is used for:  
A. UI  
B. Backup & availability  
C. CSS  
D. Routing  

17. Sharding helps in:  
A. UI design  
B. Splitting data  
C. Styling  
D. Caching  

18. Consistency ensures:  
A. Speed  
B. Correct data  
C. UI  
D. Deployment  

19. Fault tolerance means:  
A. No failure  
B. System survives failure  
C. UI  
D. CSS  

20. SPOF refers to:  
A. Multiple servers  
B. Backup  
C. Single failure point  
D. Load balancer  

---

## 🔹 Section 3: Advanced Concepts

21. Idempotency ensures:  
A. Duplicate effects  
B. Same result on retries  
C. UI  
D. Storage  

22. API acts as:  
A. DB  
B. UI  
C. Communication layer  
D. Cache  

23. Monitoring helps:  
A. Ignore issues  
B. Detect issues  
C. UI  
D. CSS  

24. Rate limiting prevents:  
A. Speed  
B. Abuse  
C. UI  
D. DB  

25. Which improves latency?  
A. Cache  
B. UI  
C. CSS  
D. HTML  

26. Which improves availability?  
A. Replication  
B. UI  
C. CSS  
D. HTML  

27. Which improves throughput?  
A. Scaling  
B. UI  
C. CSS  
D. HTML  

28. Queue helps:  
A. UI  
B. Async work  
C. Styling  
D. Layout  

29. Trade-off example:  
A. Speed vs cost  
B. UI vs CSS  
C. HTML vs JS  
D. Color vs font  

30. Constraint example:  
A. Login  
B. Budget limit  
C. UI  
D. Button  

---

## 🔹 Section 4: Scenario-Based

31. App crashes when DB fails. Issue?  
A. Cache  
B. SPOF  
C. UI  
D. CSS  

32. System handles more users by adding servers:  
A. Sharding  
B. Replication  
C. Horizontal scaling  
D. Cache  

33. Slow DB queries solved by:  
A. Cache  
B. UI  
C. CSS  
D. HTML  

34. Duplicate payment prevention uses:  
A. Retry  
B. Idempotency  
C. Cache  
D. UI  

35. Sending emails later uses:  
A. Queue  
B. DB  
C. UI  
D. CSS  

36. System downtime reduced by:  
A. Replication  
B. UI  
C. CSS  
D. HTML  

37. API overload handled by:  
A. Rate limiting  
B. Cache  
C. UI  
D. CSS  

38. Data split across DBs:  
A. Replication  
B. Sharding  
C. Cache  
D. UI  

39. High latency reduced by:  
A. Cache  
B. UI  
C. CSS  
D. HTML  

40. System monitoring tracks:  
A. UI  
B. Metrics  
C. CSS  
D. HTML  

---

## 🔹 Section 5: Mixed

41. Functional requirement example:  
A. Login  
B. Latency  
C. Availability  
D. Throughput  

42. Non-functional example:  
A. Signup  
B. Latency  
C. Order  
D. Chat  

43. External system example:  
A. DB  
B. API  
C. Payment gateway  
D. Cache  

44. Internal system example:  
A. Stripe  
B. Maps  
C. Auth service  
D. SMS  

45. Load balancer prevents:  
A. UI  
B. Overload  
C. CSS  
D. HTML  

46. Cache reduces:  
A. DB load  
B. UI  
C. CSS  
D. HTML  

47. Queue improves:  
A. UI  
B. User wait time  
C. CSS  
D. HTML  

48. Reliability ensures:  
A. Speed  
B. Correctness  
C. UI  
D. CSS  

49. Latency is:  
A. Count  
B. Time  
C. UI  
D. CSS  

50. Throughput is:  
A. Time  
B. Count  
C. UI  
D. CSS  

---

# 🧾 Answer Key

1-C 2-B 3-C 4-B 5-C  
6-C 7-C 8-B 9-B 10-B  

11-B 12-B 13-C 14-B 15-C  
16-B 17-B 18-B 19-B 20-C  

21-B 22-C 23-B 24-B 25-A  
26-A 27-A 28-B 29-A 30-B  

31-B 32-C 33-A 34-B 35-A  
36-A 37-A 38-B 39-A 40-B  

41-A 42-B 43-C 44-C 45-B  
46-A 47-B 48-B 49-B 50-B  

---

# 🧠 Subjective Questions with Answers

---

### 1. What is system design?
System design is the process of structuring components, data, and interactions to build scalable systems.

---

### 2. Functional vs Non-functional?
Functional → features  
Non-functional → performance  

---

### 3. What are constraints?
Limitations like budget, time, or tools.

---

### 4. What are assumptions?
Beliefs made when requirements are incomplete.

---

### 5. Explain trade-offs
Balancing decisions like speed vs cost.

---

### 6. What is scalability?
Handling growth in users/data.

---

### 7. What is availability?
System uptime.

---

### 8. What is reliability?
Consistent correct behavior.

---

### 9. What is latency?
Time to respond.

---

### 10. What is throughput?
Requests handled per unit time.

---

### 11. What is load balancing?
Distributing traffic across servers.

---

### 12. What is caching?
Storing frequent data for fast access.

---

### 13. What is a queue?
Background task processing.

---

### 14. Async processing?
Work done without blocking user.

---

### 15. Replication?
Copying data across servers.

---

### 16. Sharding?
Splitting data across DBs.

---

### 17. Consistency?
Correct and synchronized data.

---

### 18. Fault tolerance?
System survives failures.

---

### 19. Idempotency?
Same result on repeated calls.

---

### 20. Monitoring?
Tracking system health and metrics.

---
Assignment : 
Start with your project idea
Come up with some lines regarding each and every point 




