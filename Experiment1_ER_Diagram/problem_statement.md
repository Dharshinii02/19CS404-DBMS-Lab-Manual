# ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

**Business Context:**  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**  
- Members register with name, membership type, and start date.  
- Each member can join multiple programs (Yoga, Zumba, Weight Training).  
- Trainers assigned to programs; a program may have multiple trainers.  
- Members may book personal training sessions with trainers.  
- Attendance recorded for each session.  
- Payments tracked for memberships and sessions.

### ER Diagram:
<img width="870" height="643" alt="Screenshot 2025-09-22 132558" src="https://github.com/user-attachments/assets/e9ac7bee-6912-4a08-a927-bbf53221f7b5" />

![ER Diagram](er_diagram_fitness.png)

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|  Member      |   MemberID, Name, Membershiptype                 |  Each member has a unique ID     |
|  Trainer      |   TrainerID, Name, Expertise, ContactNumber                 | Trainers are uniquely identified|
|  Program      |   ProgramID, Title, Category, Duration                 |    Programs can exist without members   |
| PersonalSession       |  SessionID, Date, Time, TrainerID, MemberID                  |  Each session links exactly one trainer and one member     |
| Attendance       |   AttendanceID, MemberID, Amount, PaymentDate                 |    Tracks attendance per session   |
| Payment  | PaymentID, MemberID, Amount, PaymentDate, PaymentType |  Linked to membership or session fees      |      
### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|  Member – Program            |   M:N         |   Partial            |  Members can enroll in multiple programs     |
|    Trainer – Program          |     M:N       |    Partial           |  A program can be managed by multiple trainers     |
|  Member – PersonalSession            |    1:N        |     Mandatory for Session          |  One member can book many sessions     |
|   Trainer – PersonalSession           |     1:N       |      Mandatory for Session         |   One trainer conducts many sessions    |
|    Session – Attendance          |     1:N       |     Mandatory          | Each session has multiple attendance records     |
|     Member – Payment         |      1:N      |      Mandatory for Payment         |    Each payment belongs to exactly one member   |
### Assumptions
- IDs uniquely identify entities.
- Programs can exist without members enrolled.

- Personal sessions always have 1 trainer + 1 member.

- Attendance tracked only at session level.

- Payment types: membership fees / session fees.


---

# Scenario B: City Library Event & Book Lending System

**Business Context:**  
The Central Library wants to manage book lending and cultural events.

**Requirements:**  
- Members borrow books, with loan and return dates tracked.  
- Each book has title, author, and category.  
- Library organizes events; members can register.  
- Each event has one or more speakers/authors.  
- Rooms are booked for events and study.  
- Overdue fines apply for late returns.

### ER Diagram:
*Paste or attach your diagram here*  
![ER Diagram](er_diagram_library.png)

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|              |            |               |       |
|              |            |               |       |
|              |            |               |       |

### Assumptions
- 
- 
- 

---

# Scenario C: Restaurant Table Reservation & Ordering

**Business Context:**  
A popular restaurant wants to manage reservations, orders, and billing.

**Requirements:**  
- Customers can reserve tables or walk in.  
- Each reservation includes date, time, and number of guests.  
- Customers place food orders linked to reservations.  
- Each order contains multiple dishes; dishes belong to categories (starter, main, dessert).  
- Bills generated per reservation, including food and service charges.  
- Waiters assigned to serve reservations.

### ER Diagram:

![ER Diagram](er_diagram_restaurant.png)

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|       |                    |       |
|      |                    |       |
|       |                    |       |
|    |                    |       |
|        |                    |       |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|              |            |               |       |
|              |            |               |       |
|              |            |               |       |

### Assumptions
- 
- 
- 

---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
