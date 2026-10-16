# Support CRM — Customer Support Ticket Management System

Support CRM is a web-based customer support ticket management system built using Python and FastAPI. It helps customers raise and manage support tickets while allowing support agents to handle customer requests, update ticket status, and assign tickets to agents.

The project focuses on REST API development, database management, authentication, and role-based access control.

## Features

- **Authentication:** Separate registration and login for customers and agents.
- **JWT Authorization:** Token-based authentication for protected endpoints.
- **Customer Management:** Create, view, update, and manage customer profiles.
- **Ticket Management:** Create, retrieve, update, and delete support tickets.
- **Ticket Assignment:** Assign tickets to support agents.
- **Status and Priority Management:** Track tickets according to their status and priority.
- **Role-Based Access Control:** Customers can access their own profiles and tickets, while agents can manage tickets across customers.
- **Pagination and Filtering:** Retrieve tickets in manageable batches and filter them by status or priority.
- **API Documentation:** Explore and test endpoints through FastAPI's interactive Swagger UI.

## Technology Stack

| Technology | Purpose |
|---|---|
| Python | Backend development |
| FastAPI | Building REST APIs |
| SQLAlchemy | Database interaction using ORM |
| SQLite | Persistent database storage |
| Pydantic | Request validation and response schemas |
| JWT | Authentication and token-based access |
| Passlib and bcrypt | Password hashing and verification |
| HTML, CSS, JavaScript | Frontend development |

## Application Architecture

The application follows a modular structure that separates API routes, database operations, data models, validation, and authentication.

- **FastAPI** handles incoming HTTP requests and returns API responses.
- **Routers** organize endpoints for authentication, customers, and tickets.
- **SQLAlchemy** manages communication between the backend and database.
- **Pydantic schemas** validate incoming request data and define response formats.
- **JWT authentication** identifies users accessing protected endpoints.
- **SQLite** stores customer, user, and ticket information.

## User Roles

### Customer

Customers can register, log in, manage their profiles, create support tickets, view their own tickets, and update their ticket details and status.

### Agent

Agents can log in, manage customer records, create tickets for customers, view and update tickets, assign tickets to agents, and filter tickets by status and priority.

## Project Structure

```text
Support-CRM/
├── app/
│   ├── main.py
│   ├── database.py
│   ├── models.py
│   ├── schemas.py
│   ├── auth.py
│   └── routers/
│       ├── utils.py
│       ├── customers.py
│       ├── tickets.py
│       ├── logs.py
│       └── reports.py
├── frontend/
├── requirements.txt
└── README.md
```

### Main Components

- **main.py:** Initializes the FastAPI application, configures middleware, registers routers, and mounts frontend files.
- **database.py:** Configures the SQLite database connection, SQLAlchemy engine, session factory, and database session dependency.
- **models.py:** Defines database models, columns, relationships, and foreign keys.
- **schemas.py:** Defines Pydantic schemas for request validation and API responses.
- **auth.py:** Implements registration, login, and profile-related authentication endpoints.
- **routers/utils.py:** Contains password hashing, JWT utilities, and authenticated-user identification.
- **routers/customers.py:** Handles customer creation, retrieval, updates, and deletion.
- **routers/tickets.py:** Handles ticket creation, retrieval, filtering, updates, assignment, and deletion.

## API Endpoints

### Authentication

| Method | Endpoint | Description |
|---|---|---|
| POST | `/auth/register` | Register an agent account |
| POST | `/auth/login` | Authenticate an agent |
| POST | `/auth/customer/register` | Register a customer |
| POST | `/auth/customer/login` | Authenticate a customer |
| GET | `/auth/me` | Retrieve the authenticated agent's profile |
| GET | `/auth/customer/me` | Retrieve the authenticated customer's profile |

### Customer Management

| Method | Endpoint | Description |
|---|---|---|
| POST | `/customers/` | Create a customer profile |
| GET | `/customers/` | Retrieve all customers |
| GET | `/customers/{customer_id}` | Retrieve a customer by ID |
| PUT | `/customers/{customer_id}` | Update a customer profile |
| DELETE | `/customers/{customer_id}` | Delete a customer profile |

### Ticket Management

| Method | Endpoint | Description |
|---|---|---|
| POST | `/tickets/` | Create a support ticket |
| GET | `/tickets/` | Retrieve tickets with optional filters |
| GET | `/tickets/{ticket_id}` | Retrieve a ticket by ID |
| PUT | `/tickets/{ticket_id}` | Update a support ticket |
| DELETE | `/tickets/{ticket_id}` | Delete a support ticket |

Protected endpoints enforce authentication and access restrictions according to the application's authorization logic.

## Database Design

The application uses SQLAlchemy ORM with SQLite to store and manage structured data.

- **User:** Stores agent account details, credentials, and role information.
- **Customer:** Stores customer profile information.
- **Ticket:** Stores ticket title, description, status, priority, creation date, customer association, and optional agent assignment.

A customer can have multiple tickets. Each ticket is associated with a customer and can optionally be assigned to an agent.

## Authentication and Security

The application uses JWTs to authenticate users and protect API endpoints. Passwords are hashed before being stored in the database and verified during login.

Role-based authorization and ownership checks help ensure that customers can access only their own profiles and tickets, while agents can manage tickets across customers.

## Installation and Setup

### 1. Clone the repository

```bash
git clone <https://github.com/gaurijolly09/SUPPORT-CRM.git>
cd Support-CRM
```

Replace `<YOUR_REPOSITORY_URL>` with your repository's Git URL.

### 2. Create a virtual environment

```bash
python -m venv venv
```

Activate it on Windows:

```bash
venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Start the application

```bash
uvicorn app.main:app --reload
```

### 5. Access the API documentation

Open the following URL in your browser:

`http://127.0.0.1:8000/docs`

## Future Enhancements

- Add automated unit and integration tests.
- Improve validation and error handling.
- Strengthen production security and secret management.
- Add advanced ticket search and reporting capabilities.
- Deploy the application in a production environment.
