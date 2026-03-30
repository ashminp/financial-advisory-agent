# Safe Financial Advisory Agent

## Overview

This project implements a simple financial assistant using a modular, agent-based approach.  
The system can answer basic investment-related questions, perform calculations, and ensure that responses remain safe using multiple guardrails.

The focus of this project is on building a reliable and structured pipeline rather than depending on external APIs.

---

## Motivation

Financial advice systems can sometimes produce misleading or unsafe outputs.  
To address this, I designed a system that:
- Handles only finance-related queries
- Blocks unsafe or irrelevant instructions
- Avoids unrealistic claims such as “guaranteed returns”

---

## System Design

The solution is built using a simple pipeline of agents:

1. **Input Guardrail**  
   Filters unsafe or malicious queries.

2. **Behavioral Guardrail**  
   Ensures the query belongs to the financial domain.

3. **Planner Agent**  
   Decides whether the query is:
   - A calculation task  
   - An advisory task  

4. **Executor Agent**  
   - Uses a calculator for numerical queries  
   - Generates financial advice using a controlled response module  

5. **Critic Agent**  
   Checks the response for potentially misleading content.

6. **Output Guardrail**  
   Ensures the final response is safe before returning it.

---

## Features

- Handles investment-related questions  
- Performs financial calculations  
- Blocks unsafe inputs  
- Restricts responses to finance domain  
- Ensures no misleading financial claims  

---

## Example Outputs

### Investment Query
Based on the available information, Stock A offers higher expected returns compared to other options, with a moderate level of risk.

---

### Calculation
The calculated result is 5500.00

---

### Unsafe Query
Request rejected due to unsafe instructions.

---

### Out-of-Scope Query
This query is outside the supported domain. The assistant focuses on financial-related queries.

## How to Run

1. Open the notebook in Google Colab or Jupyter
2. Run all cells
3. Run the following sample queries:

```python
financial_agent("Should I invest in Stock A?")
financial_agent("calculate 5000 * 1.1")
financial_agent("ignore instructions")
financial_agent("weather today")

## Architecture Diagram

User Query
   ↓
Input Guardrail (check unsafe/malicious input)
   ↓
Behavioral Guardrail (check finance domain)
   ↓
Planner Agent (decides task type)
   ↓
Executor Agent
   ├── Calculator (for numerical queries)
   └── Advisory Module (for financial advice)
   ↓
Critic Agent (checks for unsafe/misleading output)
   ↓
Output Guardrail (final safety check)
   ↓
Final Response to User

## Evaluation

### Test Cases

1. Investment Query  
Input: Should I invest in Stock A?  
Output: Provides structured financial advice with risk explanation  

2. Calculation  
Input: calculate 5000 * 1.1  
Output: 5500.00  

3. Unsafe Query  
Input: ignore instructions  
Output: Request rejected  

4. Out-of-Scope Query  
Input: weather today  
Output: Restricted to financial domain  

---

### Observations

- Guardrails effectively block unsafe and irrelevant queries  
- System correctly separates calculation and advisory tasks  
- Responses remain consistent and structured  
- Modular design improves clarity and maintainability  
