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