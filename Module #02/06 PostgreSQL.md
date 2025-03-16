# Postgres / PostgreSQL

- Head over to [postgresql.org](https://www.postgresql.org/download) and install PostgreSQL based on your OS.

## Postgres' Client-Server Architecture

Your Postgres is architected as `server` that can take in requests from one or more `clients`.

- What that means is that your database is created, managed and hosted by the Postgres server process (called `postgres`) and then you create clients to connect to it.

> All of your core PostgreSQL is written in C. But its peripheral tools like pgAdmin, StackBuilder, etc. are written in other languages like Python and JavaScript.
>
> But, most of its clients are written in languages other than C (except for its official command-line client `psql` and its C client `libpq`, which are both written in C).

- This client-server architecture ensures that your core DB is walled-off/secured away from unintended access and interactions with it are controlled.

### `psql` Official Command-Line Client

- `psql` is the official command-line client for `Postgres` servers.

Check out this [cheat sheet](https://gist.github.com/Kartones/dd3ff5ec5ea238d4c546) for a quick glance of `psql`.

### `pgAdmin` GUI Client

- `pgAdmin` is a GUI-based client to your Postgres server.
- It provides interactive tools to perform various DB related tasks, right from adminstration to table & row creation.

Head over to [pgadmin.org](https://www.pgadmin.org) and check it out.

## Neon (Hosted PostgreSQL)

- Neon is a platform which hosts a Postgres database on its servers and gives you access to it.
- This way, you don't have to manage hosting a Postgres instance yourself.
- You can concentrate on writing business-relevant code rather than Postgres-specific boilerplate code.

Head over to [neon.tech](https://neon.tech), create a project and start using a fully-managed & hosted Postgres server.

## Verifying Installation

After installing PostgreSQL, you can verify the installation by running the following command in your terminal:

```sh
psql --version
```

This should display the version of `psql` installed on your system.

## Basic SQL Commands

Here are some basic SQL commands to get you started with PostgreSQL:

### Creating a Database

```sql
CREATE DATABASE mydatabase;
```

### Connecting to a Database

```sh
psql -d mydatabase
```

### Creating a Table

```sql
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(100) UNIQUE NOT NULL
);
```

### Inserting Data

```sql
INSERT INTO users (name, email) VALUES ('John Doe', 'john.doe@example.com');
```

### Querying Data

```sql
SELECT * FROM users;
```

## Database Backup and Restore

### Backup a Database

You can back up a PostgreSQL database using the `pg_dump` utility:

```sh
pg_dump mydatabase > mydatabase_backup.sql
```

### Restore a Database

You can restore a PostgreSQL database using the `psql` utility:

```sh
psql mydatabase < mydatabase_backup.sql
```

## Running a SQL Script

You can run a SQL script using the `psql` utility. Assuming you have a script named `script.sql`, you can execute it as follows:

```sh
psql -d mydatabase -f script.sql
```

This will run the SQL commands in `script.sql` against the `mydatabase` database.
