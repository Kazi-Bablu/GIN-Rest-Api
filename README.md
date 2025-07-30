REST API with Gin Framework
This is a RESTful API built using the Gin framework in Go, featuring user authentication, event management, and an event registration system.

✅ Features
🔐 User authentication (Signup / Login) with JWT tokens

🔑 Password hashing using bcrypt for secure storage

📅 Full CRUD operations for events

✅ Event registration & cancellation

🗄 SQLite database backend

🔒 Middleware for route authentication

⏳ JWT token expiration (2 hours)

📌 API Endpoints

Authentication

| Method | Endpoint  | Description                  |
| ------ | --------- | ---------------------------- |
| POST   | `/signup` | Create a new user account    |
| POST   | `/login`  | Authenticate and receive JWT |

Events (Public)

| Method | Endpoint      | Description          |
| ------ | ------------- | -------------------- |
| GET    | `/events`     | Get all events       |
| GET    | `/events/:id` | Get a specific event |

Events (Authenticated)

| Method | Endpoint               | Description           |
| ------ | ---------------------- | --------------------- |
| POST   | `/events`              | Create a new event    |
| PUT    | `/events/:id`          | Update an event       |
| DELETE | `/events/:id`          | Delete an event       |
| POST   | `/events/:id/register` | Register for an event |
| DELETE | `/events/:id/register` | Cancel registration   |

🗄 Database Schema
The application uses SQLite with these tables:

| Column   | Type    | Description       |
| -------- | ------- | ----------------- |
| id       | INTEGER | Primary Key       |
| email    | TEXT    | Unique user email |
| password | TEXT    | Hashed password   |

events
| Column      | Type     | Description            |
| ----------- | -------- | ---------------------- |
| id          | INTEGER  | Primary Key            |
| name        | TEXT     | Event name             |
| description | TEXT     | Event details          |
| location    | TEXT     | Event location         |
| dateTime    | DATETIME | Event date & time      |
| user\_id    | INTEGER  | Foreign Key → users.id |

registrations

| Column    | Type    | Description                               |
| --------- | ------- | ----------------------------------------- |
| id        | INTEGER | Primary Key                               |
| event\_id | INTEGER | Foreign Key → events.id ON DELETE CASCADE |
| user\_id  | INTEGER | Foreign Key → users.id ON DELETE CASCADE  |




