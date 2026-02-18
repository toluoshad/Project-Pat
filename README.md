# Full-Stack Project Collaboration Platform (Project Pat)

## Overview
This project is a full-stack web-based project collaboration system built using Django REST Framework (DRF) and JavaScript (ES6).

The application allows authenticated users to:
Create and manage projects
Assign members to projects
Track project status (Ongoing → Completed)
Enforce role-based access control
Secure endpoints using JWT authentication

The system demonstrates backend API architecture, relational database design, secure authentication, and dynamic frontend–backend integration.

## Architecture
The application follows a clear separation of concerns:
Frontend (HTML / CSS / JavaScript)
↓
REST API Layer (Django REST Framework)
↓
Database Layer (SQLite via Django ORM)

Key architectural principles implemented:
RESTful API design
Token-based authentication (JWT)
Role-based authorization
Many-to-Many relational modeling
Secure protected endpoints
Asynchronous client-side API integration

## Features
### Authentication & Security

JWT-based authentication
Protected API endpoints using IsAuthenticated
Authorization headers for secure API access
Role-based access control:
    Only project creators can add members
    Only authenticated users can access projects
Proper HTTP status handling (401, 404, etc.)

### Project Management

Create new projects
Update project status (Ongoing / Completed)
Prevent reverting completed projects
Dynamic project rendering on frontend
Real-time UI updates after state changes

### Member Management

Many-to-Many relationship between Users and Projects
Add members to projects (creator-only permission)
Exclude existing members from selection dropdown
Display project member count
Owner identification inside project view

### Frontend Implementation

Dynamic DOM rendering via Fetch API
Async/Await API handling
Modal-based UI using SweetAlert
Event propagation control (event.stopPropagation)
Conditional UI rendering based on user role
Secure token storage via localStorage

## Technical Concepts Demonstrated

### Backend

Django REST Framework APIViews
Serializer validation and structured JSON responses
Permission classes (IsAuthenticated)
Relational database modeling
Query filtering and data transformation
HTTP method handling (GET, POST, PUT)

### Frontend

Fetch API with Authorization headers
Template literals for dynamic HTML generation
State management via API refresh
Error handling and promise management
Debugging asynchronous authentication issues

### Database

Many-to-Many relationships
ForeignKey ownership model (creator → project)
ORM-based querying
Normalized relational schema design

## Technology Stack

### Languages

Python
JavaScript (ES6+)
SQL
HTML5
CSS3

### Frameworks & Libraries

Django
Django REST Framework
SimpleJWT
SweetAlert2

### Database

SQLite

### Tools

Insomnia (API testing)
Git
Browser Developer Tools

## API Endpoints
Method	Endpoint	Description
POST	/projects/create-project/	Create a new project
GET	/projects/get-all-projects/	Retrieve all projects
PUT	/projects/update-project/<id>/	Update project status
GET	/projects/<id>/members/	Retrieve project members
POST	/projects/<id>/add-member/	Add member to project
GET	/projects/users/	Retrieve available users
GET	/api/user-profile-drop/	Retrieve authenticated user

All endpoints require JWT authentication.

## Installation
### 1. Clone Repository
git clone https://github.com/yourusername/project-name.git
cd project-name

### 2. Create Virtual Environment
python -m venv venv
source venv/bin/activate      (Mac/Linux)
venv\Scripts\activate         (Windows)

### 3. Install Dependencies
pip install -r requirements.txt

### 4. Apply Migrations
python manage.py migrate

### 5. Run Development Server
python manage.py runserver

Backend runs at:

http://127.0.0.1:8000/

## Authentication Flow

1. User logs in

2. JWT access token is returned

3. Token is stored in localStorage

4. Token is attached to all API requests:

Authorization: Bearer <access_token>

5. Backend validates token before granting access

## Challenges & Problem Solving

Resolved JWT authentication issues (401 errors)
Debugged frontend-backend routing mismatches (404 errors)
Implemented conditional UI rendering based on authenticated user
Prevented event collision between modal triggers and status toggles
Ensured consistent API base URL configuration

## Future Improvements

Deploy to production (Render / Railway)
Switch to PostgreSQL
Add pagination and filtering
Add project analytics dashboard
Implement unit tests
Dockerize application
Add CI/CD pipeline

Author

Your Name Tolu
GitHub: https://github.com/toluoshad

LinkedIn: https://www.linkedin.com/in/tolu-oshadiya/
