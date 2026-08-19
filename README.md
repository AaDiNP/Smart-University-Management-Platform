# Smart University Management Platform

An automation-based university management system built using **n8n** to simplify student registration, attendance monitoring, assignment evaluation, grade processing, and workflow error handling.

The project integrates **Google Sheets, Google Drive, Gmail, OpenAI, Webhooks, and n8n** to automate repetitive academic and administrative tasks.

---

## Project Overview

Universities handle large amounts of repetitive work such as processing registrations, tracking attendance, evaluating assignments, publishing grades, and communicating with students.

The **Smart University Management Platform** uses multiple n8n workflows to automate these processes.

The system contains five sub-workflows:

1. Student Registration & Enrollment
2. Attendance Management & Low Attendance Alerts
3. AI Assignment Evaluation
4. Scheduled Grade Processing
5. Global Error Handler & Audit Log

---

## Objectives

The main objectives of the project are:

- Digitize student registration and academic administration
- Automate attendance calculation and monitoring
- Send automatic low-attendance warnings
- Automate assignment evaluation using AI
- Store academic records using Google Sheets
- Automate scheduled grade processing
- Send personalized academic notifications
- Maintain workflow error logs
- Notify administrators when workflow failures occur

---

## Technologies Used

| Technology | Purpose |
|---|---|
| n8n | Workflow automation and orchestration |
| Google Sheets | Student, attendance, evaluation, and audit records |
| Google Drive | Assignment submission storage |
| Gmail | Automated student and administrator emails |
| OpenAI | AI-based assignment evaluation |
| Webhooks | Receiving attendance data |
| JavaScript | Attendance and grade calculations |
| Schedule Trigger | Weekly automated grade processing |

---

# System Architecture

The project follows a modular architecture where each major university process is implemented as a separate n8n workflow.

```text
Student Registration
        |
        v
Google Sheets -> n8n -> Enrollment Email


Attendance Data
        |
        v
Webhook -> Calculate Attendance -> Google Sheets
                              |
                              v
                      Attendance < 75%?
                       /             \
                     Yes              No
                      |                |
                Warning Email      Log Attendance


Assignment Submission
        |
        v
Google Drive
        |
        v
Download File -> Extract PDF Text
        |
        v
OpenAI Evaluation
        |
        v
Google Sheets -> Result Email


Every Friday at 5 PM
        |
        v
Read Grades
        |
        v
Calculate Average & Grade Status
        |
        v
Distinction / Pass / Fail
        |
        v
Academic Summary Email


Workflow Failure
        |
        v
Global Error Handler
        |
        v
Extract Error Details
        |
        +----> Audit Log
        |
        +----> Admin Alert
