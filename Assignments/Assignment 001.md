# Assignment #001 <br/> Reminders

> This assignment is due by 12:30 PM, 11 March 2025.
>
> Once you've completed your assignment, submit it over [here](https://forms.gle/qm9iS17vmK86XeNy9).

- Create a class called `ReminderDatabase` that keeps track of various reminders.
- It should have the following methods on it -

  - `createReminder(...)` - Creates a reminder and stores it.
  - `exists(id: string)` - Checks if a given reminder is present based on its `id`.
  - `markReminderAsCompleted(id: string)` - Marks a reminder as `completed`.
  - `unmarkReminderAsCompleted(id: string)` - Unmarks a reminder as `completed`.
  - `getAllReminders()` - Returns all reminders stored so far.
  - `getReminder(id: string)` - Returns a specific reminder, if present, based on its `id` otherwise returns `null`.
  - `getAllRemindersMarkedAsCompleted()` - Returns all reminders that are marked as `completed`.
  - `getAllRemindersNotMarkedAsCompleted()` - Returns all reminders that are not marked as `completed`.
  - `getAllRemindersDueByToday()` - Returns all reminders that are due by today.
  - `updateReminder(id: string, ...)` - Updates a given reminder based on its `id`.
  - `removeReminder(id: string)` - Deletes a reminder based on its `id`.
