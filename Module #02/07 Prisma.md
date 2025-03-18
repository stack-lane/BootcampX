# Prisma

In order to integrate `prisma` into your `Node.js` + `Hono` project, you'd have to carry out the following steps --

1. Install `prisma` and `@prisma/client` as follows --

   ```bash
   npm install --save-dev prisma
   npm install @prisma/client
   ```

   > `prisma` is the code generator (and therefore to be only added to `devDepencies`) whereas `@prisma/client` is the core ORM that is responsible for building and executing SQL queries basis generated code (thus add it to `dependencies`).

2. Initialise `prisma` on your project by running the following command --

   ```bash
   npx prisma init
   ```

   This will create a `prisma` folder with `schema.prisma` file on it as well as a `.env` file (if it already doesn't exists).

3. Update `.env` with the correct database URL.

   ```bash
   DATABASE_URL="<database-url>"
   ```

   Replace `<database-url>` with the one you got from your DB vendor (Neon, Supabase, Azure, etc.)

4. Add a `model` onto your `schema.prisma` file and then run the following command --

   ```bash
    npx prisma migrate dev --name "<migration-version>"
   ```

   Replace `<migration-version>` with an appropriate name such as `v0`, `v1`, `v2` etc.

   Once the command has run successfuly, it will create a `migrations` folder under your `prisma` folder with some `.sql` files on it.

   > **Reset Stategy**
   >
   > If for whatever reason you want to reset everything and start from scratch, you can do by deleting the `migrations` folder and running `npx prisma migrate reset` and re-run the above command.
   >
   > _Do note that this will erase all the data on your database._

5. Lastly, create a global variable called `prismaClient` in your TypeScript code and use it through-out your project to leverage `prisma`'s code-gen and ORM capabilities.

   ```typescript
   // instantiation (global)
   const prismaClient = new PrismaClient();

   // usage
   const employee = await prismaClient.employee.create({
     data: {
       name: "John Doe",
       department: "Finance",
     },
   });
   ```

   > A typical best practice is to create a file called `prisma.ts` at the root of your `src` folder and export `prismaClient` from within it.

## Next Steps

- Each time you make some changes to `schema.prisma`, you'd have to run `npx prisma migrate dev --name "<updated-migration-name>"` in order to update your DB structure as well.

  > Do not forget to repalce `<updated-migration-name>` with a correct and appropriate name like `v1`, `v2`, `v3`, etc.

- Sometimes you'd have made changes that are too drastic and thus your `prisma` migrate may not be able to handle it. You'd have to then use some alternative strategies as listed [here](https://www.prisma.io/docs/orm/prisma-migrate/understanding-prisma-migrate).
