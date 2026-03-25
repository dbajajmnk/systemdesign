# 📘 Understanding Requirements and Problem Framing (System Design)

---

## 1️⃣ Clarifying Vague Requirements

### ✅ What
Clarifying vague requirements means converting unclear, high-level problem statements into precise, actionable, and testable requirements.

### 🎯 Why
- Prevents building the wrong system
- Reduces ambiguity across teams
- Enables better architecture

### ⏰ When
- At the start of design
- During stakeholder discussions

### 🌍 Real-Life Analogy
Ordering food clearly vs vaguely

### ⚙️ How
- Ask structured questions
- Define functional & non-functional requirements
- Identify constraints
- Validate assumptions

---

## 2️⃣ Identifying System Boundaries

### ✅ What
Defines what is inside vs outside the system.

### 🎯 Why
- Avoids over-engineering
- Defines ownership

### ⏰ When
- After requirement clarity

### 🌍 Real-Life Analogy
Food app vs payment/maps

### ⚙️ How
- Identify internal components
- Identify external systems
- Define integrations

---

## 3️⃣ User Flows and Responsibilities

### ✅ What
Step-by-step system interaction

### 🎯 Why
- Ensures completeness
- Defines responsibilities

### ⏰ When
- Before detailed design

### 🌍 Real-Life Analogy
Cab booking flow

### ⚙️ How
- Map steps
- Assign roles
- Handle edge cases

---

## 4️⃣ Success & Failure Criteria

### ✅ What
Defines measurable outcomes

### 🎯 Why
- Ensures reliability

### ⏰ When
- During design

### 🌍 Real-Life Analogy
ATM success/failure

### ⚙️ How
- Define metrics
- Plan failure handling

---

# 🧠 Subjective Questions with Answers

---

### 1. Explain requirement clarification with examples  
**Answer:**  
Requirement clarification is the process of converting vague statements into clear, structured requirements.  
Example:  
“Build a chat app” →  
- 1:1 or group chat?  
- Real-time or async?  
- File sharing needed?  

---

### 2. Functional vs non-functional requirements  
**Answer:**  
- Functional → What system does (login, send message)  
- Non-functional → How system performs (latency, scalability)  

---

### 3. Approach vague requirements in interviews  
**Answer:**  
- Ask clarifying questions  
- Define assumptions  
- Break into features  
- Confirm scope  

---

### 4. Define system boundaries  
**Answer:**  
System boundaries define what components are part of the system and what is external.  

---

### 5. Internal vs external systems  
**Answer:**  
- Internal → APIs, DB, services  
- External → payment gateway, third-party APIs  

---

### 6. Importance of boundaries  
**Answer:**  
- Avoids over-design  
- Defines ownership  
- Improves clarity  

---

### 7. Explain user flows  
**Answer:**  
User flows are step-by-step interactions between user and system components.

---

### 8. Responsibility mapping importance  
**Answer:**  
Ensures each component has a clear role and avoids overlap or confusion.

---

### 9. Design user flow for chat system  
**Answer:**  
User → Frontend → API → Message Service → DB → Notification → Receiver  

---

### 10. What are edge cases?  
**Answer:**  
Unusual scenarios like failures, timeouts, invalid input.

---

### 11. Define success criteria  
**Answer:**  
Metrics like latency, uptime, and accuracy that define system success.

---

### 12. Explain failure scenarios  
**Answer:**  
Cases where system fails like timeout, crash, partial failure.

---

### 13. SLA vs SLO  
**Answer:**  
- SLA → Agreement with users  
- SLO → Internal performance target  

---

### 14. Retry vs fallback  
**Answer:**  
- Retry → Try again  
- Fallback → Alternate solution  

---

### 15. Measuring system performance  
**Answer:**  
Using metrics like latency, throughput, error rate.

---

### 16. Requirement gathering mistakes  
**Answer:**  
- Not asking questions  
- Assuming requirements  
- Ignoring edge cases  

---

### 17. Requirement validation  
**Answer:**  
Confirming requirements with stakeholders before implementation.

---

### 18. Flow vs reliability  
**Answer:**  
Better flows ensure fewer failures and improved reliability.

---

### 19. Design requirement framework  
**Answer:**  
- Define features  
- Define constraints  
- Define scale  
- Validate  

---

### 20. End-to-end system thinking  
**Answer:**  
Understanding the complete flow from user action to system response including failures.

---

# 🚀 Summary
