# ER Diagram Workshop – Submission Template
# Name: Sanjay A
# reg.no: 212224040288
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
<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/7bbc45a1-614d-4401-8654-744dae443d06" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|   Member     |MemberID (PK), Name, MembershipType, StartDate                    |Stores member details. Members can join programs & sessions.       |
| Program       |    ProgramID (PK), ProgramName                |  Gym programs like Yoga, Zumba, Weight Training.     |
| Trainer       |       TrainerID (PK), TrainerName, Specialization             | Trainers assigned to programs and personal sessions.      |
|  PersonalTrainingSession      | SessionID (PK), SessionDate, MemberID (FK), TrainerID (FK)                   |  	Personal 1-to-1 training bookings.     |
|     Attendance   |           AttendanceID (PK), Date, MemberID (FK), ProgramID (FK)         |    Tracks member attendance for programs.   |


### Relationships and Constraints

| Relationship                                  | Cardinality             | Participation                        | Notes                                                                        |
| --------------------------------------------- | ----------------------- | ------------------------------------ | ---------------------------------------------------------------------------- |
| Member — joins — Program                      | Many-to-Many (M:N)      | Total on Member, Partial on Program  | A member can join multiple programs; a program may have many members.        |
| Trainer — assigned to — Program               | Many-to-Many (M:N)      | Partial on both                      | A program can have multiple trainers; trainers may handle many programs.     |
| Member — books — PersonalTrainingSession      | One-to-Many (1:M)       | Total on Session, Partial on Member  | Each session is for one member; a member can book many sessions.             |
| Trainer — conducts — PersonalTrainingSession  | One-to-Many (1:M)       | Total on Session, Partial on Trainer | Each session is handled by one trainer; a trainer can conduct many sessions. |
| Member — has — Attendance                     | One-to-Many (1:M)       | Total on Attendance                  | Every attendance record must belong to a member.                             |
| Program — recorded in — Attendance            | One-to-Many (1:M)       | Total on Attendance                  | Every attendance record must be associated with a valid program.             |
| Member — makes — Payment                      | One-to-Many (1:M)       | Total on Payment                     | Every payment belongs to a specific member.                                  |
| PersonalTrainingSession — billed in — Payment | Optional (0..1) to Many | Partial on Payment                   | Payments may or may not be linked to personal training sessions.             |


### Assumptions
Each member, trainer, program, and session has a unique ID.
A member can join many programs; a program may have no members.
A trainer can handle multiple programs.
Personal training sessions always involve one member and one trainer.
Payments are always linked to a member; linking to a session is optional.
Attendance is recorded only for programs.
A program may exist even without trainers assigned.
Dates are stored in standard date formats.
Members can have multiple attendance records on different days.
Trainers can exist without conducting any sessions.
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
<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/aa776ea1-7c2b-41cb-b483-a9ec459514f6" />

### Entities and Attributes

| Entity         | Attributes (PK, FK)                                                                | Notes                                               |
| -------------- | ---------------------------------------------------------------------------------- | --------------------------------------------------- |
| Member         | **MemberID (PK)**, Name, Email, Phone                                              | Library members who borrow books and attend events. |
| Book           | **BookID (PK)**, Title, Author, Category                                           | Each book has a unique ID and is used for lending.  |
| Loan           | **LoanID (PK)**, LoanDate, ReturnDate, DueDate, **MemberID (FK)**, **BookID (FK)** | Tracks book borrowing and returns.                  |
| Event          | **EventID (PK)**, EventName, EventDate, **RoomID (FK)**                            | Events organized by the library.                    |
| Speaker        | **SpeakerID (PK)**, SpeakerName, Expertise                                         | Speakers or authors who participate in events.      |
| Room           | **RoomID (PK)**, RoomName, Capacity                                                | Rooms used for events or study bookings.            |
| MemberEventReg | **RegID (PK)**, **MemberID (FK)**, **EventID (FK)**                                | Records member registrations for events.            |
| Fine           | **FineID (PK)**, Amount, PaidStatus, **LoanID (FK)**                               | Stores overdue fines for late book returns.         |

### Relationships and Constraints

| Entity 1 | Relationship  | Entity 2        | Cardinality | Participation                      |
| -------- | ------------- | --------------- | ----------- | ---------------------------------- |
| Member   | borrows       | Book (via Loan) | 1:M         | Total (Loan)                       |
| Book     | issued in     | Loan            | 1:M         | Total (Loan)                       |
| Member   | registers for | Event           | M:N         | Partial (Member), Partial (Event)  |
| Event    | has           | Speaker         | M:N         | Partial (Event), Partial (Speaker) |
| Event    | uses          | Room            | M:1         | Total (Event)                      |
| Loan     | generates     | Fine            | 0..1:1      | Partial (Loan)                     |


### Assumptions
- Each book, member, event, and speaker has a unique ID.
-A book can only be borrowed by one member at a time.
-fine is generated only when a loan exceeds the due date.
-A member can attend many events; an event may have no registrations.
-Each event is assigned to exactly one room.
-A speaker may participate in multiple events.
-ReturnDate may be NULL when book is not returned yet.

  
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
<img width="1024" height="1024" alt="image" src="https://github.com/user-attachments/assets/a2a8a201-cd5b-4981-a8fe-ea92a750e067" />


### Entities and Attributes
| Entity      | Attributes (PK, FK)                                               | Notes                                             |
| ----------- | ----------------------------------------------------------------- | ------------------------------------------------- |
| Customer    | **CustomerID (PK)**, Name, Phone, Email                           | Customers who place orders and make reservations. |
| MenuItem    | **ItemID (PK)**, ItemName, Price, Category                        | Food items available in the restaurant menu.      |
| Order       | **OrderID (PK)**, OrderDate, **CustomerID (FK)**, TotalAmount     | Stores information about customer orders.         |
| OrderItem   | **OrderItemID (PK)**, **OrderID (FK)**, **ItemID (FK)**, Quantity | Maps each menu item included in an order.         |
| Reservation | **ReservationID (PK)**, **CustomerID (FK)**, TableNo, Date, Time  | Stores customer table bookings.                   |
| Payment     | **PaymentID (PK)**, **OrderID (FK)**, AmountPaid, PaymentMethod   | Tracks payments made for orders.                  |



### Relationships and Constraints

| Entity 1 | Relationship | Entity 2    | Cardinality | Participation      |
| -------- | ------------ | ----------- | ----------- | ------------------ |
| Customer | places       | Order       | 1:M         | Total (Order)      |
| Order    | contains     | OrderItem   | 1:M         | Total (OrderItem)  |
| MenuItem | appears in   | OrderItem   | 1:M         | Partial (MenuItem) |
| Customer | makes        | Reservation | 1:M         | Partial (Customer) |
| Order    | has          | Payment     | 1:1         | Partial (Payment)  |


### Assumptions
- Each customer, order, and menu item has a unique ID.
A customer may place orders without making reservations.
Payment is linked only to orders, not reservations.
A reservation is always for a single table.
Menu items can exist even if they are not ordered.
- 
- 

---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
