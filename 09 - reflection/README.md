# IT 353 — Final Project Report
## Student Activities Management System (SAMS)

**Team:** 
- Ali Al-Ghamdi (S220040014)
- Emad Al-Sifani (S240032704)
- Adel Al-Otaibi (S240054457)
- Mohammed Al-Otaibi (S230042360)
- Fahad Al-Salmi (S240032977)

---

## Task 1 — Gantt Chart

![image](01%20-%20gantt/gantt-chart.png)

| ID | Major Development Activity | Start Date | End Date | Duration | Dependency |
|---|---|---|---|---|---|
| 1 | Project kickoff and allocation of group responsibilities | 17 Jul | 17 Jul | 1 day | None |
| 2 | Analyze the scenario and identify system requirements | 17 Jul | 18 Jul | 2 days | Task 1 |
| 3 | Prepare the project plan and Gantt chart | 19 Jul | 19 Jul | 1 day | Task 2 |
| 4 | Select the prototyping approach and design three low-fidelity screens | 20 Jul | 22 Jul | 3 days | Task 2 |
| 5 | Develop the Context Diagram and Level-0 DFD | 20 Jul | 22 Jul | 3 days | Task 2 |
| 6 | Develop three Level-1 DFDs | 23 Jul | 25 Jul | 3 days | Task 5 |
| 7 | Identify actors and develop the complete Use Case Model | 20 Jul | 23 Jul | 4 days | Task 2 |
| 8 | Prepare and submit the mid-project progress report | 25 Jul | 26 Jul | 2 days | Tasks 3–7 |
| 9 | Develop two UML Activity Diagrams | 26 Jul | 27 Jul | 2 days | Tasks 6 and 7 |
| 10 | Develop the UML Class Diagram | 28 Jul | 30 Jul | 3 days | Tasks 6, 7, and 9 |
| 11 | Design the relational database and normalize it to Third Normal Form | 31 Jul | 3 Aug | 4 days | Task 10 |
| 12 | Check consistency between prototypes, DFDs, use cases, UML diagrams, and database design | 4 Aug | 5 Aug | 2 days | Tasks 4, 6, 7, 9, 10, and 11 |
| 13 | Prepare individual reflections and update the Project Artifacts section | 6 Aug | 7 Aug | 2 days | Tasks 8 and 12 |
| 14 | Integrate all sections and format the final report | 7 Aug | 8 Aug | 2 days | Tasks 12 and 13 |
| 15 | Conduct the final review, export Word and PDF copies, and submit | 9 Aug | 9 Aug | 1 day | Task 14 |


## Task 2 — Prototyping

**Selected Approach: Evolutionary Prototyping**

Evolutionary prototyping is selected for the Student Activities Management System. The first prototype will contain the main functions and basic screen layouts. It can then be improved gradually after receiving feedback from students, activity organizers, and the Student Affairs Department.

This approach is appropriate because SAMS includes several connected processes, such as activity registration, waiting lists, electronic attendance, notifications, certificates, and activity transcripts. Users may identify new needs after interacting with the early version. Evolutionary prototyping allows the development team to refine these functions without discarding the entire prototype.

**Screen 1: Student Activities Browser**

![image1](02%20-%20prototypes/screen1-student-activities-browser.png)

This screen allows students to search and browse available activities. They can filter the results by category, campus, or date and select an activity to view its full details. The navigation bar also provides access to reservations, notifications, and participation history.

**Screen 2: Activity Details and Reservation**

![image2](02%20-%20prototypes/screen2-activity-details-reservation.png)

This screen presents the information students need before making a reservation. It displays the activity schedule, location, eligibility requirements, registration deadline, attendance method, and remaining capacity. When the activity is full, the reservation button can be replaced with a “Join Waiting List” button.

**Screen 3: Organizer Activity Management Dashboard**

![image3](02%20-%20prototypes/screen3-organizer-dashboard.png)

This screen allows organizers to create and manage activities from one location. They can monitor registration numbers, edit activity information, approve students when approval is required, record attendance, issue certificates, and generate reports.


**Why Evolutionary Prototyping Is More Appropriate**

Evolutionary prototyping is more suitable than throwaway prototyping because the SAMS prototype can become the foundation of the final system. The functions are closely related, and changes in one area may affect other areas. For example, revising the registration process may also require changes to capacity checks, waiting-list promotion, and notifications.

The approach also supports regular user feedback. Students can evaluate whether activity discovery and registration are simple, while organizers can test whether participant and attendance management meets their needs. Student Affairs staff can later review approval and reporting functions. Each version can therefore become more accurate and usable while preserving the work completed in earlier versions.

## Task 3 — Data Flow Diagrams (DFDs)


**Context Diagram for the Student Activities Management System**

![Task 3 diagram](context-diagram.png)

The context diagram represents SAMS as one central process and shows its interaction with three external entities. Students send activity searches, reservations, cancellations, attendance information, and history requests. In return, they receive activity details, reservation updates, notifications, certificates, and activity transcripts.

Activity organizers provide activity information, registration conditions, approvals, attendance records, and report requests. The system returns participant lists, registration updates, attendance results, and engagement reports.

The Student Affairs Department manages categories, approves activities, requests institutional reports, and verifies activity transcripts. SAMS provides activities awaiting approval, university-wide participation statistics, reports, and student activity records. No internal processes or data stores are shown because the context diagram presents only the system boundary and its external data flows.

**Level-0 DFD**

![image1](03%20-%20dfd/level0-dfd.png)

**Level-1 DFD**

**Process 1.0: Manage Activities**

This process explains how activities are created and made available to students. The Activity Organizer enters the activity details through Process 1.1, including the title, description, location, and other basic information. Process 1.2 adds the schedule, participant limit, registration period, eligibility rules, and attendance method. The activity information is then stored in the Activities data store.

Process 1.3 submits the activity to the Student Affairs Department for review. The department approves or rejects the request, and the approval status is recorded. After approval, Process 1.4 allows the organizer to publish, update, or cancel the activity. Finally, Process 1.5 receives students’ search and filter requests, retrieves published activity data, and returns the relevant activity information.

![image2](03%20-%20dfd/level1-manage-activities.png)

**Process 2.0: Manage Registration and Waitlist**

This process manages seat reservations, cancellations, and waiting-list entries. Process 2.1 receives a reservation or cancellation request from the student. For a reservation, Process 2.2 checks the activity’s eligibility requirements and registration deadline using information from the Activities data store.

If the request is valid, Process 2.3 checks the current number of registrations against the activity capacity. Process 2.4 confirms the registration when a seat is available or sends an approval request to the Activity Organizer when organizer approval is required. If the activity is full, the student is added to the waiting list. All registration and waiting-list details are stored in the Registrations and Waitlist data store.

Process 2.5 handles cancellations and updates the student’s status. When a cancellation creates an available seat, the system promotes an eligible student from the waiting list and updates the registration records and participant list.

![image3](03%20-%20dfd/level1-registration-waitlist.png)

**Process 3.0: Record Attendance and Issue Certificates**

This process records student attendance and updates participation records. Process 3.1 receives attendance input through a QR code scanned by the student or through manual attendance data entered by the Activity Organizer.

Process 3.2 checks the Registrations and Waitlist data store to confirm that the student has a valid registration for the activity. After validation, Process 3.3 records the attendance information in the Attendance Records data store.

Process 3.4 uses the confirmed attendance to issue a participation certificate and update the student’s activity history, including participation hours and completed activities. These details are stored in the Certificates and Activity History data store. Process 3.5 then sends the attendance result or certificate to the student and provides an attendance summary to the Activity Organizer.

![image4](03%20-%20dfd/level1-attendance-certificates.png)


## Task 4 — Use Case Model


**System Actors**

An actor represents an external role that interacts with the system to achieve a specific goal.

| Actor | Role in the System |
|---|---|
| Student | Searches for activities, views details, reserves seats, cancels reservations, joins waiting lists, records attendance, receives notifications, and views participation records. |
| Activity Organizer | Creates and manages activities, handles registrations, records attendance, issues certificates, and generates activity reports. |
| Student Affairs Officer | Represents the Student Affairs Department by managing categories, approving activities, monitoring participation, generating institutional reports, and verifying activity transcripts. |

The QR code and notification functions are treated as parts of SAMS rather than separate actors because the scenario does not identify independent external systems for them.

**Use Case Diagram**

![image](04%20-%20use-case/use-case-diagram.png)

**Fully Documented Use Cases**

Use Case 1: Reserve a Seat

| Field | Description |
|---|---|
| Use Case Name | Reserve a Seat |
| Level | User goal |
| Primary Actor | Student |
| Supporting Actor | Activity Organizer, when approval is required |
| Stakeholders | The student needs a clear reservation result. The organizer needs an accurate participant list and capacity count. |
| Preconditions | The activity is published, registration is open, and the student is eligible to use the system. |
| Minimal Guarantee | No invalid or duplicate reservation is recorded. |
| Success Guarantee | The student receives a confirmed, pending, or waitlisted status, and the registration records are updated. |
| Trigger | The student selects the “Reserve a Seat” option. |

**Main Success Scenario**

The student opens the selected activity.

SAMS displays the activity details and registration conditions.

The student requests a seat.

The system checks the registration deadline.

The system verifies the student’s eligibility.

The system checks for an existing reservation.

The system checks the remaining activity capacity.

SAMS creates a confirmed reservation.

The participant list and available capacity are updated.

The student receives a registration confirmation.

**Extensions**

4a. The registration deadline has passed. The system rejects the request and displays the reason.

5a. The student does not meet the eligibility requirements. The request is rejected.

6a. The student already has a reservation. The system displays the existing status.

7a. The activity is full. The student is added to the waiting list.

7b. Organizer approval is required. The reservation is recorded as pending until the organizer makes a decision.



**Use Case 2: Create and Submit Activity**

| Field | Description |
|---|---|
| Use Case Name | Create and Submit Activity |
| Level | User goal |
| Primary Actor | Activity Organizer |
| Supporting Actor | Student Affairs Officer |
| Stakeholders | The organizer needs to create a complete activity. Student Affairs needs sufficient information to review it. Students need accurate activity details after publication. |
| Preconditions | The organizer is authorized to manage activities, and the required activity categories are available. |
| Minimal Guarantee | An incomplete activity is not submitted or published. A saved draft remains available for editing. |
| Success Guarantee | The activity is stored with a pending approval status and becomes available for Student Affairs review. |
| Trigger | The organizer selects “Create New Activity.” |

**Main Success Scenario**

The organizer selects the option to create an activity.

SAMS displays the activity form.

The organizer enters the activity title, description, category, date, time, and location.

The organizer defines the participant limit and registration period.

The organizer enters the eligibility requirements and attendance method.

The organizer indicates whether student registrations require approval.

SAMS validates the entered information.

The organizer submits the activity.

The system saves the activity with a pending approval status.

Student Affairs is notified that the activity requires review.

The organizer receives submission confirmation.

**Extensions**

3a. The activity is virtual. The organizer provides virtual location information.

7a. Required information is missing. The system identifies the missing fields.

7b. The dates are invalid. The system requests corrected dates.

8a. The organizer selects “Save as Draft.” The activity is stored without being submitted.

10a. Student Affairs rejects the activity. The system records the reason and notifies the organizer.



## Task 5 — Activity Diagrams

UML Activity Diagram 1: Student Activity Registration

![Image1](05%20-%20activity-diagrams/activity-diagram1-registration.png)

The process begins when a student browses and selects an activity. SAMS checks the registration period, eligibility requirements, and available capacity. If the activity is full, the student is placed on the waiting list. When organizer approval is required, the request remains pending until a decision is made. A successful reservation updates the participant list and sends a confirmation notification.
UML Activity Diagram 2: Attendance and Certificate Issuance

![Image2](05%20-%20activity-diagrams/activity-diagram2-attendance.png)

The attendance process starts when the student scans a QR code or the organizer records attendance manually. SAMS verifies that the student has a valid registration and prevents duplicate attendance records. After successful validation, the system records attendance and updates participation hours and activity history. A certificate is issued when the required participation conditions are satisfied.


## Task 6 — Class Diagram

![image](06%20-%20class-diagram/class-diagram.png)

**Inheritance**

User is an abstract superclass containing the common information and operations shared by all users. Student, ActivityOrganizer, and StudentAffairsOfficer inherit these features and add functions related to their specific roles.

**Main Associations and Multiplicities**

An Activity Organizer can manage many activities, while each activity is managed by one organizer. An activity belongs to one category, but a category can contain many activities. A Student Affairs Officer may approve several activities.

The Registration class resolves the many-to-many relationship between students and activities. One student can create many registrations, and one activity can receive many registrations. A registration may also create one waiting-list entry when the activity is full.

Each registration may produce one attendance record. Valid attendance may result in one certificate. A student can receive several notifications and earn several achievements. Each student may also have one Activity Transcript that summarizes the student’s verified participation records.

## Task 7 — Database Design


**1 - Database Tables**

| Table | Columns and Data Types | Keys |
|---|---|---|
| Users | user_id INT, university_id VARCHAR(20), full_name VARCHAR(100), email VARCHAR(120), password_hash VARCHAR(255), role VARCHAR(25), campus VARCHAR(50) | PK: user_id; UNIQUE: university_id, email |
| ActivityCategories | category_id INT, category_name VARCHAR(60), description VARCHAR(255) | PK: category_id; UNIQUE: category_name |
| Activities | activity_id INT, category_id INT, organizer_id INT, approved_by INT NULL, title VARCHAR(150), description TEXT, campus VARCHAR(50), location VARCHAR(150), is_virtual BOOLEAN, start_datetime DATETIME, end_datetime DATETIME, registration_start DATETIME, registration_deadline DATETIME, participant_limit INT, participation_hours DECIMAL(5,2), attendance_method VARCHAR(30), eligibility_requirements VARCHAR(255), approval_required BOOLEAN, status VARCHAR(20) | PK: activity_id; FK: category_id → ActivityCategories; organizer_id → Users; approved_by → Users |
| Registrations | registration_id INT, activity_id INT, student_id INT, registration_date DATETIME, status VARCHAR(20), waitlist_position INT NULL, approved_by INT NULL, cancelled_at DATETIME NULL | PK: registration_id; FK: activity_id → Activities; student_id → Users; approved_by → Users; UNIQUE: activity_id + student_id |
| Attendance | attendance_id INT, registration_id INT, check_in_time DATETIME, attendance_method VARCHAR(30), status VARCHAR(20), recorded_by INT NULL | PK: attendance_id; FK: registration_id → Registrations; recorded_by → Users; UNIQUE: registration_id |
| Certificates | certificate_id INT, attendance_id INT, certificate_number VARCHAR(50), issue_date DATE, certificate_status VARCHAR(20) | PK: certificate_id; FK: attendance_id → Attendance; UNIQUE: attendance_id, certificate_number |
| Achievements | achievement_id INT, student_id INT, activity_id INT NULL, achievement_title VARCHAR(120), description VARCHAR(255), earned_date DATE | PK: achievement_id; FK: student_id → Users; activity_id → Activities |
| Notifications | notification_id INT, user_id INT, activity_id INT NULL, notification_type VARCHAR(30), message VARCHAR(255), sent_at DATETIME, is_read BOOLEAN | PK: notification_id; FK: user_id → Users; activity_id → Activities |

&nbsp;
**2 - Relational Schema**

![image](07%20-%20database/database-erd-schema.png)

&nbsp;
**3 - Main Relationships**
One activity category can classify many activities, while each activity belongs to one category.

One organizer can manage many activities, while each activity has one organizer.

Students and activities have a many-to-many relationship resolved through the Registrations table.

One registration may have one attendance record.

One attendance record may generate one certificate.

One student may receive many notifications and achievements.

A waitlisted student is represented by a registration with the status Waitlisted and a waitlist position.
&nbsp;
**4 - Important Constraints**
role should be limited to Student, Organizer, or Student Affairs Officer.

participant_limit must be greater than zero.

The activity end date must be later than its start date.

The registration deadline must be before the activity begins.

A student cannot register for the same activity more than once.

Each registration can have no more than one attendance record.

Activity status may be Draft, Pending, Approved, Published, Cancelled, or Completed.

Registration status may be Pending, Confirmed, Waitlisted, Rejected, or Cancelled.

&nbsp;
*5 - Normalization**

**First Normal Form**

Each table contains atomic values, and no column stores repeating groups. For example, registrations are stored as separate rows rather than keeping several student IDs inside the Activities table.

**Second Normal Form**

Every non-key attribute depends on the whole primary key. Each table uses a single primary key, while the unique combination of activity_id and student_id prevents duplicate registrations.

**Third Normal Form**

Non-key attributes do not depend on other non-key attributes. Category information is stored in ActivityCategories instead of being repeated in Activities. User details are stored once in Users, while registration, attendance, certificate, achievement, and notification information is maintained in separate relations.

The Student Activity Transcript does not need a separate table. It can be generated from confirmed attendance, activities, certificates, participation hours, and achievements. This avoids duplicated data and keeps the transcript accurate when participation records change.

---

## Project Artifacts

Github Repository: https://github.com/PRQAE/IT-353-Project.git

---

## Reflection

### Reflection — Ali

For my part, I was responsible for building the Gantt chart and developing the prototypes. Building the Gantt chart on my own turned out to be the task that took the longest, since it required breaking the whole project down into 15 separate activities, estimating realistic durations for each team mate, and working out which tasks depended on others before anything else could start; it's essentially the task of managing the whole team's time, not just my own two deliverables. While reviewing the chart for clarity, I noticed the dependency column was using labels like "Task 1" and "Task 2" to refer to the row numbers in the Gantt chart itself, which was confusing because the assignment already uses "Task 1" through "Task 7" to refer to the seven graded deliverables. Someone reading the dependency column could easily mistake a Gantt row reference for an actual assignment task. I fixed this by renaming the column to "Depends on Activity ID" so the two numbering systems couldn't be confused with each other. For prototyping, choosing Evolutionary Prototyping over Throwaway Prototyping was a fairly clear decision rather than something we debated at length; given SAMS has several closely connected features (registration, waitlist, attendance, notifications), rebuilding a throwaway prototype from scratch after testing didn't make sense with our timeline, so Evolutionary Prototyping was the obvious fit. I designed the three screens in Figma, and unlike some other parts of the project, I only built one version of each screen rather than iterating through multiple drafts. If I were to redo this project with more time, I would want to actually test the prototype's UI/UX with real users — even just a few classmates walking through the Figma screens rather than relying on my own judgment for whether the flow makes sense. Since I only made one version of each screen, I don't have strong confidence that the layout is genuinely intuitive to someone seeing it for the first time, and user feedback at that stage would have been more valuable than refining it further on my own.

### Reflection — Emad
For my part, I was responsible for developing the Data Flow Diagrams (DFDs) for the Student Activities Management System. The biggest challenge was making sure that the Context Diagram, the Level-0 DFD, and the three Level-1 DFDs matched each other. At first, I found that some data flows were not connected correctly between the different diagram levels. To solve this, I reviewed every process, external entity, and data store carefully. I compared all the diagrams and corrected the missing or incorrect data flows until everything matched. This helped me better understand how DFDs work and why every level should represent the same system.
When creating the diagrams, I divided the system into three main processes: Manage Activities, Manage Registration and Waitlist, and Record Attendance and Issue Certificates. I chose this structure because it follows the normal workflow of the system and makes the diagrams easier to understand. I also considered creating more major processes, such as notifications and reports, but that would have made the diagrams more complicated. Keeping these functions inside the existing processes made the design simpler while still including all the required system functions.
I used ChatGPT during this project only for grammar checking. After correcting the language, I reviewed the explanations myself to make sure they correctly described the Context Diagram, Level-0 DFD, and the Level-1 DFDs. I also checked that the descriptions matched the diagrams before adding them to the final report.
If I had more time, I would ask classmates or potential users to review the diagrams and provide feedback before submitting the project. Their comments could help me improve the design and identify any missing details. I would also improve the layout of the diagrams to make them clearer and easier to read. Overall, this project improved my understanding of DFDs and showed me the importance of checking every part of the diagrams to make sure they are accurate.

### Reflection — Adel

Actually During my work on the Student Activities Management System (SAMS) project, I was mainly responsible for designing and modeling the Use Case Diagram. The biggest challenge I faced was accurately structuring the interaction between seat reservation, eligibility checks, and waitlist management without creating an overly complex diagram. To resolve this, I carefully studied UML relationship guidelines and implemented <<include>> relationships for essential prerequisites like Check Eligibility and Check Capacity, while using an <<extend>> relationship for Join Waitlist so it only triggers when a capacity limit is reached.
For handling attendance tracking, I chose to implement an automated QR-code system rather than traditional manual check-ins by activity organizers. Although manual entry was considered, the automated approach drastically minimizes human error and integrates smoothly with generating student participation transcripts. The tradeoff was assuming all students have active smartphone access, which was a reasonable decision given our target campus audience.
Throughout this design process, I utilized AI tools such as Gemini to brainstorm complex edge cases and double-check standard UML relationship rules, verifying every generated suggestion against core software engineering principles before applying it. If I had more time and resources, I would conduct usability tests with actual students and faculty members to gather direct feedback on the interaction flow, and I would expand the diagram to include real-time automated notifications for students on the waitlist.

### Reflection — Mohammed
During this project, I learned how to create UML Activity Diagrams and how to easily illustrate system processes. The biggest challenge I faced was ensuring the steps were in the correct order and then verifying that all the important decisions in the process were included. To overcome this, I went back to the project and checked the requirements multiple times, making sure the diagram content matched the system.

I chose to use UML Activity Diagrams because they make the process easier to understand. I considered using a simple, standard diagram, but UML is more suitable for the software project and provides a better visual representation of the system.

This project helped me improve my understanding of systems analysis and design. I learned about small details, such as verifying available spaces in an activity or checking student attendance. These details are important because they affect the entire system and how it works.

I also learned a lot through teamwork with my team. We understood each other, shared ideas, and reviewed the work thoroughly before adding the report.

If I had more time, I would have added more diagrams and explained the system better. I would have reviewed the project multiple times to ensure there were no missing steps and to identify any errors. This project helped me gain experience in UML, and through it, I understood the design process within the system and how the system works.

### Reflection — Fahad
