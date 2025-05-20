# Phase II

## 📝 Business Process Modeling: HOOF-CARE – Horse Health & Performance Tracking

This phase focuses on **visualizing the business process** of the HOOF-CARE Management Information System (MIS) using a **BPMN swimlane diagram**. It maps how health, training, and race participation data flows between key stakeholders and systems to support better decision-making in horse racing.

---

## 📌 Scope Definition

**Business Process:** Racehorse Health and Performance Monitoring

**Relevance to MIS:**  
The process ensures real-time collection and use of critical data (health status, training logs, race results), enabling trainers, veterinarians, and race organizers to make informed, data-driven decisions.

**Objectives:**
- Accurately log and track training sessions and health checks.
- Automatically analyze horse readiness for racing events.
- Approve or restrict race participation based on real-time insights.

**Expected Outcomes:**
- Safer race conditions through medical oversight.
- Improved race preparation strategies.
- Transparent communication between all stakeholders.

---

## 🧍‍ Entities and Roles

| Entity            | Role & Responsibilities                                                   |
|-------------------|----------------------------------------------------------------------------|
| **Trainer**        | Logs training data and monitors performance trends.                      |
| **Veterinarian**   | Performs health checks and updates medical records.                      |
| **Horse Owner**    | Monitors horse status and gets notified of approvals/restrictions.       |
| **Race Organizer** | Decides race eligibility based on health and training reports.           |
| **Betting Agency** | (Limited access) Uses race history for odds and analysis.                |
| **HOOF-CARE System** | Central system that stores and processes all data interactions.        |

---

## 🏊 BPMN Swimlane Diagram

![BPMN Diagram](A_UML_Business_Process_Model_and_Notation_(BPMN)_d.png)

> **Legend**:  
> • **Ovals**: Start/End  
> • **Rectangles**: Activities  
> • **Diamonds**: Decisions  
> • **Swimlanes**: Entities/Actors  

---

## 🔄 Process Flow Summary

1. **Trainer** initiates a training session and logs performance.
2. **Veterinarian** performs a health check and logs results.
3. The **HOOF-CARE System** analyzes inputs.
4. If the horse is **fit**, the **Race Organizer** is notified for race approval.
5. If **unfit**, the **Horse Owner** receives restriction notice.
6. **Betting Agency** receives race event data once approved.
7. All records are stored centrally for reporting and decision support.

---

## 📌 Status

✅ Phase II Complete – Business process modeled and explained using BPMN.



