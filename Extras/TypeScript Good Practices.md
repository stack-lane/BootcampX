# TypeScript Good Practices

## File and Folder Naming

- **File Names**: Use kebab-case (all lowercase with hyphens) for file names. Example: `user-service.ts`, `main-app.component.ts`.
- **Folder Names**: Use kebab-case for folder names as well. Example: `core-services`, `ui-components`.

## Variable and Function Naming

- **Variables**: Use `camelCase` for variable names. Example: `userName`, `userAge`.
- **Constants**: Use `UPPER_CASE` for constants. Example: `MAX_USERS`, `API_URL`.
- **Functions**: Use `camelCase` for function names. Example: `getUserName()`, `setUserAge()`.

## Class and Interface Naming

- **Classes**: Use `PascalCase` for class names. Example: `UserService`, `AppComponent`.
- **Interfaces**: Use `PascalCase` for interface names. Example: `MainUser`, `CoreService`.

## Type and Enum Naming

- **Types**: Use `PascalCase` for type aliases. Example: `UserType`, `ServiceType`.
- **Enums**: Use `PascalCase` for enum names and `UPPER_CASE` for enum values. Example:
  ```typescript
  enum UserRole {
    ADMIN,
    USER,
    GUEST,
  }
  ```

## Code Structuring

- **Imports**: Group imports by:

  1. Standard library imports.
  2. Third-party library imports.
  3. Local module imports.

  Example:

  ```typescript
  // 1. Standard-library imports
  import { Component } from "@angular/core";

  // 2. Third-party library imports
  import { Observable } from "rxjs";

  // 3. Local module imports
  import { UserService } from "./services/user-service";
  ```

- **Exporting**: Prefer named exports over default exports for better maintainability.

  ```typescript
  // Named export
  export class UserService { ... }

  // Importing named export
  import { UserService } from './services/user-service';
  ```

## Comments

- **Single-line Comments**: Use `//` for single-line comments.
- **Multi-line Comments**: Use `/* ... */` for multi-line comments.
- **Documentation Comments**: Use `/** ... */` for documentation comments, especially for public APIs.

  Example:

  ```typescript
  /**
   * Gets the user name.
   * @param userId The ID of the user.
   * @returns The name of the user.
   */
  function getUserName(userId: number): string { ... }
  ```

## Miscellaneous

- **Indentation**: Use 2 spaces for indentation.
- **Semicolons**: Always use semicolons at the end of statements.
- **Quotes**: Prefer double quotes for strings. Example: `"Hello, world!"`.
- **Trailing Commas**: Use trailing commas in multi-line objects and arrays.

  Example:

  ```typescript
  const user = {
    name: "John",
    age: 30,
  };

  const users = ["John", "Jane"];
  ```

By following these conventions, you can ensure that your `TypeScript` code is clean, consistent, and easy to maintain.
