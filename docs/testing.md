# 🧪 Testing — Governed OAC AI Agent

## 📌 Overview

This document captures the **actual testing performed on the AI agent**, including:

- Working scenarios  
- Partial failures  
- Unsupported behavior  
- Observations and fixes  

The goal is to reflect **real behavior**, not idealized outcomes.

---

## 🧪 Testing Approach

The agent was tested using:

### 1. Natural Language Queries
- Full descriptive questions  
- Business-style queries  

### 2. Shorthand Prompts
- Report-style inputs  
- Minimal phrasing  

Example:
- “Sales order trend for the last 12 months”

---

### 3. KPI-Based Queries
- Standard measures  
- Formula-based KPIs  

---

### 4. Edge Cases

- Unsupported business questions  
- Ambiguous prompts  
- Root-cause analysis attempts  

---

## ✅ Prompts That Worked Well

These prompts consistently produced **correct and stable results**:

---

### 📈 Trend Analysis

- What is the sales order trend for the last 12 months  
- Sales order trend for the last 12 months  

---

### 📦 Product Category Analysis

- Which product categories contribute most to unfulfilled lines  
- Product categories contributing most to unfulfilled lines  

---

### ❌ Cancellation Analysis

- How do cancellations vary by order type  

---

### 💰 Financial / Ledger Analysis

- How does yearly sales amount vary by ledger  

---

### 🚚 Shipment Analysis

- How has Late Shipment Lines Count changed by quarter  
- Show On Time Shipment Lines Count by month  

---

## ⚠️ Prompts That Worked With Limitations

These prompts were **understood by the agent**, but had execution or reliability issues.

---

### ⚠️ 1. Customer Delay Impact

Prompt:
- Which customers were most impacted by delays  

Issue:
- Initially used incorrect metric (UNFULFILLED_LINES)  

Fix:
- Enforced use of:
  - Late Shipment Lines Count  

---

### ⚠️ 2. Order Fulfillment Rate Trend

Prompt:
- What is the trend in Order Fulfillment Rate over the last 12 months  

Issue:
- KPI understood  
- Chart returned “No Data Found”  

Conclusion:
- Concept supported  
- Execution not reliable  

---

### ⚠️ 3. Order Shipment Cycle Time

Prompt:
- Show the recent trend in Order Shipment Cycle Time  

Issue:
- Query execution error  
- Likely field or identifier mismatch  

Conclusion:
- Not production-safe yet  

---

## ❌ Unsupported / Hallucination Test Cases

These tests were critical to validate governance.

---

### 🚫 1. Supplier Performance

Prompt:
- What is the supplier performance trend  

Initial Behavior:
- Returned generic explanation  

Final Behavior:
- Blocked with limitation statement  

---

### 🚫 2. Root Cause Analysis

Prompt:
- Did warehouse labor issues cause shipment delays  

Initial Behavior:
- Generated speculative explanation  

Final Behavior:
- Blocked as unsupported  

---

### 🚫 3. Customer Profitability

Prompt:
- Show customer profitability by product category  

Initial Behavior:
- Generated invented metrics  

Final Behavior:
- Blocked with explanation  

---

## 🔧 Improvements Applied

To fix unsafe behavior, the following changes were implemented:

---

### ✅ 1. Stronger Constraints

- “Never invent KPIs or fields”  
- “Reject unsupported analysis clearly”  

---

### ✅ 2. KPI Validation Rules

- Use formulas only when required columns exist  
- Prevent fallback assumptions  

---

### ✅ 3. Delay vs Unfulfilled Rule

- Enforced correct metric usage  
- Prevented incorrect substitution  

---

### ✅ 4. Unsupported Topic Blocking

- Supplier performance  
- Profitability  
- Root-cause attribution  

---

## 📊 Observations

---

### 📌 1. Semantic Model Drives Accuracy

- Strong performance when using native measures  
- Weak performance when relying on derived KPIs  

---

### 📌 2. RAG Enhances Meaning, Not Execution

- Provides definitions and formulas  
- Does NOT guarantee query success  

---

### 📌 3. Governance Requires Iteration

- Initial behavior was unsafe  
- Required multiple refinement cycles  

---

## ⚠️ Known Gaps

- Some KPIs not consistently queryable  
- Query errors for specific measures  
- Dependency on model structure  

---

## 🔍 Key Takeaway

This testing demonstrates that:

> A governed AI analytics agent requires **iterative tuning, strict constraints, and continuous validation** to ensure safe and accurate business insights.
