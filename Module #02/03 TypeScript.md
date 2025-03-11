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

## TypeScript + NodeJS set-up

### 1. Install the following packages to your Node.js project --

```bash
npm install --save-dev @types/node tsx
```

Your `package.json` should contain the following two important elements (`type: module` and `devDependencies` with `@types/node` and `tsx` on it) --

```JSON
{
  ...
  "type": "module", // very important
  "devDependencies": {
    ...
    "@types/node": "^20.11.17", // very important
    "tsx": "^4.7.1" // very important
    ...
  }
  ...
}
```

> 💡 We're using `tsx` to run TypeScript on NodeJS

### 2. Add a file called `tsconfig.json` with the following contents --

```JSON
{
  "compilerOptions": {
    "target": "ESNext",
    "module": "NodeNext",
    "strict": true,
    "verbatimModuleSyntax": true,
    "skipLibCheck": true,
    "types": ["node"],
    "jsx": "react-jsx",
    "jsxImportSource": "hono/jsx"
  }
}
```

### 3. You can now run your `.ts` files by running `npx tsx <file-name>`.

Or you can create a `start` script as below --

```JSON
{
  "scripts": [
    "start": "tsx src/index.ts" // assuming src/index.ts exists
  ]
}
```

---

# Assignments

## Assignment #001 - Reminders

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
