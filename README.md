# Phase I

## 📄 Project Title: HOOF-CARE – A Horse Racing & Health Monitoring Database System

This repository contains the PowerPoint presentation for **Phase I** of the HOOF-CARE project, which models a Management Information System (MIS) focused on improving the health monitoring and race performance of horses.

---

## 🎯 Objective

To model a business process relevant to MIS by visualizing how information flows within the horse racing system. The goal is to enhance decision-making for trainers, veterinarians, and race organizers through structured data management and system interaction.

---

## 📋 Contents

- `Thurs_26858_Tresor_PLSQL.pptx`: PowerPoint presentation outlining the system overview, objectives, key entities, and benefits of the proposed solution.

---

## 👥 Target Users

- Horse Trainers  
- Veterinarians  
- Race Organizers  
- Betting Agencies  
- Horse Owners

---

## 🧩 Main Entities

- Horses  
- Health Records  
- Performance History  
- Race Events  
- Training Logs  
- Betting Insights

---

## 🛠️ Tools & Concepts

- Management Information Systems (MIS) principles  
- Business Process Modeling  
- Entity Identification  
- PowerPoint for visual presentation

---

## 📌 Status

✅ Phase I Complete – Presentation uploaded and ready for review.






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

![BPMN Diagram](https://github.com/Rugerot/THURS_Tresor_26858_pl_Assign/blob/main/hoofcare_bpmn.png)

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





# Phase III

## 🧩 Logical Model Design – HOOF-CARE MIS

This phase defines the logical data model for the HOOF-CARE Management Information System. It aligns with the problem definition in **Phase I** and the business process modeling in **Phase II**.

---

## 1️⃣ Entity-Relationship (ER) Model

### 🔹 Entities and Attributes

| **Entity**       | **Attributes** |
|------------------|----------------|
| **Horse**        | `HorseID (PK)`, `Name`, `Breed`, `DateOfBirth`, `OwnerID (FK)` |
| **Owner**        | `OwnerID (PK)`, `Name`, `ContactInfo` |
| **Trainer**      | `TrainerID (PK)`, `Name`, `ExperienceLevel`, `ContactInfo` |
| **Veterinarian** | `VetID (PK)`, `Name`, `Specialization`, `ContactInfo` |
| **TrainingLog**  | `TrainingID (PK)`, `HorseID (FK)`, `TrainerID (FK)`, `Date`, `Duration`, `PerformanceNotes` |
| **HealthRecord** | `RecordID (PK)`, `HorseID (FK)`, `VetID (FK)`, `Date`, `HealthStatus`, `MedicationGiven` |
| **RaceEvent**    | `EventID (PK)`, `EventName`, `Date`, `Location` |
| **Participation**| `ParticipationID (PK)`, `HorseID (FK)`, `EventID (FK)`, `Result`, `Rank`, `TimeCompleted` |
| **BettingInsight** | `InsightID (PK)`, `HorseID (FK)`, `EventID (FK)`, `Odds`, `Notes` |

---

## 2️⃣ Relationships & Constraints

### 🔗 Relationships

- **Horse ↔ Owner**: Many-to-One
- **Horse ↔ Trainer**: Many-to-Many via `TrainingLog`
- **Horse ↔ Veterinarian**: Many-to-Many via `HealthRecord`
- **Horse ↔ RaceEvent**: Many-to-Many via `Participation`
- **Horse ↔ BettingInsight**: Many-to-Many via `BettingInsight`

### ✅ Constraints

- `Horse.Name` → `NOT NULL`
- `TrainingLog.Duration` → `CHECK(Duration > 0)`
- `HealthRecord.HealthStatus` → `NOT NULL`
- `Participation.Result` → `DEFAULT 'Pending'`
- `Owner.ContactInfo`, `Trainer.ContactInfo` → `UNIQUE`

---

## 3️⃣ Normalization

This logical model is fully normalized to **Third Normal Form (3NF)**:

- **1NF**: All values are atomic.
- **2NF**: All attributes depend fully on the primary key.
- **3NF**: No transitive dependencies between non-key attributes.

---

## 4️⃣ Handling Data Scenarios

The design handles various real-world situations:

- Horses training with multiple trainers → handled via `TrainingLog`.
- One veterinarian treating many horses → handled via `HealthRecord`.
- Horses entering many races → managed via `Participation`.
- Betting data tied to specific races → handled via `BettingInsight`.

---

## 5️⃣ Presentation & Review

This file documents the logical model clearly and is ready for review. It includes all key entities, their attributes, relationships, and constraints for feedback before moving to Phase IV (Physical Design or Implementation).

---

## 📌 Status

✅ Phase III Complete – Logical model design finished and documented.


