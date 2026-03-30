# Mergington High School Activities API

A super simple FastAPI application that allows students to view and sign up for extracurricular activities.

## Features

- View all available extracurricular activities
- Create a student account and sign in
- Sign up for activities as the authenticated student
- Unregister yourself from activities

## Getting Started

1. Install the dependencies:

   ```
   pip install fastapi uvicorn
   ```

2. Run the application:

   ```
   python app.py
   ```

3. Open your browser and go to:
   - API documentation: http://localhost:8000/docs
   - Alternative documentation: http://localhost:8000/redoc

## API Endpoints

| Method | Endpoint                           | Description                                                         |
| ------ | ---------------------------------- | ------------------------------------------------------------------- |
| GET    | `/activities`                      | Get all activities with their details and current participant count |
| POST   | `/auth/signup`                     | Create a student account (email, name, password)                   |
| POST   | `/auth/login`                      | Sign in and receive a bearer token                                 |
| GET    | `/auth/me`                         | Get current student profile from bearer token                       |
| POST   | `/auth/logout`                     | Invalidate the current bearer token                                |
| POST   | `/activities/{activity_name}/signup` | Sign up authenticated student for an activity                     |
| DELETE | `/activities/{activity_name}/unregister` | Unregister authenticated student from an activity              |

Protected endpoints require an `Authorization` header in the form:

```
Authorization: Bearer <token>
```

## Data Model

The application uses a simple data model with meaningful identifiers:

1. **Activities** - Uses activity name as identifier:

   - Description
   - Schedule
   - Maximum number of participants allowed
   - List of student emails who are signed up

2. **Students** - Uses email as identifier:
   - Name
   - Password hash

All data is stored in memory, which means data will be reset when the server restarts.
