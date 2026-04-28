# 📘 Module 6 – Scalability Fundamentals

---

## 🎯 Why This Module Is Covered in Depth

Module 6 focuses on how systems grow over time. Many systems work correctly at small scale but fail when usage increases because scalability was treated as an afterthought.

This module builds the ability to:
- Anticipate growth
- Scale systems in a controlled manner
- Optimize cost vs performance

Scalability is not about blindly adding servers.  
It is about understanding system limits and scaling only what is necessary.

---

## 1️⃣ Vertical vs Horizontal Scaling

### ✅ WHAT
- **Vertical Scaling (Scale Up):** Increasing resources of a single machine (CPU, RAM, Storage)
- **Horizontal Scaling (Scale Out):** Adding more machines to distribute load

### 🎯 WHY
- Vertical scaling is simple but has physical limits
- Horizontal scaling supports long-term growth and fault tolerance

### ⏰ WHEN
- Vertical scaling → Early-stage systems
- Horizontal scaling → High traffic and large-scale systems

### 🍔 Use Case (Food Delivery)
- Initially: Single server handles orders (vertical scaling)
- During peak hours: Multiple instances handle traffic (horizontal scaling)

---

## 2️⃣ Load Distribution Concepts

### ✅ WHAT
Load distribution is the process of spreading incoming traffic across multiple components.

### 🎯 WHY
- Prevents overload on a single instance
- Ensures better performance and lower latency

### ⏰ WHEN
- When traffic exceeds single-instance capacity
- When traffic patterns are unpredictable

### 🍔 Use Case
- API requests distributed across multiple backend servers during lunch-time spikes

---

## 3️⃣ Bottlenecks and Capacity Planning

### ✅ WHAT
- **Bottleneck:** Component limiting system performance
- **Capacity Planning:** Estimating system load handling capability

### 🎯 WHY
- Scaling non-bottleneck components wastes resources
- Identifying bottlenecks improves system efficiency

### ⏰ WHEN
- During load testing
- Before product launches or promotions
- During performance analysis

### 🍔 Use Case
- During sales: Database writes become slow → DB is bottleneck, not API servers

---

## 4️⃣ Scaling System Components Independently

### ✅ WHAT
Different system components scale independently based on their load.

### 🎯 WHY
- Not all services grow equally
- Reduces infrastructure cost
- Improves performance efficiency

### ⏰ WHEN
- After clear microservice or modular boundaries are defined

### 🍔 Use Case
- Menu service (read-heavy) scales aggressively
- Payment service (consistency-critical) scales cautiously

---

# 🎤 Interview Question Bank with Answers

---

### ❓ Q1: What is scalability?  
**A:** The ability of a system to handle increased load efficiently by adding resources.

---

### ❓ Q2: What is vertical scaling?  
**A:** Increasing the capacity of a single machine.

---

### ❓ Q3: What is horizontal scaling?  
**A:** Adding multiple machines to distribute load.

---

### ❓ Q4: Why is horizontal scaling preferred?  
**A:** It avoids single-node limits and supports long-term growth.

---

### ❓ Q5: When is vertical scaling sufficient?  
**A:** In early stages or when growth is limited and predictable.

---

### ❓ Q6: What is load distribution?  
**A:** Spreading traffic across multiple components.

---

### ❓ Q7: Why is load balancing important?  
**A:** Ensures even utilization and reduces latency.

---

### ❓ Q8: What is a bottleneck?  
**A:** The component limiting system throughput.

---

### ❓ Q9: Why scale bottlenecks first?  
**A:** Because other scaling won’t improve performance.

---

### ❓ Q10: What is capacity planning?  
**A:** Estimating future resource requirements.

---

### ❓ Q11: How to identify bottlenecks?  
**A:** Monitoring, metrics, and load testing.

---

### ❓ Q12: What happens if capacity planning is ignored?  
**A:** System failures and poor user experience.

---

### ❓ Q13: What is independent scaling?  
**A:** Scaling each component based on its own demand.

---

### ❓ Q14: Why is independent scaling cost-effective?  
**A:** Only stressed components are scaled.

---

### ❓ Q15: How does statelessness help scaling?  
**A:** Any instance can handle any request.

---

### ❓ Q16: Why are databases hard to scale?  
**A:** Due to shared state and consistency requirements.

---

### ❓ Q17: How does caching help scalability?  
**A:** Reduces load on core systems.

---

### ❓ Q18: Common scalability mistake?  
**A:** Scaling everything instead of bottlenecks.

---

### ❓ Q19: Scalability vs reliability?  
**A:** Overloaded systems reduce reliability.

---

### ❓ Q20: One-line summary?  
**A:** Scale the right components at the right time for efficient growth.

---

# ✅ Final Summary

Scalability is not about adding more infrastructure blindly.  
It is about:
- Understanding system limits  
- Identifying bottlenecks  
- Scaling selectively  
- Balancing cost, performance, and reliability  
