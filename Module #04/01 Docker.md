# Docker

## What is Docker?

Docker is a platform that allows you to package, distribute, and run applications in isolated environments called containers.

> 💡 Imagine you're a developer, and you want your app to run exactly the same way on your machine, on your teammate’s machine, on the test server, and in production. But each of these environments has different setups, dependencies, and OS-level configurations. Docker solves that.
>
> Docker packages all of your code and its dependencies (OS, run-times, and so on).

There are two key concepts around Docker --

1. Application Code

   This is the core logic of your software — the files you write as a developer. It includes your scripts, backend/frontend code, configuration files, dependencies, etc. But on its own, it doesn’t guarantee consistency across different environments.

   Docker helps solve that by packaging this code with everything it needs to run.

2. Docker Image

   A Docker image is a blueprint or snapshot of your application environment.

   It includes:

   - Your application code
   - OS and OS-level dependencies
   - Libraries, runtimes (like Python, Node.js, Java)
   - Environment setup

   You build an image using a Dockerfile, which tells Docker how to construct this environment.

   > 💡 Think of an `image` like a recipe for a dish.

3. Docker Container

   A container is a running instance of a Docker image. It’s the actual execution environment where your app lives and runs.

   You can spin up multiple containers from the same image — each one isolated and self-contained.

   > 💡 If an image is the recipe, the container is the dish served on the plate.

| **Component**    | **What it is**                      | **Analogy**                     |
| ---------------- | ----------------------------------- | ------------------------------- |
| Application Code | The code you write                  | Ingredients                     |
| Image            | Packaged environment (code + setup) | Recipe                          |
| Container        | Running environment (from image)    | Final dish made from the recipe |

## `Dockerfile`

A `Dockerfile` is a text file that contains a set of instructions for building a Docker image.

It defines:

- The base image to start from (e.g., `node`, `python`, `ubuntu`)
- The application code and dependencies to copy/install
- The commands to run when the container starts (like `npm start` or `python app.py`)

When you run `docker build`, Docker reads the Dockerfile and creates a custom image tailored for your application.

> ⬇️ An example `Dockerfile`

```Dockerfile
# 1. Use Node.js base image
FROM node:22

# 2. Set working directory
WORKDIR /app

# 3. Copy files
COPY . .

# 4. Install dependencies
RUN npm install

# 5. Command to run when container starts
CMD ["npm", "start"]
```

## `.dockerignore`

The `.dockerignore` file tells Docker which files and folders to exclude when building a Docker image.

It works just like a `.gitignore` file — preventing unnecessary files (like logs, local configs, or `node_modules`) from being copied into the Docker image.

**Why it's important?**

- Reduces image size
- Speeds up build times
- Improves security by excluding sensitive or local-only files

> ⬇️ An example `.dockerignore`

```.dockerignore
node_modules
.env
.git
*.log
Dockerfile
README.md
```

> 💡 Always include a `.dockerignore` to keep your images clean, small, and production-ready.

## Docker Container Registry (DockerHub)

A Docker Container Registry is a storage and distribution system for Docker images. It’s where you push (upload) your images after building them and pull (download) them when you need to run containers.

> 💡 Think of it like an app store — but for containers.

**Common Workflow**

- You build your Docker image locally

- Then you push it to a registry (public or private)

- Later, you can pull that image from anywhere and run it as a container

**Common Docker Registries**

- Docker Hub (default, public registry, paid private registry)
- GitHub Container Registry (GHCR)
- Azure Container Registry (ACR)
- Amazon Elastic Container Registry (ECR)
- Google Artifact Registry (GCR)

**Why is a Docker Container Registry needed?**

- Enables easy sharing, versioning, and deployment of container images
- Plays a key role in CI/CD pipelines
- Allows centralized management of images across teams or environments

---

References: [Docker's Official Resources](https://www.docker.com/resources/what-container)
