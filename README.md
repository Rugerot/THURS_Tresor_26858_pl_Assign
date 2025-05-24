## 📝 Introduction

### **Project Title:** HOOF-CARE Management Information System (MIS)  

### **Course:** Database Development with PL/SQL 

### **Institution:** AUCA  

### **Project Phase Coverage:** Phase I – VII  


| Student Name            | Student ID      |
|-------------------------|-----------------|
| NKUBIRI RUGERO Tresor   | 26858           |

### 🎯 Problem Statement

This project addresses the need for a centralized and secure system to manage horse health, training, race participation, and betting analytics. The HOOF-CARE MIS streamlines operations for trainers, veterinarians, and race organizers by modeling workflows, managing data, and enforcing business rules.

### Key challenges addressed include:
- Accurate record-keeping of horse performance, health, and race data
- Controlled access to sensitive operations using PL/SQL restrictions
- Auditing and accountability through advanced database logging
- Automation of administrative policies such as DML blocking on holidays and weekdays

This project demonstrates full-cycle MIS development — from business process modeling and ERD design to advanced Oracle programming and auditing.
---

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

![BPMN Diagram](https://github.com/Rugerot/THURS_Tresor_26858_pl_Assign/blob/main/bpmn_diagram.png)

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

### Entity Relationship Diagram (ERD)

![ERD DIAGRAM](https://github.com/Rugerot/THURS_Tresor_26858_pl_Assign/blob/main/Untitled.png)

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

## 👤 2. User Creation
### ➤ Admin User
Username: admin

Password: tresor

### ➤ Project Schema User

CREATE USER hoofcare_user IDENTIFIED BY tresor;
GRANT CONNECT, RESOURCE, DBA TO hoofcare_user;

This user will be used in future phases for schema creation and PL/SQL development.

## 🔄 3. Listener and Service Configuration
To verify that the listener recognizes the newly created PDB:

lsnrctl services

The output confirmed the registration of the service:

Service "thurs_26858_Tresor_hoofcare_db" has 1 instance(s) ...

### ➤ Connection Tested Using SQL*Plus

sqlplus hoofcare_user/tresor@localhost:1521/thurs_26858_Tresor_hoofcare_db

## 🌐 4. Oracle Enterprise Manager (OEM) Monitoring
OEM Express was accessed via:

https://localhost:5500/em

### ➤ Login Credentials

User: hoofcare_user

Container: THURS_26858_TRESOR_HOOFCARE_DB

Password: tresor

### 📸 Screenshots of Monitoring:

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

## 🛡 3. Data Integrity Enforcement
Integrity was validated using:

- Primary Keys to uniquely identify each entity

- Foreign Keys to maintain relational dependencies

- NOT NULL to ensure essential fields are always filled

- UNIQUE to avoid duplicate contact information

- CHECK constraints to validate logical values (e.g., Duration > 0)

### 🔎 Validation Queries Used:
```sql
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
```

---


# Phase VI – Database Interaction and Transactions

## 📘 Project: HOOF-CARE MIS

This phase focuses on implementing database interaction logic using PL/SQL procedures, functions, and packages to automate and modularize operations such as data retrieval, analysis, and error handling.

---

## ✅ 1. Problem Statement

**Objective:**  
Retrieve a ranked list of horses based on their race performance (finish time) and analyze training patterns.

### 🧩 Use Case 1:
> Show all horses participating in a specific event, including their rank, result, and finish time.

### 🧩 Use Case 2:
> Calculate the average training session duration for a given horse.

These use cases support performance analysis and race-readiness evaluation — core functions of the HOOF-CARE system.

---

## 🛠 2. PL/SQL Procedure: `get_participation_by_event`

### 📋 Description:
Displays a list of horses participating in a specific event, sorted by finish time.

### 📄 Syntax:
```sql
EXEC hoofcare_package.get_participation_by_event(1);
```

### 🔍 Output Example:

Horse Name | Rank | Result | Time Completed
--------------------------------------------
Thunderbolt | 2 | Completed | +0 00:02:15.00


This procedure uses:

- A cursor to fetch data

- A parameter to accept the Event ID

- Exception handling using WHEN OTHERS



## 📊 3. PL/SQL Function: get_avg_training_duration
### 📋 Description:
Returns the average duration of all training sessions for a given horse.

### 📄 Syntax:

```sql
SELECT hoofcare_package.get_avg_training_duration(1) AS avg_duration FROM dual;
```
### 🔍 Output Example:

AVG_DURATION
------------
52.5

### The function:

- Uses AVG() aggregate function

- Accepts horse ID as input

- Returns NULL on error or no data

## 📦 4. PL/SQL Package: hoofcare_package
The package wraps both the procedure and function to support modular programming.

### ✅ Package Specification:

```sql
CREATE OR REPLACE PACKAGE hoofcare_package AS
  PROCEDURE get_participation_by_event(p_event_id IN Participation.EventID%TYPE);
  FUNCTION get_avg_training_duration(p_horse_id IN TrainingLog.HorseID%TYPE) RETURN NUMBER;
END hoofcare_package;
```


### ✅ Package Body:
Implements both with error handling, cursors, and logic.

## 🔁 5. DML and DDL Operations
### Type	Example
- DML	INSERT INTO Participation VALUES (...), UPDATE, DELETE, COMMIT
- DDL	CREATE TABLE, ALTER, DROP, CREATE PROCEDURE, CREATE FUNCTION, CREATE PACKAGE

All operations were successfully executed under hoofcare_user in the PDB thurs_26858_Tresor_hoofcare_db.

## 📦 6. Full Package Script (hoofcare_package.sql)

```sql
-- PACKAGE SPEC
CREATE OR REPLACE PACKAGE hoofcare_package AS
  PROCEDURE get_participation_by_event(p_event_id IN Participation.EventID%TYPE);
  FUNCTION get_avg_training_duration(p_horse_id IN TrainingLog.HorseID%TYPE) RETURN NUMBER;
END hoofcare_package;
/

-- PACKAGE BODY
CREATE OR REPLACE PACKAGE BODY hoofcare_package AS
  PROCEDURE get_participation_by_event (
    p_event_id IN Participation.EventID%TYPE
  ) IS
    CURSOR part_cursor IS
      SELECT h.Name, p.Rank, p.Result, p.TimeCompleted
      FROM Participation p JOIN Horse h ON h.HorseID = p.HorseID
      WHERE p.EventID = p_event_id ORDER BY p.TimeCompleted;

    v_record part_cursor%ROWTYPE;

  BEGIN
    OPEN part_cursor;
    DBMS_OUTPUT.PUT_LINE('Horse Name | Rank | Result | Time Completed');
    DBMS_OUTPUT.PUT_LINE('--------------------------------------------');
    LOOP
      FETCH part_cursor INTO v_record;
      EXIT WHEN part_cursor%NOTFOUND;
      DBMS_OUTPUT.PUT_LINE(
        v_record.Name || ' | ' ||
        NVL(TO_CHAR(v_record.Rank), 'N/A') || ' | ' ||
        v_record.Result || ' | ' ||
        v_record.TimeCompleted
      );
    END LOOP;
    CLOSE part_cursor;
  EXCEPTION
    WHEN OTHERS THEN
      DBMS_OUTPUT.PUT_LINE('Error: ' || SQLERRM);
  END;

  FUNCTION get_avg_training_duration (
    p_horse_id IN TrainingLog.HorseID%TYPE
  ) RETURN NUMBER
  IS
    v_avg_duration NUMBER;
  BEGIN
    SELECT AVG(Duration) INTO v_avg_duration FROM TrainingLog WHERE HorseID = p_horse_id;
    RETURN v_avg_duration;
  EXCEPTION
    WHEN NO_DATA_FOUND THEN
      RETURN NULL;
    WHEN OTHERS THEN
      DBMS_OUTPUT.PUT_LINE('Error: ' || SQLERRM);
      RETURN NULL;
  END;

END hoofcare_package;
/

```

## 🧪 7. Testing Summary


| Test                                    | Result                         |
| --------------------------------------- | ------------------------------ |
| Execute procedure with valid EventID    | ✅ Success                      |
| Run function with HorseID that has logs | ✅ Success                      |
| Run function with no data               | ✅ Returns NULL gracefully      |
| Run invalid EventID in procedure        | ✅ Returns no results, no crash |


## 🛡 8. Error Handling
Both the procedure and function include:

```sql
EXCEPTION
  WHEN OTHERS THEN
    DBMS_OUTPUT.PUT_LINE('Error occurred: ' || SQLERRM);
```


> Ensures safe execution without unexpected crashes.

### 📌 Phase Completion Status

| Task                      | Completed |
| ------------------------- | --------- |
| DML/DDL Execution         | ✅         |
| Procedure with Cursor     | ✅         |
| Function with Aggregation | ✅         |
| Modular Package           | ✅         |
| Error Handling            | ✅         |
| Testing and Validation    | ✅         |


## ✅ Conclusion
Phase VI successfully implements robust database interaction logic for the HOOF-CARE MIS. Key operations are now modular, testable, and fault-tolerant, ready for integration with front-end systems or advanced reporting in future phases.

---


# Phase VII – Advanced Database Programming and Auditing

## 📘 Project: HOOF-CARE MIS

This final phase enhances the system with advanced PL/SQL programming techniques and auditing features that enforce data restrictions and ensure accountability. It addresses security requirements by restricting DML operations during specified periods and by logging user activity for sensitive operations.

---

## ✅ 1. Problem Statement

In HOOF-CARE MIS, users manage sensitive records such as training logs, veterinary records, and race participation data. Unauthorized data manipulation—especially during business hours or holidays—poses a risk to data integrity and compliance.

### To address this, we implemented:

- A **weekday and holiday DML restriction trigger**
- An **audit system** that records all DML attempts (whether allowed or blocked)
- A **holiday reference table** that administrators can update monthly
- A **standalone logging procedure** using an autonomous transaction to capture audit logs even during DML failures

---

## 📅 2. Holiday Reference Table

A `HolidayDates` table stores the restricted dates.

```sql
CREATE TABLE HolidayDates (
  HolidayDate DATE PRIMARY KEY,
  Description VARCHAR2(100)
);
```
Sample data for June 2025:

```sql
INSERT INTO HolidayDates VALUES (TO_DATE('2025-06-01', 'YYYY-MM-DD'), 'Madaraka Day');
INSERT INTO HolidayDates VALUES (TO_DATE('2025-06-17', 'YYYY-MM-DD'), 'Veterinary Appreciation Day');
INSERT INTO HolidayDates VALUES (TO_DATE('2025-06-20', 'YYYY-MM-DD'), 'Hoofcare Maintenance Break');
COMMIT;
```

## 🔒 3. Trigger to Enforce DML Restrictions
This BEFORE INSERT OR UPDATE OR DELETE trigger blocks DML on the TrainingLog table during:

- Weekdays (Mon–Fri)

- Any holiday listed in HolidayDates

```sql
CREATE OR REPLACE TRIGGER trg_block_and_audit_traininglog
BEFORE INSERT OR UPDATE OR DELETE ON TrainingLog
FOR EACH ROW
DECLARE
  v_today       DATE := TRUNC(SYSDATE);
  v_day_name    VARCHAR2(10);
  v_holiday_cnt NUMBER := 0;
  v_op          VARCHAR2(10);
  v_user        VARCHAR2(50);
BEGIN
  v_user := SYS_CONTEXT('USERENV', 'SESSION_USER');

  IF INSERTING THEN
    v_op := 'INSERT';
  ELSIF UPDATING THEN
    v_op := 'UPDATE';
  ELSIF DELETING THEN
    v_op := 'DELETE';
  END IF;

  SELECT TO_CHAR(v_today, 'DY', 'NLS_DATE_LANGUAGE=ENGLISH') INTO v_day_name FROM dual;

  SELECT COUNT(*) INTO v_holiday_cnt FROM HolidayDates WHERE HolidayDate = v_today;

  IF v_day_name IN ('MON', 'TUE', 'WED', 'THU', 'FRI') OR v_holiday_cnt > 0 THEN
    log_audit_action(v_user, v_op, 'TrainingLog', 'DENIED', 'Weekday or holiday restriction');
    RAISE_APPLICATION_ERROR(-20001, 'DML operations are restricted on weekdays and holidays.');
  ELSE
    log_audit_action(v_user, v_op, 'TrainingLog', 'ALLOWED', NULL);
  END IF;
END;
/
```

## 📋 4. Audit Table
All DML attempts are logged in this AuditLog table:

```sql
CREATE TABLE AuditLog (
  LogID NUMBER GENERATED BY DEFAULT AS IDENTITY PRIMARY KEY,
  UserName VARCHAR2(50),
  Operation VARCHAR2(10),
  TableName VARCHAR2(50),
  ActionDate DATE DEFAULT SYSDATE,
  ActionTime TIMESTAMP DEFAULT SYSTIMESTAMP,
  Status VARCHAR2(20),
  Reason VARCHAR2(200)
);
```

## ⚙️ 5. Logging Procedure (log_audit_action)
The procedure uses an autonomous transaction to insert audit logs independently of the main transaction (even if DML is blocked):

```sql
CREATE OR REPLACE PROCEDURE log_audit_action (
  p_user     IN VARCHAR2,
  p_op       IN VARCHAR2,
  p_table    IN VARCHAR2,
  p_status   IN VARCHAR2,
  p_reason   IN VARCHAR2
)
IS
  PRAGMA AUTONOMOUS_TRANSACTION;
BEGIN
  INSERT INTO AuditLog (UserName, Operation, TableName, Status, Reason)
  VALUES (p_user, p_op, p_table, p_status, p_reason);
  COMMIT;
END;
/
```
## 🧪 6. Testing and Output
### ❌ Blocked Insert on Weekday:

```sql
INSERT INTO TrainingLog (...) VALUES (...);
```
### Output:

```sql
ORA-20001: DML operations are restricted on weekdays and holidays.
```
### ✅ Logged in Audit Table:

```sql
SELECT * FROM AuditLog ORDER BY ActionDate DESC, ActionTime DESC;
```

### Sample Entry:

| UserName       | Operation | Status | Reason                         |
| -------------- | --------- | ------ | ------------------------------ |
| HOOFCARE\_USER | INSERT    | DENIED | Weekday or holiday restriction |

## 🔐 7. Security Impact

This approach:

- Prevents unauthorized changes during critical periods

- Logs all DML attempts for review and compliance

- Supports real-time monitoring and historical audits

- It aligns with the HOOF-CARE MIS goal of ensuring data reliability and controlled access in a high-integrity environment.

### ✅ Phase Completion Status

| Task                          | Completed |
| ----------------------------- | --------- |
| Problem Statement             | ✅         |
| Holiday Table                 | ✅         |
| Restriction Trigger           | ✅         |
| Autonomous Logging Procedure  | ✅         |
| Audit Table & Logging         | ✅         |
| Testing and Output Validation | ✅         |


### 📌 Conclusion
This phase successfully introduces automation, restriction, and traceability into HOOF-CARE MIS. All sensitive operations are now governed by advanced PL/SQL logic with real-time audit trails — establishing a secure, monitored, and policy-driven environment.





