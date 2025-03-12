# Hono

- In order to create a Hono project, you can run the following command --

```bash
npm create hono@latest <project-name>
```

> 💡 Replace `<project-name>` with an appropriate project name of your choice (remember to use `kebab-case`).

- Pick `nodejs` when asked to choose a template and `npm` when asked to pick a package manager.

- Once you project is created, replace the contents of your `tsconfig.json` with the ones below --

```json
{
  "compilerOptions": {
    "target": "ESNext",
    "module": "ESNext",
    "moduleResolution": "node",
    "strict": true,
    "verbatimModuleSyntax": true,
    "skipLibCheck": true,
    "types": ["node"],
    "jsx": "react-jsx",
    "jsxImportSource": "hono/jsx"
  }
}
```

- You can check out all the documentation on `Hono` from over [here](https://hono.dev/docs/api/hono).
