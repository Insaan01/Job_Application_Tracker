# Job Application Tracker API

A backend system for tracking job applications with full status history,
analytics, and secure authentication.

The system is designed to preserve every state change instead of overwriting
data, enabling accurate tracking, auditing, and insights.

---
## What is an API?

An API (Application Programming Interface) is a contract that allows different
software systems to communicate with each other. It defines a set of endpoints
that accept requests and return structured responses, enabling clients
(frontend apps, mobile apps, or other services) to interact with backend logic
and data in a controlled way.

In this project, the API exposes endpoints over HTTP that allow authenticated
users to create, update, and query job application data without direct access
to the database.
---
## What This Project Does

This project provides a RESTful API for tracking job applications over time.
Instead of overwriting application status, it records every status change as a
historical event. This makes it possible to accurately reconstruct past states,
derive the current status, and run time-based analytics.

The API allows users to:
- Register and authenticate securely using JWT
- Create and manage job applications
- Record application status changes without data loss
- Retrieve current and historical application states
- Identify applications that have been inactive for a period of time

The system is designed as a backend service and can be consumed by any frontend
or client capable of making HTTP requests.

---

## Core Features

- User registration and login (JWT-based authentication)
- Create and manage job applications
- Append-only status history (no data loss)
- Derived current status (not stored redundantly)
- Time-based analytics (stuck applications)
- Optional AI layer (isolated and failure-safe)

---

## Tech Stack

- Python
- FastAPI
- MySQL
- SQLAlchemy
- JWT Authentication
- Pydantic

---

## Key Design Decisions

- **Append-only history**  
  Application status is never overwritten. Every change is recorded.

- **Derived state**  
  Current status is calculated from history, not stored.

- **Stateless authentication**  
  JWT is used instead of sessions for scalability.

- **AI is optional**  
  The system functions fully without AI. AI failures do not affect core logic.

- **Separation of concerns**  
  Database, security, schemas, and business logic are clearly separated.

---

## API Overview

Authentication:
- `POST /register`
- `POST /login`

Applications:
- `POST /applications`
- `POST /applications/{id}/status`
- `GET /applications`
- `GET /applications/{id}`
- `GET /applications/stuck`

System:
- `GET /health`

---

## Running the Project Locally

1. Clone the repository
2. Create a virtual environment
3. Install dependencies

```bash
pip install -r requirements.txt

