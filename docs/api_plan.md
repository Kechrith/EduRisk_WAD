# EduRisk Analytics API Plan

## Purpose

This document plans possible backend API endpoints for EduRisk Analytics.

The current Streamlit app loads data from:

```text
students.csv
```

In future backend chapters, the app can request data from an API instead of reading only from a local CSV file.

The API will help separate:

```text
frontend display
backend logic
database storage
prediction service
```

## Student Data Endpoints

| Method | Endpoint | Purpose |
|---|---|---|
| GET | `/students` | Get all student records |
| GET | `/students/{student_id}` | Get one student by ID |
| POST | `/students` | Add a new student record |
| PATCH | `/students/{student_id}` | Update part of a student record |
| DELETE | `/students/{student_id}` | Delete a student record |

## Example Use

The Streamlit Student Data page could call:

```text
GET /students
```

The backend could return student records as JSON.

## Risk Checker Endpoints

| Method | Endpoint | Purpose |
|---|---|---|
| POST | `/risk-check` | Submit score and attendance to calculate risk |
| POST | `/predict-risk` | Submit student features for ML-based risk prediction |
| GET | `/risk-history` | Get previous risk-check results |

## Example Request

```json
{
  "student_name": "Sok Dara",
  "score": 85,
  "attendance": 90
}
```

## Example Response

```json
{
  "student_name": "Sok Dara",
  "score": 85,
  "attendance": 90,
  "risk_level": "Low Risk",
  "message": "Student appears on track."
}

```

## Dashboard Summary Endpoints

| Method | Endpoint | Purpose |
|---|---|---|
| GET | `/summary/overview` | Get total students, average score, average attendance, high-risk count |
| GET | `/summary/courses` | Get grouped summary by course |
| GET | `/summary/risk-levels` | Get count of students by risk level |
| GET | `/summary/attendance` | Get attendance summary |
| GET | `/summary/scores` | Get score summary |

## Example Overview Response

```json
{
  "total_students": 8,
  "average_score": 71.62,
  "average_attendance": 79.0,
  "high_risk_students": 2
}
```

## Example Risk Summary Response

```json
{
  "Low Risk": 3,
  "Medium Risk": 3,
  "High Risk": 2
}

```


## Filter Query Parameters

The Streamlit Dashboard currently filters data using frontend logic.

In the future, the frontend could send filter values to the backend.

Example endpoint:

```text
GET /students?course=Python&risk_level=High%20Risk&min_attendance=70
```

Possible query parameters:

| Parameter | Meaning | Example |
|---|---|---|
| `course` | Filter by course | `Python` |
| `risk_level` | Filter by risk level | `High Risk` |
| `min_attendance` | Filter by minimum attendance | `70` |
| `min_score` | Filter by minimum score | `60` |
| `max_score` | Filter by maximum score | `100` |

## Example Use

```text
The frontend sends selected filter values.
The backend returns only matching student records.
The frontend displays updated metrics and charts.
```

