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

## Task 5 — Activity Diagrams

## Task 6 — Class Diagram

## Task 7 — Database Design

---

## Project Artifacts

Github Repository: https://github.com/PRQAE/IT-353-Project.git

---

## Reflection

### Reflection — Ali

### Reflection — Emad

### Reflection — Adel

### Reflection — Mohammed

### Reflection — Fahad