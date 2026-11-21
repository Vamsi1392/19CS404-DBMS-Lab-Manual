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
*Paste or attach your diagram here*  
<img width="1885" height="862" alt="Screenshot 2026-11-21 123320" src="https://github.com/user-attachments/assets/5ed7a3ac-e872-4df5-a245-938f25d24e6b" />


### Entities and Attributes

Entities and Attributes
Entity	Attributes (PK, FK)	Notes
Member	MemberID (PK), Name, PhoneNumber, Email, MembershipType, StartDate	Stores member details
Trainer	TrainerID (PK), Name, ContactDetails, Specialization, Experience	Stores trainer details
Program	ProgramID (PK), ProgramName, Description, Duration, Fee	Stores fitness program information
MemberProgram	MemberProgramID (PK), MemberID (FK), ProgramID (FK), JoinDate	Stores member program registrations
ProgramTrainer	ProgramTrainerID (PK), ProgramID (FK), TrainerID (FK)	Stores trainer assignments to programs
TrainingSession	SessionID (PK), MemberID (FK), TrainerID (FK), SessionDate, StartTime, EndTime	Stores personal training session details
Attendance	AttendanceID (PK), SessionID (FK), AttendanceStatus, AttendanceDate	Records member attendance for sessions
Payment	PaymentID (PK), MemberID (FK), SessionID (FK), Amount, PaymentDate, PaymentType, PaymentStatus	Tracks membership and training session payments

Relationships and Constraints
Relationship	Cardinality	Participation	Notes
Member - Program (Joins)	Many-to-Many	Member: Partial; Program: Partial	A member can join multiple programs
Program - Trainer (Assigned To)	Many-to-Many	Program: Total; Trainer: Partial	A program may have multiple trainers
Member - MemberProgram (Registers)	One-to-Many	Member: Partial; MemberProgram: Total	A member can register for multiple programs
Program - MemberProgram (Includes)	One-to-Many	Program: Partial; MemberProgram: Total	Each registration belongs to one program
Program - ProgramTrainer (Assigns)	One-to-Many	Program: Total; ProgramTrainer: Total	A program can have multiple trainers
Trainer - ProgramTrainer (Assigned)	One-to-Many	Trainer: Partial; ProgramTrainer: Total	A trainer can handle multiple programs
Member - TrainingSession (Books)	One-to-Many	Member: Partial; TrainingSession: Total	A member can book multiple sessions
Trainer - TrainingSession (Conducts)	One-to-Many	Trainer: Partial; TrainingSession: Total	A trainer conducts multiple sessions
TrainingSession - Attendance (Records)	One-to-One	TrainingSession: Total; Attendance: Total	Attendance is recorded for each session
Member - Payment (Makes)	One-to-Many	Member: Partial; Payment: Total	A member can make multiple payments
TrainingSession - Payment (Generates)	One-to-Many	TrainingSession: Partial; Payment: Partial	Payments can be linked to training sessions

Assumptions
- Each entity has a unique primary key.
- Foreign keys connect related entities.
- Each member has a membership type and start date.
- A member can join multiple fitness programs.
- A program can have multiple trainers.
- A trainer can handle multiple fitness programs.
- Members can book personal training sessions with trainers.
- Each training session is conducted by one trainer.
- Attendance is recorded for every training session.
- Members can make payments for memberships and training sessions.
- Payment status indicates whether the payment is paid or pending.
- Payment type identifies membership payment or session payment.
- Each session has a unique session ID.
- A member can attend multiple training sessions.




