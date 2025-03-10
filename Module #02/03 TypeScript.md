# TypeScript

TypeScript is a strongly typed programming language that is built on top of JavaScript.

## Fundamentals

1. `let` and `const` (along with type specification & type inference).
2. Basic types - `boolean`, `number`, `string`, `Array`, tuple, `any`, `void`, `undefined`, `null`,
3. Control Flow - `if`, `else`, `switch`.
4. Loops - `for`, `for-in`, `for-of`, `while`, `do-while`.
5. Enums & String Enums
6. Operators -

- `+`, `-`, `*`, `/`, `**`, `%`, `++`, `--`, `=`, `+=`, `-=`, `*=`, `/=`, `**=`
- `==`, `===`, `!=`, `!==`, `>`, `>=`, `<`, `<=`,
- `!`, `||`, `&&`
- `??`, `??=`
- `?:` `typeof`, `as`

7. Functions & Arrow Functions
8. `async` and `await`
9. Classes -

- `private`, `public` & `protected`
- `fields`
- `methods`
- `constructor`
- `extends` & `implements`

10. Interfaces
11. Modules - `import`, `export` & `export default`

# Assignment

## Reminder

- Create a class called `ReminderDatabase` that keeps track of various reminders.
- It should have the following methods on it -

  - `createReminder(...)` - Creates a reminder and stores it.
  - `exists(id: string)` - Checks if a given reminder is present based on its `id`.
  - `getAllReminders()` - Returns all reminders stored so far.
  - `getReminde(id: string)` - Returns a specific reminder, if present, based on its `id` otherwise returns `null`.
  - `removeReminder(id: string)` - Deletes a reminder based on its `id`.
  - `updateReminder(id: string, ...)` - Updates a given reminder based on its `id`.
