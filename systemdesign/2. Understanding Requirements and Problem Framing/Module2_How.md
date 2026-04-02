# 📘 Understanding Requirements & Problem Framing (Online Boutique System)

---

# 🧠 1️⃣ HOW to Clarify Requirements

---

## 🎯 Goal
Convert vague boutique idea → clear requirements

---

## ⚙️ Step-by-Step

### Step 1: Ask Questions
- Who are users? → Customers, Admin  
- Platform? → Mobile/Web  
- Features? → Browse, Cart, Order, Payment  

---

### Step 2: Define Functional Requirements

Customer:
- Browse products  
- Filter (size, color, price)  
- Add to cart  
- Place order  
- Track orders  

Admin:
- Manage products  
- Manage inventory  
- Manage orders  

---

### Step 3: Define Non-Functional Requirements

- Product page < 500ms  
- Checkout < 2 sec  
- High availability  
- Secure payments  

---

### Step 4: Identify Constraints

- No multi-vendor  
- Domestic shipping only  

---

### Step 5: Make Assumptions

- Mobile-first users  
- Moderate traffic  

---

### Step 6: Validate Requirements

Confirm:
“Does system include cart, payment, and order tracking?”

---

## 🧰 Tools
- Notion / Confluence → Requirement docs  
- Jira / Trello → Task tracking  

---

## 🖼️ Mind Mapping (Requirement Tools)


::contentReference[oaicite:0]{index=0}


---

# 🧠 2️⃣ HOW to Define System Boundaries

---

## 🎯 Goal
Define internal vs external systems

---

## ⚙️ Step-by-Step

### Step 1: Internal Services
- Catalog  
- Cart  
- Order  
- Inventory  

---

### Step 2: External Systems
- Payment Gateway  
- Email/SMS  

---

### Step 3: Flow

User → App → Backend → Payment Gateway  

---

### Step 4: Interfaces
- REST APIs  
- Payment Webhooks  

---

### Step 5: Avoid Over-Engineering
Use external services instead of building everything  

---

## 🧰 Tools
- draw.io / Excalidraw → Architecture diagrams  
- Postman → API testing  

---

## 🖼️ Mind Mapping (Architecture Tools)


::contentReference[oaicite:1]{index=1}


---

# 🧠 3️⃣ HOW to Design User Flow

---

## 🎯 Goal
Understand full user journey

---

## ⚙️ Step-by-Step

### Step 1: Start with Action
User clicks “Buy Now”

---

### Step 2: Flow

User → Browse → Cart → Checkout → Payment → Order  

---

### Step 3: Breakdown

1. Select product  
2. Add to cart  
3. Checkout  
4. Payment  
5. Order confirmation  

---

### Step 4: Responsibilities

- Frontend → UI  
- API → Validation  
- Order Service → Order logic  
- Payment → Payment processing  

---

### Step 5: Edge Cases

- Payment failure  
- Out-of-stock  
- Duplicate orders  
- Network failure  

---

### Step 6: States

- Created  
- Paid  
- Shipped  
- Delivered  
- Cancelled  

---

## 🧰 Tools
- Figma → Flow design  
- Miro → Journey mapping  
- Whimsical → Flowcharts  
- Mermaid → Sequence diagrams  

---

## 🖼️ Mind Mapping (Flow Tools)


::contentReference[oaicite:2]{index=2}


---

# 🧠 4️⃣ HOW to Define Success & Failure

---

## 🎯 Goal
Ensure reliability and performance

---

## ⚙️ Step-by-Step

### Step 1: Success Metrics
- Page load < 500ms  
- Checkout < 2 sec  
- 99.9% uptime  

---

### Step 2: Failure Scenarios
- Payment failure  
- Inventory mismatch  
- Server crash  

---

### Step 3: Handling Strategies

- Retry → Payment retry  
- Fallback → Alternative option  
- Queue → Async processing  
- Cache → Serve product data  

---

### Step 4: Monitoring

Track:
- Orders/min  
- Failed payments  
- API latency  

---

### Step 5: Graceful Degradation

If payment fails → allow retry  

---

## 🧰 Tools
- Grafana → Dashboards  
- Prometheus → Metrics  
- Datadog → Monitoring  
- ELK Stack → Logging  
- k6 → Load testing  

---

## 🖼️ Mind Mapping (Monitoring Tools)


::contentReference[oaicite:3]{index=3}


---

# 🧠 MCQ (Knowledge Check)

---

1. First step in system design?  
A. Coding  
B. Clarifying requirements  
C. Deployment  
D. Testing  
Answer: B  

---

2. External system example?  
A. Cart  
B. Order  
C. Payment Gateway  
D. Catalog  
Answer: C  

---

3. Non-functional requirement?  
A. Add to cart  
B. Browse  
C. Response time  
D. Login  
Answer: C  

---

4. API testing tool?  
A. Figma  
B. Postman  
C. Jira  
D. Notion  
Answer: B  

---

5. Edge case example?  
A. Login  
B. Payment failure  
C. UI  
D. Browsing  
Answer: B  

---

6. Monitoring tool?  
A. Trello  
B. Grafana  
C. Figma  
D. Swagger  
Answer: B  

---

7. User flow step?  
A. Scaling  
B. Checkout  
C. Logging  
D. Deployment  
Answer: B  

---

8. Internal system example?  
A. Stripe  
B. Payment gateway  
C. Order service  
D. Email provider  
Answer: C  

---

9. Diagram tool?  
A. draw.io  
B. Postman  
C. k6  
D. Jira  
Answer: A  

---

10. Failure handling strategy?  
A. Ignore  
B. Retry  
C. Skip  
D. Delete  
Answer: B  

---

# 🧠 Subjective Questions with Answers

---

### 1. How to clarify boutique requirements?  
Answer:  
Ask about users, features, platform, and validate scope before design.  

---

### 2. Define system boundaries  
Answer:  
Internal: catalog, orders  
External: payment gateway  

---

### 3. Explain user flow  
Answer:  
Browse → Cart → Checkout → Payment → Order  

---

### 4. What are edge cases?  
Answer:  
Payment failure, stock issues  

---

### 5. Why define non-functional requirements?  
Answer:  
To ensure performance and scalability  

---

### 6. Explain monitoring  
Answer:  
Tracking system performance metrics  

---

### 7. Why avoid over-engineering?  
Answer:  
To reduce complexity and focus on core system  

---

### 8. How to handle failures?  
Answer:  
Retry, fallback, queue, caching  

---

### 9. Role of tools?  
Answer:  
They help structure and visualize system design  

---

### 10. End-to-end thinking?  
Answer:  
Understanding full journey from user to system response  

---

# 🚀 FINAL SUMMARY

- Clarify before designing  
- Define boundaries clearly  
- Design full user flow  
- Handle failures early  
- Use tools effectively  

