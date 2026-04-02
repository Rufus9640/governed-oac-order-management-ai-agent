# 🏗️ Architecture — Governed OAC AI Agent

## 📌 Overview

This project implements a **governed AI analytics agent** in Oracle Analytics Cloud (OAC) using a layered architecture that ensures:

- Accurate, model-driven analysis  
- Controlled KPI usage  
- No hallucinated metrics or joins  
- Clear handling of unsupported requests  

The architecture combines:

1. Semantic Model (Subject Area)
2. Supplemental Instructions (Control Layer)
3. Knowledge Document (RAG Layer)
4. AI Agent Interface

---

## 🔷 1. Subject Area (Semantic Model Layer)

The **subject area is the foundation** of the entire system.

### Source
Fusion SCM Sales Order custom subject area

### Contains

- Measures:
  - QUANTITY_ORDERED  
  - SHIPPED_QUANTITY  
  - FULFILLED_QUANTITY  
  - RETURNED_QUANTITY  
  - UNFULFILLED_LINES  
  - CANCELLED_QUANTITY  
  - Sales Order Lines Amount  
  - Order Discount Amount  
  - Cancelled Lines Amount  
  - On Time Shipment Lines Count  
  - Late Shipment Lines Count  
  - Order Shipment Cycle Time  
  - Order Fulfillment Rate  
  - Yearly Sales Amount  

- Dimensions:
  - Customer, Account, City, Country  
  - Product Category  
  - Order Type, Status, Source System  
  - Ledger  

---

### ✅ Key Principle

> The agent ONLY uses data that exists in the subject area.

---

### ❌ The Agent Does NOT

- Create new fields  
- Modify the semantic model  
- Add permanent calculations  
- Persist new KPIs in workbooks  

---

## 🔷 2. Supplemental Instructions (Control Layer)

This is the **governance and behavior layer** of the system.

### Responsibilities

- Interpret user intent  
- Route queries to correct subject area  
- Enforce KPI rules  
- Prevent hallucinations  
- Control response structure  

---

### 🔒 Key Constraints Enforced

- Never invent fields, KPIs, joins, or calculations  
- Use formulas only if required columns exist  
- Do not assume relationships unless supported  
- Reject unsupported business questions clearly  
- Ask clarifying questions when needed  

---

### 📊 Output Structure Enforced

Every response follows:

1. Subject Area Used  
2. KPI or Measure Used  
3. Executive Summary  
4. Supporting Metrics / Formula Logic  
5. Breakdown by Dimensions  
6. Recommended Visualization  
7. Recommended Next Action  

---

## 🔷 3. Knowledge Document (RAG Layer)

The knowledge document is used through **Retrieval-Augmented Generation (RAG)**.

### Purpose

- Provide KPI definitions  
- Provide approved formulas  
- Define business glossary  
- Enforce supported/unsupported scope  
- Guide interpretation  

---

### 📌 Important Design Principle

> The knowledge document is a **reference layer**, not a calculation layer.

---

## 🔷 What RAG DOES

- Supplies:
  - KPI definitions  
  - Formula logic  
  - Business interpretation rules  
  - Governance rules  

- Enables:
  - Dynamic KPI calculation at query time  

---

## 🔷 What RAG DOES NOT DO

- ❌ Does NOT create measures  
- ❌ Does NOT store calculations  
- ❌ Does NOT modify the semantic model  
- ❌ Does NOT guarantee query execution  

---

## 🧮 Formula Application Model

KPI formulas are retrieved from the knowledge document and applied **only when valid**.

---

### Example 1: Ordered Quantity Index
SUM(QUANTITY_ORDERED) / 100

Execution:

1. Formula retrieved from knowledge document  
2. QUANTITY_ORDERED fetched from subject area  
3. Formula applied at query time  
4. Result visualized  

---

### Example 2: Execution Quantity Score
SUM(SHIPPED_QUANTITY) + SUM(FULFILLED_QUANTITY)

Execution:

1. Formula retrieved from knowledge document  
2. SHIPPED_QUANTITY and FULFILLED_QUANTITY retrieved  
3. Formula applied dynamically  
4. Chart + summary generated  

---

### ⚠️ Important Clarification

> These formulas are NOT stored as workbook calculations or semantic model measures.

---

## 🔷 4. Runtime Flow

The system operates as follows:

1. User submits natural-language query  
2. Agent identifies business intent  
3. Supplemental Instructions validate request  
4. Subject area is queried  
5. Knowledge document is retrieved (if needed)  
6. KPI formula applied (if supported)  
7. Response generated with metrics + visualization  

---

## 🔷 Governance Model

This project is built around **strict governance principles**:

### Supported Analysis

- Must use available subject-area fields  
- Must follow approved KPI mappings  
- Must use valid joins  

---

### Unsupported Analysis Handling

If a request is not supported:

1. Clearly state limitation  
2. Do NOT generate fake analysis  
3. Suggest closest valid alternative  

---

## 🔷 Key Takeaway

This architecture ensures that the AI agent behaves as a:

> **Governed analytics system**, not a free-form generative chatbot.

It balances:

- Natural language flexibility  
- Semantic model accuracy  
- KPI validation  
- Business-safe responses  
