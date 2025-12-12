# Koa Sleep API

The backend API for Koa Sleep - an open-source web dashboard for viewing and analyzing your Fitbit sleep data. Built with Postgres, Express, Node.js, and TypeScript.

[Live Deployment](https://koasleep.dev)

## Development Setup

This section outlines the steps required to set up your local development environment for the API.

### 1. Prerequisites

Ensure your system meets the following requirements:

* **Node.js:** `v20.0.0` or later.
    * _Recommendation:_ Use a Node.js version manager like [NVM (Node Version Manager)](https://github.com/nvm-sh/nvm) for easy switching between Node.js versions.
* **npm:** `v8.0.0` or later (usually bundled with Node.js).
* **Docker:** We use Docker Compose to manage a locally running `postgreSQL` server during development.

### 2. Getting the Code

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/loganhagen/koa-sleep-api.git
    cd koa-sleep-api
    ```

### 3. Environment Configuration

The application uses environment variables for configuration.

1.  **Create `.env` file:**
    * **`.env` (example):**
        ```
        EXPRESS_PORT=5000
        DATABASE_URL="postgresql://admin:admin@localhost:5432/koa_sleep?schema=public"
        CORS_ALLOWED_ORIGINS=https://localhost:3000
        JWT_SECRET=yourjwtsecrethere
        BACKEND_URL=http://localhost:5000
        ```

        See the local `.env.example` for a more up-to-date version.

### 4. Install Dependencies

Install the project's dependencies.

```
npm install
```

### 5. Seed the Database

Follow the provided steps in the root of the backend directory.

**NOTE**: Ensure your database of choice is running and its connection string is in `.env`. 
  I am using a local Postgres container- you can find the Docker Compose file in `https://github.com/Koa-Sleep/koa-sleep-infra`.

1. **Apply migrations:**
    ```bash
    npx prisma migrate dev 
    ```

2. **Use the seed file:**
    ```bash
    npx prisma db seed
    ```

3. **Check database contents (optional):**
    ```bash
    npx prisma studio
    ```

## Versioning

### Front-End

1. Check-out a new branch (Ex. `chore/bump-version`).
2. Run `npm version patch --no-git-tag-version -m "chore: bump version to %s"`
3. Push to remote and create a PR.
