# API Documentation: AI Assistant for Student Tutors

## Overview

This API assists tutors in managing and assessing student projects, particularly for students developing physical robots. It includes features for recording student bio-data, managing projects and milestones, generating lesson plans, and auto-generating assessments. The API also supports audit trails, dynamic resource recommendations, and dashboards for monitoring student progress.

---

## 1. **Authentication Module**

The Authentication Module handles user registration, login, password management, and account activation/deactivation. It ensures secure access to the system and manages user roles (e.g., tutor, student, parent/guardian) to control permissions.

### Description:
- This module is critical for managing user access and ensuring that only authenticated users can interact with the system.
- It includes endpoints for creating new accounts, logging in, resetting passwords, and activating or deactivating accounts.

### Screenshots:
*(Insert screenshots showing the user registration and login pages here)*

### Endpoints:

| Endpoint              | Method | Description                                  |
|-----------------------|--------|----------------------------------------------|
| /auth/register        | POST   | Registers a new user.                        |
| /auth/login           | POST   | Authenticates a user and returns a token.    |
| /auth/reset-password  | POST   | Initiates a password reset process.          |
| /auth/update-password | PUT    | Updates the user’s password.                 |
| /auth/activate-account| POST   | Activates a user account.                    |
| /auth/deactivate-account| POST | Deactivates a user account.                  |

---

## 2. **Student Management Module**

The Student Management Module allows for the recording and management of student data, including their bio-data, assigned projects, and the ability for parents/guardians to access and monitor their progress.

### Description:
- This module manages student information and tracks their progress through the system.
- It includes functionality for registering students, retrieving student details, and updating or deleting student records.

### Screenshots:
*(Insert screenshots showing student registration and profile management screens here)*

### Endpoints:

| Endpoint              | Method | Description                                          |
|-----------------------|--------|------------------------------------------------------|
| /students             | POST   | Registers a new student.                             |
| /students             | GET    | Retrieves a list of all students.                    |
| /students/{id}        | GET    | Retrieves details of a specific student.             |
| /students/{id}        | PUT    | Updates student details.                             |
| /students/{id}        | DELETE | Deletes a student record.                            |
| /students/{id}/progress| GET   | Allows parents/guardians to view their child’s progress.|

---

## 3. **Project Management Module**

The Project Management Module is central to the student’s learning process. This module allows tutors to assign projects to students, track progress, and ensure milestones are completed in sequence.

### Description:
- This module handles the creation, updating, and tracking of projects assigned to students.
- Projects can be detailed with descriptions and linked to specific students for better tracking.

### Screenshots:
*(Insert screenshots showing project creation and progress tracking screens here)*

### Endpoints:

| Endpoint              | Method | Description                                    |
|-----------------------|--------|------------------------------------------------|
| /projects             | POST   | Assigns a new project to a student.            |
| /projects             | GET    | Retrieves a list of all projects.              |
| /projects/{id}        | GET    | Retrieves details of a specific project.       |
| /projects/{id}        | PUT    | Updates project details.                       |
| /projects/{id}        | DELETE | Deletes a project record.                      |

---

## 4. **Milestone Management Module**

The Milestone Management Module handles the creation, updating, and deletion of milestones, ensuring they maintain the correct order within their associated projects.

### Description:
- Milestones are independent entities that belong to a specific project.
- This module ensures that milestones are completed in a specific sequence and can be reordered if necessary.

### Screenshots:

![alt text](<login page design.webp>)

### Endpoints:

| Endpoint                         | Method | Description                                                    |
|----------------------------------|--------|----------------------------------------------------------------|
| /milestones                      | POST   | Creates a new milestone within a specific project, maintaining order. |
| /projects/{projectId}/milestones | GET    | Retrieves a list of milestones for a specific project, in order.  |
| /milestones/{id}                 | PUT    | Updates details of a specific milestone, maintaining its order within the project. |
| /milestones/{id}                 | DELETE | Deletes a specific milestone.                                   |
| /projects/{projectId}/milestones/reorder| POST | Reorders milestones within a project.                          |

---

## 5. **Assessment and Feedback Module**

The Assessment and Feedback Module allows tutors to record detailed assessments of student projects, noting challenges and achievements. The system can also auto-generate quizzes or assessments based on project data and milestones.

### Description:
- This module is key to evaluating student progress and providing feedback.
- Tutors can link assessments to specific milestones and provide feedback that helps improve AI-generated content.

### Screenshots:
*(Insert screenshots showing assessment recording and feedback submission screens here)*

### Endpoints:

| Endpoint               | Method | Description                                                    |
|------------------------|--------|----------------------------------------------------------------|
| /assessments           | POST   | Records a new assessment for a project, possibly linked to a specific milestone. |
| /assessments           | GET    | Retrieves a list of all assessments.                           |
| /assessments/{id}      | GET    | Retrieves details of a specific assessment.                    |
| /assessments/{id}      | PUT    | Updates an existing assessment.                                |
| /assessments/{id}      | DELETE | Deletes an assessment record.                                  |
| /assessments/{id}/feedback | POST| Allows tutors to provide feedback on the lesson plans or student progress. |
| /assessments/auto-generate| POST| Generates a quiz or assessment based on project data, possibly tied to a milestone. |

---

## 6. **Lesson Plan Management Module**

The Lesson Plan Management Module allows tutors to generate, version, and manage lesson plans using GPT-4. The system can generate multiple versions of a lesson plan, provide dynamic resource recommendations, and integrate auto-generated assessments.

### Description:
- This module leverages AI to create lesson plans based on student assessments and progress.
- Tutors can version lesson plans and receive recommendations for additional resources.

### Screenshots:
*(Insert screenshots showing lesson plan generation and version management screens here)*

### Endpoints:

| Endpoint                         | Method | Description                                                    |
|----------------------------------|--------|----------------------------------------------------------------|
| /lesson-plans/generate           | POST   | Generates a new lesson plan using GPT-4 based on project assessments and student progress. |
| /lesson-plans                    | GET    | Retrieves all lesson plans, including their versions.          |
| /lesson-plans/{id}               | GET    | Retrieves a specific lesson plan version.                      |
| /lesson-plans/{id}               | PUT    | Updates the content or resources of a lesson plan.             |
| /lesson-plans/{id}               | DELETE | Deletes a specific lesson plan version.                        |
| /lesson-plans/{id}/recommend-resources | POST| Uses GPT-4 to suggest additional resources based on the lesson plan content. |

---

## 7. **Resource Management Module**

The Resource Management Module manages the creation, retrieval, and updating of educational resources linked to lesson plans. The system also suggests resources dynamically based on content and past assessments.

### Description:
- Resources are integral to supporting lesson plans and providing additional learning material.
- This module allows tutors to manage resources and link them to specific lesson plans.

### Screenshots:
*(Insert screenshots showing resource management screens here)*

### Endpoints:

| Endpoint              | Method | Description                                                    |
|-----------------------|--------|----------------------------------------------------------------|
| /resources            | POST   | Adds a new resource to the system, linked to a lesson plan or standalone. |
| /resources            | GET    | Retrieves a list of all resources.                             |
| /resources/{id}       | GET    | Retrieves details of a specific resource.                      |
| /resources/{id}       | PUT    | Updates resource details.                                      |
| /resources/{id}       | DELETE | Deletes a resource record.                                     |

---

## 8. **Audit Trail Module**

The Audit Trail Module records every action performed in the system, providing a detailed record of who did what and when. This is crucial for maintaining transparency and accountability.

### Description:
- This module tracks changes across all entities in the system.
- It provides detailed logs that can be reviewed for auditing purposes.

### Screenshots:
*(Insert screenshots showing audit trail logs and details screens here)*

### Endpoints:

| Endpoint                         | Method | Description                                                    |
|----------------------------------|--------|----------------------------------------------------------------|
| /audit-trails                    | GET    | Retrieves all audit trails, recording actions performed on various entities. |
| /audit-trails/{entityType}/{entityId}| GET | Retrieves audit trail logs for a specific entity.              |

---

## 9. **Dashboard Module**

The Dashboard Module provides a high-level overview of key metrics and activities. Tutors, students, and parents/guardians each have tailored dashboards that display relevant information, helping them track progress and stay informed about upcoming events and deadlines.

### Description:
- Dashboards provide users with an overview of relevant data, such as student progress, project milestones, and lesson plan effectiveness.
- Different user roles have access to different types of dashboards.

### Screenshots:
*(Insert screenshots showing tutor, student, and parent/guardian dashboard views here)*

### Endpoints:

| Endpoint              | Method | Description                                    |
|-----------------------|--------|------------------------------------------------|
| /dashboard/tutor/{id} | GET    | Retrieves a summary of a tutor’s dashboard, including student progress, areas of difficulty, lesson plan effectiveness, and upcoming assessments. |
| /dashboard/student/{id}| GET   | Retrieves a summary of a student’s dashboard, including project status, upcoming assessments, and feedback. |
| /dashboard/parent/{id}| GET    | Retrieves a summary of a parent/guardian’s dashboard, including their child’s progress and upcoming events. |

---

## 10. **User Management Module**

The User Management Module allows for the management of user roles and access levels. It handles the creation, updating, and deletion of users, and manages their roles (e.g., tutor, student, parent/guardian).

### Description:
- This module is essential for maintaining the system's security and ensuring users have the correct permissions.
- It supports CRUD operations for user management and role assignments.

### Screenshots:
*(Insert screenshots showing user management screens here)*

### Endpoints:

| Endpoint              | Method | Description                                   |
|-----------------------|--------|-----------------------------------------------|
| /users                | POST   | Creates a new user.                           |
| /users                | GET    | Retrieves a list of all users.                |
| /users/{id}           | GET    | Retrieves details of a specific user.         |
| /users/{id}           | PUT    | Updates a user’s details.                     |
| /users/{id}           | DELETE | Deletes a user.                               |
| /users/{id}/role      | PUT    | Assigns or updates the role of a user.        |

---

## 11. **Notifications Module**

The Notifications Module handles the delivery of notifications to users about important events, deadlines, and system updates. This module ensures that users are informed about key actions and reminders.

### Description:
- Notifications can be sent via email, SMS, or in-app messages.
- This module supports creating, scheduling, and managing notifications.

### Screenshots:
*(Insert screenshots showing notification management screens here)*

### Endpoints:

| Endpoint                      | Method | Description                                |
|-------------------------------|--------|--------------------------------------------|
| /notifications                 | POST   | Creates a new notification.                |
| /notifications                 | GET    | Retrieves a list of all notifications.     |
| /notifications/{id}            | GET    | Retrieves details of a specific notification. |
| /notifications/{id}            | PUT    | Updates a notification’s details.          |
| /notifications/{id}            | DELETE | Deletes a notification.                    |
| /notifications/send            | POST   | Sends out notifications immediately.       |


# Modules in Detail

## Authentication & Authorization Module
This module handles user registration, login, password management, and account activation/deactivation. It ensures secure access to the system and manages user roles (e.g., tutor, student, parent/guardian) to control permissions.

## Student Management Module
This module allows for the recording and management of student data, including their bio-data, assigned projects, and the ability for parents/guardians to access and monitor their progress.

## Project Management Module
Projects are central to the student’s learning process. This module allows tutors to assign projects to students, track progress, and ensure milestones are completed in sequence. Each project can be broken down into multiple milestones, which must maintain a specific order.

## Milestone Management Module
Milestones are independent entities that belong to a specific project. This module manages the creation, updating, and deletion of milestones, ensuring they maintain the correct order within their associated projects. Milestones can also be reordered if necessary.

## Assessment and Feedback Module
Tutors can record detailed assessments of student projects, noting challenges and achievements. The system can also auto-generate quizzes or assessments based on project data and milestones. Tutor feedback on lesson plans is used to continually improve AI-generated content.

## Lesson Plan Management Module
This module allows tutors to generate, version, and manage lesson plans using GPT-4. The system can generate multiple versions of a lesson plan, provide dynamic resource recommendations, and integrate auto-generated assessments.

## Resource Management Module
Resources are integral to supporting lesson plans. This module manages the creation, retrieval, and updating of educational resources linked to lesson plans. The system also suggests resources dynamically based on content and past assessments.

## Audit Trail Module
Every action performed in the system is logged in the audit trail, providing a detailed record of who did what and when. This is crucial for maintaining transparency and accountability.

## Dashboard Module
Dashboards provide a high-level overview of key metrics and activities. Tutors, students, and parents/guardians each have tailored dashboards that display relevant information, helping them track progress and stay informed about upcoming events and deadlines.
