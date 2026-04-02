# ⚠️ Limitations — Governed OAC AI Agent

## Overview

This document outlines the **current limitations of the AI agent** based on observed behavior during testing.

The purpose is to provide **transparent and accurate expectations** regarding system capabilities, particularly for:

- KPI execution reliability  
- Query behavior  
- Model dependency  
- Governance boundaries  

---

## KPI Execution Limitations

### Conditional KPI Support

Several KPIs defined in the knowledge document are **conditionally supported** and depend on:

- Availability of required fields in the subject area  
- Correct semantic relationships  
- Successful query execution  

These include:

- Average Order Value (AOV)  
- Fill Rate %  
- Order Cancellation Rate  
- Repeat Order Rate  
- Late Shipment Rate  
- Cancellation Value Impact %  
- Return Rate %  
- Order Cycle Time  

---

### Execution Reliability

Even when a KPI is logically valid:

- Queries may return **“No Data Found”**  
- Execution errors may occur due to field or identifier mismatches  

---

## Semantic Model Dependency

The agent is fully dependent on the **active subject area**.

### Implications

- Only available fields and joins can be used  
- Missing fields prevent KPI execution  
- Incorrect mappings cannot be compensated dynamically  

---

## Formula Application Constraints

KPI formulas retrieved from the knowledge document are applied **only at query time**.

### Limitations

- Formulas are not persisted as reusable model measures  
- Each query must independently validate required fields  
- Complex multi-step calculations are limited by model structure  

---

## RAG (Knowledge Document) Limitations

The knowledge document enhances interpretation but does not guarantee execution.

### Important Distinction

- Provides:
  - KPI definitions  
  - Formula logic  
  - Business guidance  

- Does NOT:
  - Supply data  
  - Create measures  
  - Ensure query success  

---

## Unsupported Business Scope

The agent is intentionally restricted from answering certain types of business questions.

### Not Supported

- Supplier performance  
- Customer profitability  
- Warehouse labor efficiency  
- Forecast accuracy  
- Transportation cost efficiency  

---

## Root Cause Analysis Limitation

The agent does not support **causal inference or attribution analysis**.

### Examples

- Labor-related delay attribution  
- Supplier-driven delay explanations  
- Logistics or operational root-cause analysis  

---

## Query Behavior Limitations

### Ambiguity Handling

- Ambiguous queries require clarification  
- In some cases, interpretation may vary depending on phrasing  

---

### Metric Selection Sensitivity

Certain analyses require **strict metric selection**.

Example:

- Delay-related analysis must use:
  - Late Shipment Lines Count  

- Incorrect substitution (e.g., UNFULFILLED_LINES) leads to inaccurate results  

---

## Testing Observations

- Native subject-area measures are highly reliable  
- Derived KPI queries are less consistent  
- Query stability varies across measures  

---

## Future Improvement Areas

The following areas have been identified for enhancement:

- Stabilization of KPI query execution  
- Improved semantic model alignment  
- Better handling of complex KPI calculations  
- Enhanced validation before query execution  
- Stronger ambiguity resolution  

---

## Key Takeaway

This system is designed with a strong emphasis on governance.

> Accuracy, transparency, and controlled scope are prioritized over broad but unreliable analytical capabilities.
