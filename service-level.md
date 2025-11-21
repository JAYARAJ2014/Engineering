# 🔧 Understanding SLA, SLO, SLI, and Error Budgets  
A Practical Guide for Engineering Teams

---

# ⭐ 1. SLI — Service Level Indicator  
**What it is:**  
A *measurement* of how the system is performing.

**Examples:**  
- Availability: `99.2%`  
- Latency: `95% of requests < 200ms`  
- Error rate: `0.5%`  
- Throughput: `300 requests/sec`

**SLI = Actual observed performance**

---

# ⭐ 2. SLO — Service Level Objective  
**What it is:**  
A *target* or *goal* for service reliability.

**Examples:**  
- Availability should be **99.9%** over 30 days  
- **99%** of requests respond under **250ms**  
- Error rate below **1%**

**SLO = Target performance**

---

# ⭐ 3. SLA — Service Level Agreement  
**What it is:**  
A customer-facing *contract* that includes:  
- A guaranteed SLO  
- Penalties if it's not met (refunds, credits)

**Example:**  
- Uptime must be **99.9%** per month  
- If not met → **10% service credit**

**SLA = SLO + penalties**

---

# 🧩 Summary Table

| Term | Meaning | Example |
|------|---------|---------|
| **SLI** | Actual measurement | “Latency = 180ms” |
| **SLO** | Target | “Latency < 250ms (99%)” |
| **SLA** | Contract w/ penalties | “If uptime < 99.9%, issue credits” |

---

# 🍕 Analogy (Easy to Remember)

**Pizza delivery service:**

- **SLI:** Actual delivery time = 28 minutes  
- **SLO:** Goal = Deliver within 30 minutes (95% of the time)  
- **SLA:** If > 30 minutes → pizza is free  

---

# ⭐ 4. Error Budgets — The Most Important SRE Concept  
**Error Budget = 100% – SLO**

If SLO is **99.9%** availability, then error budget = **0.1% downtime allowed**.

This is the *maximum acceptable unreliability*.

### Example  
SLO: **99.9% uptime**  
Error budget: **0.1% downtime**  
Which equals **43 minutes per month**.

---

# 🎯 Why Error Budgets Matter

They balance:

**Innovation (speed)**  
vs.  
**Reliability (stability)**

### When error budget is *available*:
- OK to release  
- Take risks  
- Move quickly  

### When error budget is *burned*:
- Release freeze  
- Focus on stability  
- Fix root causes  
- Improve observability/performance  

---

# 🧮 Example (Microservice)

SLO: **99.95% availability monthly**  
Error budget: **0.05% downtime**  
= **21.6 minutes** allowable downtime per month.

If you already had **20 minutes** of downtime:  
→ Only **1.6 minutes** left  
→ **Freeze deployments**  
→ Focus on reliability work  

---

# 🛠️ How to Choose Good SLOs

### 1. Pick what users care about
- Page loading → Availability  
- Speed → Latency  
- Correctness → Error rate  

### 2. Choose a window  
- 30 days  
- Last 7 days  
- Quarterly  

### 3. Select realistic targets  
Typical ranges:  
- Critical systems: **99.9–99.99%**  
- Normal services: **99–99.5%**

### 4. Alert on SLO burn rate  
(Not on CPU, memory, etc.)

---

# 📌 Definitions Recap

| Term | Definition |
|------|------------|
| **SLI** | Metric measuring system performance |
| **SLO** | Target level of performance |
| **SLA** | External contract with penalties |
| **Error Budget** | Allowed amount of failure |

---
