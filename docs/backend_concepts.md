## Frontend Responsibilities

The frontend is the user-facing part of the application.

In EduRisk Analytics, the Streamlit frontend is responsible for:

- Showing pages and navigation
- Displaying text, tables, charts, and metrics
- Collecting user input through widgets and forms
- Showing validation messages
- Showing dashboard filters
- Displaying risk-check results
- Presenting data in a clear and professional layout

## Backend Responsibilities

The backend is the server-side part of the application.

In EduRisk Analytics, the backend can be responsible for:

- Receiving requests from the frontend
- Validating submitted data
- Reading student records
- Saving student records
- Connecting to a database
- Applying business rules
- Serving risk prediction results
- Returning JSON responses
- Supporting authentication and security concepts in later chapters

The backend helps the application move from a frontend prototype to a full-stack system.

## Client-Server Communication

Most web applications follow a client-server model.

In EduRisk Analytics:

- The client is the frontend application used by the user.
- The server is the backend application that provides data and services.

The communication flow is:

```text
Frontend client
↓ sends request
Backend server
↓ sends response
Frontend displays result
```

Example:
```text
Streamlit asks for student records.
The backend returns student data as JSON.
Streamlit displays the data as a table or chart.
```

## HTTP Methods

HTTP methods describe the action that the frontend wants the backend to perform.

Common HTTP methods include:

| Method | Meaning | EduRisk Example |
|---|---|---|
| GET | Read data | Get all student records |
| POST | Submit or create data | Submit a risk-check form |
| PUT | Replace data | Replace a full student record |
| PATCH | Update part of data | Update only attendance |
| DELETE | Remove data | Delete a student record |

In the next backend labs, the most common methods will be:

```text
GET
POST
```

## HTTP Status Codes

HTTP status codes tell the frontend whether a backend request succeeded or failed.

| Status Code | Meaning | Frontend Action |
|---:|---|---|
| 200 | OK | Show returned data |
| 201 | Created | Show success message |
| 400 | Bad Request | Show validation warning |
| 404 | Not Found | Show not found message |
| 500 | Server Error | Show error message |

Example:

```text
If the frontend requests a student ID that does not exist,
the backend may return 404 Not Found.
```

## API

API means Application Programming Interface.

An API allows one software component to communicate with another software component.

In EduRisk Analytics:

```text
Streamlit frontend
↓ asks through API
Backend service
↓ returns JSON
Streamlit displays the result
```

## REST

REST is a common style for designing APIs.

REST organizes APIs around resources such as:

- students
- courses
- risk checks
- summaries
- predictions

Example REST-style endpoints:

```text
GET /students
GET /students/S001
POST /risk-check
GET /summary/courses
GET /summary/risk-levels
```

## JSON

JSON is a common data format used by APIs.

Example:

```json
{
  "student_id": "S001",
  "name": "Sok Dara",
  "course": "Web App",
  "score": 85,
  "attendance": 90,
  "risk_level": "Low Risk"
}
```

JSON uses key-value pairs.

Example:

```text
"name": "Sok Dara"
"score": 85
"risk_level": "Low Risk"
```

### FastAPI

FastAPI is useful for:

- Building REST API endpoints
- Returning JSON responses
- Validating request data
- Serving prediction results
- Connecting frontend and backend
- Supporting machine learning services later

In EduRisk Analytics, FastAPI is useful for API services such as:

```text
GET /students
POST /risk-check
GET /summary/risk-levels
POST /predict-risk
```

### Django

Django is useful for:

- Structured backend applications
- Database models
- Admin-style data management
- User and account management concepts
- Larger backend systems

In EduRisk Analytics, Django concepts are useful for:

- Managing student records
- Understanding database-centered backend design
- Understanding admin/data management workflows

### Tool Clarification

```text
FastAPI = API services and ML-ready endpoints
Django = structured backend and database-centered systems
Flask = not used in this course
```