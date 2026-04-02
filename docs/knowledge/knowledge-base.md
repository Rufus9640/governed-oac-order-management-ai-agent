# Knowledge Base (Order Management KPI Reference)

## 🎯 Purpose

Defines business KPIs, formulas, and interpretation logic used by the AI Agent.

This document supports RAG-based responses in Oracle Analytics Cloud.

---

## 📊 Subject Area

Primary:
- DW_Sales_Order_Custom_Fact

---

## 📈 KPI Definitions

### 1. Average Order Value (AOV)

**Formula:**
SUM(Sales Order Lines Amount) / COUNT DISTINCT(ORDER_NUMBER)

**Meaning:**
Average revenue per order

---

### 2. Fill Rate %

**Formula:**
SUM(SHIPPED_QUANTITY) / SUM(QUANTITY_ORDERED) * 100

**Meaning:**
Fulfillment efficiency

---

### 3. Order Cancellation Rate

**Formula:**
Cancelled Orders / Total Orders * 100

**Preferred Field:**
CANCELLED_INDICATOR

---

### 4. Repeat Order Rate

**Formula:**
Customers with >1 order / Total Customers

**Key Fields:**
- PARTY_NUMBER  
- ORDER_NUMBER  
- ORDER_DATE  

---

### 5. Late Shipment Rate

**Formula:**
Late / (Late + On-Time)

---

### 6. Cancellation Value Impact %

**Formula:**
Cancelled Amount / Total Amount

---

### 7. Return Rate %

**Formula:**
RETURNED_QUANTITY / SHIPPED_QUANTITY

---

### 8. Order Cycle Time

**Definition:**
Use Order Shipment Cycle Time (model measure)

---

## ⚠️ KPI Support Rule

A KPI is valid only if:
- All required fields exist  
- Mapping is explicitly defined  

Otherwise:
- Reject KPI  
- Suggest closest alternative  

---

## 📊 Business Interpretation

| Pattern | Meaning |
|--------|--------|
| Upward Trend | Demand growth |
| Downward Trend | Decline or constraints |
| Spike | Event / anomaly |
| High Cancellation | Instability |
| High Return Rate | Product issues |
| High Late Shipments | Operational delays |

---

## 🚫 Unsupported KPIs

- Revenue Leakage %  
- Discount Depth %  
- Order Backlog Value  

---

## 📌 Important Rule

Never:
- Invent fields  
- Assume joins  
- Derive unsupported KPIs  

---

## 🧠 Role in AI Agent

This document enables:
- KPI computation via RAG  
- Business interpretation  
- Governance enforcement  
