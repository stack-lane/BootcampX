# Assignment #003 <br/> Fitness Tracker

> This assignment is due by 5 PM, 12 March 2025.
>
> Once you've completed your assignment, submit it over [here](https://forms.gle/5YAxiKLUnE8xj9ZX7).

Create a series of methods that will make up a Fitness Tracker mechanism. Throw meaningful errors where appropriate.

- `addUser(...)` — Add a user with properties: id, name, age, weight, height.
- `logWorkout(userId: string, workout: Workout)` — Add a workout log.
- `getAllWorkoutsOf(userId: string)` — Get all workouts for a user.
- `getAllWorkoutsByType(userId: string, type: string)` — Get workouts filtered by type (e.g., "running", "yoga").
- `getUsers()` — Return all users.
- `getUser(id: string)` — Get user details.
- `updateUser(id: string, updatedFields: Partial<Omit<User, 'id'>>): void` — Update user details.
