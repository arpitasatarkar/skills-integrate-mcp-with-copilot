# Mergington High School Activities API

A super simple FastAPI application that allows students to view and sign up for extracurricular activities.

## Features

- View all available extracurricular activities
- View activity participants
- Register and unregister students as a teacher

## Getting Started

1. Install the dependencies:

   ```
   pip install fastapi uvicorn
   ```

2. Configure teacher credentials in the environment, then run the application:

   ```
   export TEACHER_USERNAME="teacher"
   export TEACHER_PASSWORD="replace-with-a-strong-password"
   ```

   ```
   cd src
   uvicorn app:app --reload
   ```

   Keep these values out of source control. In a deployed environment, set them
   through its secret manager and serve the application over HTTPS.

3. Open your browser and go to:
   - API documentation: http://localhost:8000/docs
   - Alternative documentation: http://localhost:8000/redoc

## API Endpoints

| Method | Endpoint                                                             | Description                                                         |
| ------ | -------------------------------------------------------------------- | ------------------------------------------------------------------- |
| GET    | `/activities`                                                        | Get all activities with their details and current participant count |
| GET    | `/auth/teacher`                                                       | Verify teacher credentials                                          |
| POST   | `/activities/{activity_name}/signup?email=student@mergington.edu`    | Register a student (teacher authentication required)                |
| DELETE | `/activities/{activity_name}/unregister?email=student@mergington.edu` | Unregister a student (teacher authentication required)               |

## Data Model

The application uses a simple data model with meaningful identifiers:

1. **Activities** - Uses activity name as identifier:

   - Description
   - Schedule
   - Maximum number of participants allowed
   - List of student emails who are signed up

2. **Students** - Uses email as identifier:
   - Name
   - Grade level

All data is stored in memory, which means data will be reset when the server restarts.
