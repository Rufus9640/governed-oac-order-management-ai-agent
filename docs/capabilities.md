# 📊 Capabilities — Governed OAC AI Agent

## 📌 Overview

This document defines the **actual capabilities of the AI agent based on tested behavior**, clearly separating:

- Supported capabilities  
- Partially supported capabilities  
- Unsupported capabilities  

This ensures transparency and avoids overclaiming functionality.

---

## ✅ Supported Capabilities

The following analytics are **reliably supported** using the current subject area and model:

### 📈 1. Sales Order Trends

- Trend analysis by:
  - Month  
  - Quarter  
  - Year  

**Examples:**
- Sales order trend for last 12 months  
- Monthly order volume trend  

---

### 📦 2. Quantity-Based Metrics

- QUANTITY_ORDERED  
- SHIPPED_QUANTITY  
- FULFILLED_QUANTITY  
- RETURNED_QUANTITY  

**Supported Analysis:**
- Trends  
- Comparisons  
- Breakdowns by dimension  

---

### 🚚 3. Shipment Activity

- On Time Shipment Lines Count  
- Late Shipment Lines Count  

**Supported Analysis:**
- Monthly trend  
- Quarterly trend  
- Comparison across categories or regions  

---

### ❌ 4. Cancellation and Unfulfilled Analysis

- CANCELLED_QUANTITY  
- UNFULFILLED_LINES  
- Cancelled Lines Amount  

**Supported Analysis:**
- Cancellation trends  
- Order type comparison  
- Category contribution  

---

### 💰 5. Sales and Amount-Based Metrics

- Sales Order Lines Amount  
- Order Discount Amount  
- Cancelled Lines Amount  
- Yearly Sales Amount  

---

### 🧾 6. Dimensional Analysis

Supported breakdowns:

- Product Category  
- Customer  
- Country / City  
- Line of Business  
- Order Type  
- Order Status  
- Source Order System  
- Ledger  

---

## ⚠️ Partially Supported Capabilities

These capabilities are **understood by the agent but not always reliable in execution**.

---

### ⚠️ 1. Order Fulfillment Rate

- KPI is recognized  
- May return **“No Data Found”** in some queries  

---

### ⚠️ 2. Order Shipment Cycle Time

- Measure exists in subject area  
- Query execution errors observed  

---

### ⚠️ 3. Delay-Based Customer Impact

- Requires strict use of:
  - Late Shipment Lines Count  
- Incorrect metric usage may lead to inconsistent results  

---

### ⚠️ 4. Formula-Based KPI Execution

KPI formulas from the knowledge document:

- Are understood  
- Work in controlled scenarios  
- Depend on:
  - Required columns existing  
  - Query execution success  

---

## ❌ Unsupported Capabilities

The agent is explicitly governed to **reject these topics**.

---

### 🚫 Business Areas Not Supported

- Supplier performance  
- Customer profitability  
- Warehouse labor efficiency  
- Forecast accuracy  
- Transportation efficiency  

---

### 🚫 Root Cause Analysis

The agent does NOT support:

- Labor issue attribution  
- Supplier delay attribution  
- Logistics or transportation causality  

---

### 🚫 Unsupported KPIs

If required fields are missing, the agent must:

1. Reject the KPI  
2. Explain limitation  
3. Suggest alternative  

Examples:

- Revenue Leakage %  
- Discount Depth %  
- Order Backlog Value  

---

## 📊 Supported Measures (Production-Safe)

These are the most stable and reliable measures:

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
- Yearly Sales Amount  

---

## 🧮 Conditionally Supported KPIs (RAG-Based)

These KPIs are defined in the knowledge document and used only when valid:

- Average Order Value (AOV)  
- Fill Rate %  
- Order Cancellation Rate  
- Repeat Order Rate  
- Late Shipment Rate  
- Cancellation Value Impact %  
- Return Rate %  
- Order Cycle Time  

---

### ⚠️ Important Rule

> A KPI is supported ONLY if all required source columns exist in the active subject area.

---

## 💬 Supported Prompt Examples

### 📈 Trends

- Sales order trend for the last 12 months  
- Show yearly sales amount by ledger  

---

### 📦 Category Analysis

- Which product categories contribute most to unfulfilled lines  
- Compare sales amount by product category  

---

### 🚚 Shipment Analysis

- Show Late Shipment Lines Count by quarter  
- Show On Time Shipment Lines Count by month  

---

### ❌ Cancellation Analysis

- How do cancellations vary by order type  
- Show cancelled quantity by product category  

---

### 🧮 KPI-Based

- Show Average Order Value by month  
- Show Fill Rate % by product category  

---

## 🔍 Key Takeaway

This AI agent is designed to:

- Deliver **accurate, model-driven analytics**  
- Enforce **strict KPI validation rules**  
- Prevent **unsupported or misleading insights**  

It prioritizes:

> **Accuracy, governance, and transparency over completeness.**
