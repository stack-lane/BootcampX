# Assignment #002 <br/> Movies Management System (REST API)

> This assignment is due by 5 PM, 14 March 2025.
>
> Once you've completed the assignment, submit it over [here](https://forms.gle/M9CypVx71yXjQC6bA).

- Create a REST API with the following endpoints for a Movies Management system.
- You should implement this API using Node.js + TypeScript + Hono stack.
- Ensure that you handle errors properly for each endpoint (e.g., invalid data, not found, etc.).
- Test the API using tools like Postman, Insomnia or cURL.

---

### 1. `POST /movies`

- **Description**: Add a new movie.
- **Request Body**:
  ```json
  {
    "id": "string",
    "title": "string",
    "director": "string",
    "releaseYear": "number",
    "genre": "string"
  }
  ```
- **Response**:
  - `201 Created`: When the movie is successfully added.
  - `400 Bad Request`: If required fields are missing or invalid.

---

### 2. `PATCH /movies/:id`

- **Description**: Update an existing movie partially by its ID.
- **Request Body**:
  ```json
  {
    "title": "string",
    "director": "string",
    "releaseYear": "number",
    "genre": "string"
  }
  ```
- **Response**:
  - `200 OK`: If the movie was successfully updated.
  - `404 Not Found`: If the movie with the given ID does not exist.
  - `400 Bad Request`: If the fields provided are invalid.

---

### 3. `GET /movies/:id`

- **Description**: Get the details of a movie by its ID.
- **Response**:
  - `200 OK`: Movie details.
  - `404 Not Found`: If the movie with the given ID does not exist.

---

### 4. `DELETE /movies/:id`

- **Description**: Delete a movie by its ID.
- **Response**:
  - `200 OK`: If the movie was successfully deleted.
  - `404 Not Found`: If the movie with the given ID does not exist.

---

### 5. `POST /movies/:id/rating`

- **Description**: Rate a movie (1-5 stars).
- **Request Body**:
  ```json
  {
    "rating": "number"
  }
  ```
- **Response**:
  - `200 OK`: When the movie is successfully rated.
  - `400 Bad Request`: If the rating is not between 1 and 5.
  - `404 Not Found`: If the movie with the given ID does not exist.

---

### 6. `GET /movies/:id/rating`

- **Description**: Get the average rating of a movie by its ID.
- **Response**:
  - `200 OK`: The average rating of the movie.
  - `404 Not Found`: If the movie with the given ID does not exist.
  - `204 No Content`: If the movie has no ratings yet.

---

### 7. `GET /movies/top-rated`

- **Description**: Get a list of movies sorted by the highest rating.
- **Response**:
  - `200 OK`: List of movies sorted by rating (highest first).
  - `404 Not Found`: If no movies exist.

---

### 8. `GET /movies/genre/:genre`

- **Description**: Get all movies belonging to a specific genre.
- **Response**:
  - `200 OK`: List of movies of the specified genre.
  - `404 Not Found`: If no movies are found for the genre.

---

### 9. `GET /movies/director/:director`

- **Description**: Get all movies by a specific director.
- **Response**:
  - `200 OK`: List of movies by the specified director.
  - `404 Not Found`: If no movies are found by the director.

---

### 10. `GET /movies/search`

- **Description**: Search for movies based on a keyword in the title.
- **Query Parameter**: `keyword` (string)
- **Response**:
  - `200 OK`: List of movies whose title contains the given keyword.
  - `404 Not Found`: If no movies match the search keyword.
