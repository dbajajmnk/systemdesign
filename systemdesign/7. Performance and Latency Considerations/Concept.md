# 📘 Module 8 – Reliability and Fault Tolerance

---

# 🎯 Why This Module Matters

Distributed systems fail.

Question is not:

"Will failures happen?"

Question is:

"How does system behave when they happen?"

Most outages happen because of:

❌ No retry strategy  
❌ No isolation  
❌ No redundancy  
❌ Cascading failures

---

# 🧠 Real-Life Mapping (Food Delivery → Reliability)

| Real System Problem | Reliability Pattern |
|---------------------|-------------------|
| Payment Gateway Down | Retry + Fallback |
| Delivery Service Crash | Failure Isolation |
| Database Failure | Redundancy |
| Recommendation Failure | Graceful Degradation |

---

# 1️⃣ Designing For Failures

---

## ✅ WHAT

Build assuming components fail.

---

## 🎯 WHY

Without this:

- Single failure breaks entire flow

---

## ❌ Fragile System

```mermaid
flowchart LR

User --> OrderService
OrderService --> PaymentService
PaymentService --> Success
```

Payment fails → everything fails.

---

## ✅ Failure-Aware System

```mermaid
flowchart LR

User --> OrderService
OrderService --> PaymentService
PaymentService --> RetryQueue
RetryQueue --> FallbackState
```

---

## 🧠 Meaning

Failures expected.

System survives.

---

# 2️⃣ Redundancy and Graceful Degradation

---

## ✅ WHAT

Redundancy = backups

Graceful degradation = reduced service instead of outage

---

## ❌ No Redundancy

```mermaid
flowchart TD

User --> Server1
Server1 --> Crash
```

System down.

---

## ✅ With Redundancy

```mermaid
flowchart LR

User --> LB

LB --> Server1
LB --> Server2
```

If one fails, traffic shifts.

---

## 🍔 Graceful Degradation Example

Recommendations fail:

Show basic restaurant listing.

Ordering still works.

---

```mermaid
flowchart TD

App --> Recommendation

Recommendation --> Failure

Failure --> BasicCatalog

BasicCatalog --> UserOrder
```

---

# 3️⃣ Timeout Retry Fallback

---

## ✅ WHAT

Three protection layers:

- Timeout  
- Retry  
- Fallback

---

## Retry Pattern

```mermaid
flowchart LR

Request --> Try1

Try1 --> Success

Try1 --> Retry

Retry --> Success

Retry --> Fallback
```

---

## 🧠 Meaning

Don't wait forever.

Recover first.

Fallback if needed.

---

## Common Rule

Retry only for transient failures.

---

# 4️⃣ Failure Isolation

---

## ✅ WHAT

One failing service should not break all services.

---

## ❌ Bad Design

```mermaid
flowchart LR

Order --> Payment

Payment --> Notification

Notification --> Delivery
```

Notification fails

Everything blocks.

---

## ✅ Failure Isolation

```mermaid
flowchart LR

Order --> Payment

Order --> Delivery

Order --> Notification
```

Notification fails

Order still completes.

---

## Event Isolation Example

```mermaid
flowchart LR

Order --> Event

Event --> Payment
Event --> Delivery
Event --> Notify
```

Loose coupling.

Failure contained.

---

# 5️⃣ Circuit Breaker

---

## Circuit Breaker States

```mermaid
stateDiagram-v2

[*] --> Closed

Closed --> Open : failures

Open --> HalfOpen : cooldown

HalfOpen --> Closed : success

HalfOpen --> Open : fail
```

---

## Meaning

Stop hitting broken service repeatedly.

---

# 6️⃣ Reliability Tools

---

## Infrastructure

- Kubernetes Health Probes  
- Load Balancers  
- Multi-AZ Deployments

---

## Messaging

- Apache Kafka  
- RabbitMQ

---

## Reliability Patterns

- Circuit Breakers  
- Bulkheads  
- Dead Letter Queues

---

# 🚨 Common Mistakes

---

❌ Infinite retries

❌ No timeout

❌ Shared dependency blast radius

❌ Assuming services always available

❌ No fallback logic

---

# 🧠 How To Evaluate Reliability

Ask:

- What fails first?
- What happens if dependency dies?
- Can system degrade?
- Is blast radius limited?

---

# 🎯 Interview Thinking

---

## Q: What is fault tolerance?

Continue operating despite failures.

---

## Q: What is graceful degradation?

Reduced functionality instead of outage.

---

## Q: What causes cascading failures?

Uncontrolled dependency failures.

---

## Q: How do retries become dangerous?

Retry storms increase load.

---

# 🔟 Final Mental Model

```mermaid
flowchart LR

A[Assume Failure]

B[Add Redundancy]

C[Isolate Failures]

D[Recover Gracefully]

A --> E[Reliable System]
B --> E
C --> E
D --> E
```

---

# 🧠 One-Line Summary

Reliable systems assume failures, contain them, and continue serving users.

---