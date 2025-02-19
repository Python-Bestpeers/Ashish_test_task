# Employee Recognition System (Mini Kudos App)

## Overview
The **Employee Recognition System** is a Django-based application that allows employees to give "Kudos" (appreciation) to their colleagues. It enforces **role-based access control**, includes **background task processing** for notifications, and ensures secure authentication.

## Tech Stack
- **Django** - Backend framework
- **Django Rest Framework (DRF)** - REST API development
- **Celery** - Asynchronous task processing
- **Redis** - Message broker for Celery
- **PostgreSQL** - Database
- **djangorestframework-simplejwt** - JWT authentication

## Features

### 1. Authentication & Permissions
- **JWT-based authentication** using `djangorestframework-simplejwt`.
- Role-based access control:
  - **Admin**: Manage users, assign roles, and view all kudos.
  - **Manager**: Can send kudos to any user without restrictions.
  - **Employee**: Can send a maximum of **3 kudos per week**.
- API access is **restricted based on roles**.

### 2. Kudos System
- Employees can send kudos (appreciation) to colleagues.
- Employees have a **weekly limit of 3 kudos**, enforced via validation.
- Managers have **no limit** on sending kudos.
- Kudos **cannot be sent to oneself**.

### 3. Celery for Background Tasks
- **Celery** is used to send email notifications when a kudo is given.
  - **Emails are sent** to both the **recipient** and the **admin**.
- A **scheduled Celery task** resets the **weekly kudo count every Sunday at midnight**.

## Setup Instructions
### Prerequisites
Ensure you have the following installed:
- Python 3.8+
- PostgreSQL
- Redis
- Docker (for running Redis easily)

## Testing
To run tests:
```sh
pytest
```

and configure on github actions

