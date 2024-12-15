# TaskManager

A Spring Boot application that provides a simple RESTful API to manage tasks, perform basic math operations, and handle string manipulations. The application also demonstrates custom exception handling for both arithmetic and generic errors.

## Table of Contents
- [Features](#features)
    - [Task Management](#task-management)
    - [Math Operations](#math-operations)
    - [String Manipulations](#string-manipulations)
- [Project Structure](#project-structure)
- [Endpoints](#endpoints)
    - [Task Management Endpoints](#task-management-endpoints)
    - [Math Operation Endpoints](#math-operation-endpoints)
    - [String Manipulation Endpoints](#string-manipulation-endpoints)
- [Error Handling](#error-handling)
- [Build and Run](#build-and-run)
- [Examples](#examples)

## Features

### Task Management
- Store tasks in memory using a simple data structure (e.g., `HashMap` or `List`).
- Create, retrieve, and delete tasks.
- A task typically has an `id`, `name`, and a `completed` status.

### Math Operations
- Perform basic arithmetic operations: addition, subtraction, multiplication, and division.
- Endpoints return the result of the operation in JSON format.
- Proper handling of invalid operations (e.g., division by zero).

### String Manipulations
- Reverse a given string.
- Count the vowels in a given string.
- Convert a given string to uppercase.

## Project Structure
The project follows a standard Spring Boot structure:


- **controller**: Contains REST controller classes that define the endpoints.
- **service**: Contains business logic for tasks, math, and string operations.
- **model**: Contains data model classes, such as `Task`.
- **exception**: Contains custom exception classes and global exception handlers.

## Endpoints

### Task Management Endpoints
**Base URL:** `/tasks`

| HTTP Method | Endpoint      | Description         | Example Request Body                                 |
|-------------|---------------|---------------------|------------------------------------------------------|
| GET         | `/tasks`      | Get all tasks       | N/A                                                  |
| POST        | `/tasks`      | Add a new task      | `{"id": 1, "name": "Sample Task", "completed": false}` |
| DELETE      | `/tasks/{id}` | Delete task by ID   | N/A                                                  |

### Math Operation Endpoints
**Base URL:** `/math`

| HTTP Method | Endpoint          | Description         | Example Query Parameters |
|-------------|-------------------|---------------------|--------------------------|
| GET         | `/math/add`       | Add two numbers     | `?a=5&b=10`             |
| GET         | `/math/subtract`  | Subtract two numbers| `?a=10&b=5`             |
| GET         | `/math/multiply`  | Multiply two numbers| `?a=5&b=4`              |
| GET         | `/math/divide`    | Divide two numbers  | `?a=10&b=2`             |

### String Manipulation Endpoints
**Base URL:** `/strings`

| HTTP Method | Endpoint            | Description                 | Example Query Parameters |
|-------------|---------------------|-----------------------------|--------------------------|
| GET         | `/strings/reverse`  | Reverse the given string    | `?input=hello`          |
| GET         | `/strings/count-vowels` | Count vowels in the string | `?input=education`      |
| GET         | `/strings/to-upper` | Convert string to uppercase | `?input=hello world`    |

## Error Handling
- For arithmetic errors (e.g., division by zero), the API returns **400 BAD REQUEST** along with a descriptive error message in JSON format.
- For generic or unexpected exceptions, the API returns **500 INTERNAL SERVER ERROR** with a general error message.

## Build and Run
1. **Prerequisites**:
    - Java 17 or later
    - Maven 3.8+ or Gradle (if using)

2. **Clone the repository**:
   ```bash
   git clone https://github.com/muz2002/TASK-MANAGER.git

3. **Build the project**:
   ```bash
   gradle build
4. **Run the application**:
   ```bash
   gradle bootRun

## Examples
- **Get All Tasks**:
  ```bash
  curl -X GET http://localhost:8080/tasks
  ```
  Response:
  ```json
    [
  {
    "id": 1,
    "name": "Sample Task",
    "completed": false
  }
    ]
  ```
  - **Add a Task**:
    ```bash
    curl -X POST http://localhost:8080/tasks \
       -H "Content-Type: application/json" \
       -d '{"id": 2, "name": "Another Task", "completed": false}'
    **Response:**
    ```json
    {
      "id": 2,
      "name": "Another Task",
      "completed": false
    }
    ```
    - **Add Two Numbers**:
    ```bash
    curl http://localhost:8080/math/add?a=5&b=10
    
    **Response:**
    ```json
    {
      "result": 15
    }
    ```
    - **Reverse a String**:
    ```bash
    curl http://localhost:8080/strings/reverse?input=hello
    
    **Response:**
    ```json
    {
      "result": "olleh"
    }
    ```