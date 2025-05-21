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



# Phase IV – Database Creation and OEM Monitoring

## 📘 Project: HOOF-CARE – Horse Health & Performance Monitoring MIS

This document details the successful creation of a pluggable Oracle database (PDB) for the HOOF-CARE system and its integration with Oracle Enterprise Manager (OEM) for monitoring. Phase IV ensures proper setup, access control, and visibility into the system's runtime behavior.

---

## 🗂️ 1. Pluggable Database Creation

### ✅ PDB Name
thurs_26858_Tresor_hoofcare_db


### ✅ SQL Command Used

```sql
CREATE PLUGGABLE DATABASE thurs_26858_Tresor_hoofcare_db
  ADMIN USER admin IDENTIFIED BY tresor
  FILE_NAME_CONVERT = (
    'C:/APP/TRESO/PRODUCT/21C/ORADATA/XE/PDBSEED/',
    'C:/APP/TRESO/PRODUCT/21C/ORADATA/XE/thurs_26858_Tresor_hoofcare_db/'
  );
```

This command creates the PDB using the PDBSEED template and assigns admin as the default administrator with DBA privileges.

👤 2. User Creation
➤ Admin User
Username: admin

Password: tresor

➤ Project Schema User

CREATE USER hoofcare_user IDENTIFIED BY tresor;
GRANT CONNECT, RESOURCE, DBA TO hoofcare_user;

This user will be used in future phases for schema creation and PL/SQL development.

🔄 3. Listener and Service Configuration
To verify that the listener recognizes the newly created PDB:

lsnrctl services

The output confirmed the registration of the service:

Service "thurs_26858_Tresor_hoofcare_db" has 1 instance(s) ...

➤ Connection Tested Using SQL*Plus

sqlplus hoofcare_user/tresor@localhost:1521/thurs_26858_Tresor_hoofcare_db

🌐 4. Oracle Enterprise Manager (OEM) Monitoring
OEM Express was accessed via:

https://localhost:5500/em

➤ Login Credentials

User: hoofcare_user

Container: THURS_26858_TRESOR_HOOFCARE_DB

Password: tresor

📸 Screenshots of Monitoring:

OEM Login Screen
![image](https://github.com/user-attachments/assets/7184bae8-a00d-4f1f-9843-6c4ec7c18eb1)

OEM Dashboard View
![image](https://github.com/user-attachments/assets/b24a7f7d-7d80-4a9f-9ed7-186980931968)

These screenshots confirm successful login and monitoring of the correct pluggable database and user session.

---


# Phase V – Table Implementation and Data Insertion

## 🐎 Project: HOOF-CARE MIS – Physical Database Structure

This phase focuses on implementing the physical structure of the database based on the logical model defined in Phase III. It includes creating tables in Oracle SQL, inserting realistic data, and enforcing data integrity using constraints and relationships.

---

## ✅ 1. Table Creation

All tables were created under the `hoofcare_user` schema inside the PDB `thurs_26858_Tresor_hoofcare_db`. Each table corresponds to a key entity in the system and includes:

- **Appropriate data types**
- **Primary and foreign keys**
- **NOT NULL, UNIQUE, and CHECK constraints**

### 📋 Tables Created:
- `Owner`
- `Horse`
- `Trainer`
- `Veterinarian`
- `TrainingLog`
- `HealthRecord`
- `RaceEvent`
- `Participation`
- `BettingInsight`

Each table was created using SQL `CREATE TABLE` statements with structural constraints to enforce data validity and integrity.

---

## ✍️ 2. Data Insertion

Realistic and meaningful data was inserted to simulate typical operations within the HOOF-CARE system.

Examples include:
- Horse training logs with durations and performance notes
- Health records from veterinarians with check-up dates and treatment
- Participation records in race events
- Betting insights with race odds and analytical notes

All data was inserted using standard SQL `INSERT INTO` commands.

> Data was committed using:
```sql
COMMIT;
```

🛡 3. Data Integrity Enforcement
Integrity was validated using:

Primary Keys to uniquely identify each entity

Foreign Keys to maintain relational dependencies

NOT NULL to ensure essential fields are always filled

UNIQUE to avoid duplicate contact information

CHECK constraints to validate logical values (e.g., Duration > 0)

🔎 Validation Queries Used:

-- Check horses without owners
SELECT * FROM Horse WHERE OwnerID NOT IN (SELECT OwnerID FROM Owner);

-- Check horses without training logs
SELECT HorseID FROM Horse
MINUS
SELECT HorseID FROM TrainingLog;

-- Check for duplicate trainer emails
SELECT ContactInfo, COUNT(*) FROM Trainer GROUP BY ContactInfo HAVING COUNT(*) > 1;

-- Check invalid training durations
SELECT * FROM TrainingLog WHERE Duration <= 0;


---




