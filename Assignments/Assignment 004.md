# Assignment #004 <br/> Reminders Management System (REST API)

> This assignment is due by 5 PM, 13 March 2025.
>
> Once you've completed the assignment, submit it over [here](https://forms.gle/46mamCKKagLwkd9DA).

- Create a REST API for a Reminders Management System with the following class and methods.
- You should implement this API using Node.js + TypeScript + Hono stack.
- Ensure that you handle errors properly for each endpoint (e.g., invalid data, not found, etc.).
- Test the API using tools like Postman, Insomnia or cURL.

---

### 1. `POST /reminders`

- **Description**: Creates a new reminder and stores it.
- **Request Body**:
  ```json
  {
    "id": "string",
    "title": "string",
    "description": "string",
    "dueDate": "string",
    "isCompleted": "boolean"
  }
  ```
- **Response**:
  - `201 Created`: When the reminder is successfully created.
  - `400 Bad Request`: If required fields are missing or invalid.

---

### 2. `GET /reminders/:id`

- **Description**: Retrieves a specific reminder by its `id`.
- **Response**:
  - `200 OK`: Reminder details if found.
  - `404 Not Found`: If the reminder with the given ID does not exist.

---

### 3. `GET /reminders`

- **Description**: Retrieves a list of all reminders stored so far.
- **Response**:
  - `200 OK`: List of all reminders.
  - `404 Not Found`: If no reminders exist.

---

### 4. `PATCH /reminders/:id`

- **Description**: Updates a given reminder by its `id`.
- **Request Body**:
  ```json
  {
    "title": "string",
    "description": "string",
    "dueDate": "string",
    "isCompleted": "boolean"
  }
  ```
- **Response**:
  - `200 OK`: If the reminder was successfully updated.
  - `404 Not Found`: If the reminder with the given ID does not exist.
  - `400 Bad Request`: If the fields provided are invalid.

---

### 5. `DELETE /reminders/:id`

- **Description**: Deletes a reminder by its `id`.
- **Response**:
  - `200 OK`: If the reminder was successfully deleted.
  - `404 Not Found`: If the reminder with the given ID does not exist.

---

### 6. `POST /reminders/:id/mark-completed`

- **Description**: Marks a reminder as `completed`.
- **Response**:
  - `200 OK`: If the reminder is successfully marked as completed.
  - `404 Not Found`: If the reminder with the given ID does not exist.

---

### 7. `POST /reminders/:id/unmark-completed`

- **Description**: Unmarks a reminder as `completed`.
- **Response**:
  - `200 OK`: If the reminder is successfully unmarked as completed.
  - `404 Not Found`: If the reminder with the given ID does not exist.

---

### 8. `GET /reminders/completed`

- **Description**: Retrieves all reminders that are marked as `completed`.
- **Response**:
  - `200 OK`: List of reminders that are marked as completed.
  - `404 Not Found`: If no completed reminders exist.

---

### 9. `GET /reminders/not-completed`

- **Description**: Retrieves all reminders that are not marked as `completed`.
- **Response**:
  - `200 OK`: List of reminders that are not completed.
  - `404 Not Found`: If no uncompleted reminders exist.

---

### 10. `GET /reminders/due-today`

- **Description**: Retrieves all reminders that are due by today.
- **Response**:
  - `200 OK`: List of reminders that are due by today.
  - `404 Not Found`: If no reminders are due today.
