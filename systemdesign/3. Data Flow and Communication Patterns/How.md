# 📘 Module 3 – HOW to Implement Data Flow & Communication Patterns

---

# 🎯 Goal of This README

This guide answers:

> ❓ **HOW do we actually implement communication patterns in real systems?**

We will cover:

* How to design flows
* How to choose sync vs async
* How to implement event-driven systems
* How to handle failures in real code
* Tools used in industry

---

# 🧠 Step 1: Identify Communication Type

---

## ✅ HOW to Decide (Real Thinking)

Ask these 3 questions:

### 1. Does user need immediate response?

👉 YES → Use **Synchronous**

### 2. Can this run in background?

👉 YES → Use **Asynchronous**

### 3. Will multiple services react?

👉 YES → Use **Event-Driven**

---

## 🖼️ Decision Flow

```mermaid
flowchart TD
    A[Start]
    A --> B{Immediate Response Needed?}
    B -- Yes --> C[Use Synchronous]
    B -- No --> D[Use Async]

    D --> E{Multiple Consumers?}
    E -- Yes --> F[Use Event Driven]
    E -- No --> G[Use Queue Based Async]
```

---

# ⚙️ Step 2: Implement Synchronous Communication

---

## ✅ HOW (Backend API Example)

### 🔹 Use REST API

```js
// Order Service calling Payment Service

const response = await fetch("http://payment-service/pay", {
  method: "POST",
  body: JSON.stringify({ amount: 100 })
});

const data = await response.json();
```

---

## 🧠 Rules

* Keep response time < 200ms
* Add timeout
* Add retry (limited)
* Avoid deep chaining

---

## ⚠️ Common Mistake

❌ Order → Payment → Delivery → Notification (chain)

👉 Leads to cascading failure

---

# ⚙️ Step 3: Implement Asynchronous Communication

---

## ✅ HOW (Queue-Based)

### 🔹 Producer (Order Service)

```js
queue.publish("order_created", {
  orderId: 123,
  userId: 456
});
```

---

### 🔹 Consumer (Notification Service)

```js
queue.subscribe("order_created", (event) => {
  sendNotification(event.userId);
});
```

---

## 🧠 Tools Used

* Apache Kafka
* RabbitMQ
* Amazon SQS

---

## 🖼️ Flow

```mermaid
flowchart LR
    A[Order Service] --> Q[Queue]
    Q --> B[Notification Service]
```

---

# ⚙️ Step 4: Implement Event-Driven Architecture

---

## ✅ HOW (Real Design)

### 🔹 Event Publish

```js
eventBus.publish("OrderPlaced", {
  orderId: 123
});
```

---

### 🔹 Multiple Consumers

```js
eventBus.subscribe("OrderPlaced", paymentHandler);
eventBus.subscribe("OrderPlaced", deliveryHandler);
eventBus.subscribe("OrderPlaced", notificationHandler);
```

---

## 🖼️ Flow

```mermaid
flowchart LR
    A[Order Service] --> E[OrderPlaced Event]
    E --> B[Payment Service]
    E --> C[Delivery Service]
    E --> D[Notification Service]
```

---

## 🧠 Rules

* Events must be immutable
* Consumers must be idempotent
* Use schema versioning

---

# ⚙️ Step 5: Define Data Ownership

---

## ✅ HOW

### Rule:

👉 One service = one database

---

## ❌ Wrong

```mermaid
flowchart TD
    A[Order DB]
    B[Payment Service]

    B -->|Write| A
```

---

## ✅ Correct

```mermaid
flowchart TD
    A[Order Service]
    E[OrderPlaced Event]

    A --> E
    E --> B[Payment Service]
```

---

## 🧠 Implementation Tip

* Use **read replicas**
* Use **event-based sync**
* Never share DB

---

# ⚙️ Step 6: Handle Failures (MOST IMPORTANT)

---

## ✅ HOW to Implement Retry

```js
async function retry(fn, retries = 3) {
  try {
    return await fn();
  } catch (err) {
    if (retries === 0) throw err;
    return retry(fn, retries - 1);
  }
}
```

---

## ✅ HOW to Implement Timeout

```js
const controller = new AbortController();

setTimeout(() => controller.abort(), 2000);

fetch(url, { signal: controller.signal });
```

---

## ✅ HOW to Implement Idempotency

```js
if (db.has(idempotencyKey)) {
  return db.get(idempotencyKey);
}
```

---

## 🖼️ Failure Flow

```mermaid
flowchart TD
    A[Process Request]
    B{Success?}
    B -- Yes --> C[Done]
    B -- No --> D[Retry]
    D --> E{Retry Success?}
    E -- No --> F[Dead Letter Queue]
```

---

# ⚙️ Step 7: Real System Example (End-to-End)

---

## 🍔 Food Delivery System

```mermaid
flowchart LR
    U[User]
    A[API Gateway]
    O[Order Service]
    P[Payment Service]
    E[OrderPlaced Event]
    D[Delivery Service]
    N[Notification Service]

    U --> A
    A --> O
    O --> P
    O --> E
    E --> D
    E --> N
```

---

## 🧠 Breakdown

| Step                | Type  |
| ------------------- | ----- |
| Order validation    | Sync  |
| Payment             | Sync  |
| Delivery assignment | Async |
| Notification        | Async |

---

# 🧰 Tools You Should Know

---

## Communication

* Apache Kafka
* RabbitMQ
* gRPC

---

## Monitoring

* Prometheus
* Grafana

---

## Cloud

* AWS
* Azure

---

# 🚨 Common Mistakes (Real Industry)

* Using sync everywhere ❌
* No retry logic ❌
* No timeout ❌
* Shared database ❌
* No monitoring ❌

---

# 🧠 Final Mental Model

```mermaid
flowchart TD
    A[User Action]
    B[Sync Validation]
    C[Async Processing]
    D[Event Distribution]
    E[Failure Handling]

    A --> B --> C --> D --> E
```

---

# 🔟 One-Line Summary

> Build fast systems with sync, scale them with async, and make them reliable with failure handling.

---

