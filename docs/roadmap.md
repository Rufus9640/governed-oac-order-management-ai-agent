# 🛣️ Roadmap — Governed OAC AI Agent

## Overview

This document outlines the **planned enhancements and future improvements** for the Governed Order Management Insights AI Agent.

The roadmap focuses on improving:

- KPI reliability  
- Semantic model coverage  
- Governance strength  
- Query accuracy and stability  
- Overall usability and analytical depth  

---

## 1. KPI Stabilization

### Objective
Improve reliability and execution consistency of KPI-based queries.

### Focus Areas

- Stabilize:
  - Order Fulfillment Rate  
  - Order Shipment Cycle Time  

- Improve execution success for:
  - Average Order Value (AOV)  
  - Fill Rate %  
  - Repeat Order Rate  

### Approach

- Validate field mappings in the semantic model  
- Align KPI formulas with model structure  
- Test KPI queries across multiple dimensional breakdowns  

---

## 2. Semantic Model Enhancements

### Objective
Expand and strengthen the underlying subject area.

### Focus Areas

- Ensure all required fields for KPI calculations are present  
- Improve consistency of joins across dimensions  
- Validate field naming and identifiers  

### Potential Additions

- Additional shipment timing attributes  
- Enhanced order status classification  
- Extended customer segmentation fields  

---

## 3. Advanced KPI Support

### Objective
Enable more complex and business-relevant KPI calculations.

### Focus Areas

- Support multi-step KPI calculations where feasible  
- Improve repeat-order detection logic  
- Enhance time-based KPI computations  

### Constraint

All KPIs will continue to follow strict validation rules:
- No calculation without required fields  
- No inferred or fabricated mappings  

---

## 4. Governance Strengthening

### Objective
Further improve control over unsupported or ambiguous queries.

### Focus Areas

- Expand unsupported-topic detection  
- Improve rejection messaging clarity  
- Strengthen prevention of speculative responses  

### Enhancements

- More explicit rule coverage in Supplemental Instructions  
- Improved alignment with knowledge document constraints  

---

## 5. Query Interpretation Improvements

### Objective
Enhance the agent’s ability to interpret user intent accurately.

### Focus Areas

- Better handling of shorthand prompts  
- Improved ambiguity detection  
- More consistent metric selection  

### Enhancements

- Refined intent classification rules  
- Controlled synonym mapping for business terms  

---

## 6. Validation Layer Enhancements

### Objective
Introduce stronger pre-execution validation.

### Focus Areas

- Validate required fields before query execution  
- Detect unsupported KPI requests early  
- Provide proactive user guidance  

---

## 7. Performance and Reliability

### Objective
Improve overall system stability.

### Focus Areas

- Reduce query execution failures  
- Improve response consistency  
- Optimize performance for larger datasets  

---

## 8. User Experience Improvements

### Objective
Enhance usability for business users.

### Focus Areas

- More intuitive response explanations  
- Clearer KPI definitions in responses  
- Improved visualization recommendations  

---

## 9. Documentation and Demo Enhancements

### Objective
Improve clarity and usability of project documentation.

### Focus Areas

- Add architecture diagrams  
- Include sample outputs and screenshots  
- Expand demo scenarios  

---

## Key Direction

The long-term goal of this project is to evolve the system into a:

> **Fully governed, reliable, and scalable natural-language analytics layer for enterprise reporting in Oracle Analytics Cloud.**
