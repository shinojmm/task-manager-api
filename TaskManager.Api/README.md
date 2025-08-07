# Task Manager API (.NET 8)

A simple REST API for managing personal tasks, built using .NET 8 and Entity Framework Core.

## Features

- User registration and JWT authentication
- CRUD operations for tasks
- Each user can manage their own tasks
- Task status and due date tracking

## Getting Started

### Prerequisites

- [.NET 8 SDK](https://dotnet.microsoft.com/download)
- (Optional) [SQLite](https://www.sqlite.org/index.html) CLI

### Setup

1. **Clone the repo**  
   `git clone <your-repo-url>`
2. **Navigate to project directory**

3. **Install dependencies**  
   `dotnet restore`

4. **Apply migrations & create database**  
   ```
   dotnet tool install --global dotnet-ef
   dotnet ef migrations add InitialCreate
   dotnet ef database update
   ```

5. **Run the API**  
   `dotnet run`

6. **Swagger UI**  
   Go to `https://localhost:5001/swagger` in your browser to test the endpoints.

## API Endpoints

### Auth

- `POST /api/auth/register`  
  `{ "username": "user", "password": "pass" }`
- `POST /api/auth/login`  
  `{ "username": "user", "password": "pass" }`  
  Returns: `{ "token": "..." }`

### Tasks (Requires Bearer JWT token)

- `GET /api/tasks`  
  Returns all tasks for the logged-in user.
- `POST /api/tasks`  
  `{ "title": "...", "description": "...", "dueDate": "2025-01-01T00:00:00", "status": 0 }`
- `PUT /api/tasks/{id}`
- `DELETE /api/tasks/{id}`

## License

MIT