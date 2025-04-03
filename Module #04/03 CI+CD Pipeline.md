# CI/CD Pipeline

## What is a CI/CD pipeline?

A CI/CD pipeline is an automated workflow that helps developers build, test, and deploy code faster and more reliably.

- CI (Continuous Integration) means automatically integrating code changes into a shared repository and/or running tests to ensure nothing breaks.
- CD (Continuous Delivery/Deployment) means automatically pushing those changes to production or staging environments with minimal manual effort.

**Why it matters?**

- Reduces human error
- Speeds up release cycles
- Ensures high code quality
- Makes your team more agile and efficient

**Typical CI/CD Flow**

1. Developer pushes code to Git
2. CI server builds the app (and/or runs tests to validate it)
3. If all is good, CD deploys it to staging or productio

**Popular CI/CD Tools**

- GitHub Actions
- GitLab CI
- Azure DevOps
- CircleCI
- Jenkins

> `TL;DR:`
>
> A CI/CD pipeline takes your code from commit to deployment — automatically, quickly, and safely.

## How to set up a CI/CD pipeline betwen GitHub and Azure?

In this guide, we'll walk through how to build a full-fledged CI/CD pipeline where:

- Your code lives on GitHub
- Your containers are managed by Docker
- Your app is deployed to Azure using Azure Container Apps
- Everything is automated via GitHub Actions

### 1. Register a New Azure App for GitHub Integration

Go to Azure Portal → App Registrations and:

1. Search for `App registrations`.
2. On the `App registrations` portal, click on `New registration`.
3. Give an identifiable name for this app (e.g., `GitHubActions`), allot it `Single tenant` access and hit `Register`.
4. Then open this app by clicking on it, go to `Overview` tab and copy over `Application (client) ID` and store it somewhere safe.
5. Then click on `Add a certificate or secret` followed by a click on `New client secret`, give some sensible description like "GitHub Actions Secret", retain default expiration period (usually about 6 months) and hit `Add`.
6. Copy over the `Value` field of the newly created client secret and store it somewhere safe.
7. Sarch for `Microsoft Entra ID`, go over to its `Overview` tab, copy over the `Tenant ID` and store it somewhere safe.
8. Search for `Subscriptions`, go over to an appropriate subscription available on the list, open its `Overview` tab, copy over the `Subscription ID` and store it somewhere safe.
9. Combine all the stored values so far into a string as below (by replacing the placeholders `<...>` appropriately).

```
{"clientSecret":"<client-secret>","subscriptionId":"<subscription-id>","tenantId":"<tenant-id>","clientId":"<client-id>"}
```

10. Now go to your GitHub repo → Settings → Secrets and Variables → Actions, and add a secret with the name `AZURE_GITHUB_ACTIONS` and the above string as its value.

### 2. Create a Resource Group & Assign Permissions

1. On Azure, create a new Resource Group (e.g., `Erbium`).
2. Open that resource, go to its `Access control (IAM)` tab, click on `+Add` and then click on `Add role assignment`.
3. Once there, under the `Roles` tab, switch over to `Privileged administrator roles`, click on `Contributor` role, and click on `Next`.
4. On the `Members` tab, click on `+Select members`, search for the app your created in the above step (e.g. `GitHubActions`), select it, then click on `Select` and finally click on `Review + assign`.
5. On `Review + assign` tab, click on `Review + assign` button once the validations have passed and the button becomes active.

### 3. Dockerise Your App

Make sure your project contains the following files --

1. `Dockerfile`

   It should ideally look as below --

   ```Dockerfile
   FROM node:22.1.0

   WORKDIR /app

   # Copy only needed files
   COPY package*.json ./
   COPY tsconfig*.json ./
   COPY src ./src

   # Copy Prisma folder only if it exists by copying everything, relying on .dockerignore
   COPY . .

   RUN npm install

   RUN if [ -f "./prisma/schema.prisma" ]; then npx prisma generate; else echo "Skipping prisma generate"; fi

   RUN npm run build

   EXPOSE 3000

   CMD ["npm", "start"]
   ```

2. `.dockerignore`

   It should ideally look as below --

   ```.dockerignore
   # Ignore node_modules — will be installed fresh in the container
   node_modules
   npm-debug.log
   yarn.lock
   .pnpm-debug.log

   # Ignore local environment files
   .env
   .env.*

   # Ignore build output
   dist
   build

   # Ignore TypeScript cache & editor configs
   *.tsbuildinfo
   *.log
   .vscode
   .idea

   # Ignore test files and coverage
   __tests__
   coverage
   *.test.ts
   *.spec.ts

   # Mac/Linux/Windows system files
   .DS_Store
   Thumbs.db
   ```

3. `package.json`

   It should look as below --

   ```JSON
   {
     "name": "erbium",
     "type": "module",
     "version": "1.0.0",
     "scripts": {
       "dev": "tsx watch src/index.ts",
       "build": "tsc -p tsconfig.build.json", // ‼️ Notice this change
       "start": "node dist/index.js" // ‼️ Notice this change
     },
     "dependencies": {
       "@hono/node-server": "^1.14.0",
       "hono": "^4.7.5"
     },
     "devDependencies": {
       "@types/node": "^20.11.17",
       "tsx": "^4.7.1",
       "typescript": "^5.8.2" // ‼️ Notice this change
     }
   }
   ```

   > You can install `typescript: ...` by running `npm i -D typescript`.

4. `tsconfig.json`

   It should ideally look as below --

   ```JSON
   {
     "compilerOptions": {
       "lib": ["ESNext"],
       "target": "ESNext",
       "module": "ESNext",
       "moduleDetection": "force",
       "jsx": "react-jsx",
       "allowJs": true,

       // Bundler mode
       "moduleResolution": "bundler",
       "allowImportingTsExtensions": true,
       "verbatimModuleSyntax": true,
       "noEmit": true,

       // Best practices
       "strict": true,
       "skipLibCheck": true,
       "noFallthroughCasesInSwitch": true,

       // Some stricter flags (disabled by default)
       "noUnusedLocals": false,
       "noUnusedParameters": false,
       "noPropertyAccessFromIndexSignature": false
     }
   }
   ```

5. `tsconfig.build.json`

   It should ideally look as below --

   ```JSON
   {
     "extends": "./tsconfig.json",
     "compilerOptions": {
       "noEmit": false,
       "outDir": "./dist",
       "module": "ESNext",
       "target": "ES2020",
       "allowImportingTsExtensions": false
     },
     "include": ["src"]
   }
   ```

Once all of these files are present in your codebase, run `npm i` once to update your `package-lock.json`.

### 4. Create Your GitHub Actions Workflow

In your project, create a folder called `.github` (alongside package.json, at the root of the project), then create a subfolder under it called `workflows` and add a file called `azure_deployment.yml`.

Your `azure_deployment.yml` file should ideally look as below (with changes to `RESOURCE_GROUP`, `CONTAINER_APPS_ENVIRONMENT`, `AZURE_REGION`, etc. as per your set up) --

```YAML
name: Build and Deploy to Azure Container Apps

on:
  push:
    tags:
      - "*"

env:
  AZURE_REGION: centralindia
  RESOURCE_GROUP: Erbium
  CONTAINER_APPS_ENVIRONMENT: ErbiumContainerAppsEnvironment
  LOG_ANALYTICS_WORKSPACE: ErbiumLogAnalyticsWorkspace
  ACR_REGISTRY: erbium.azurecr.io # This has to be unique (at least the `erbium` bit)
  ACR_REPOSITORY_NAME: erbium
  CONTAINER_APP_NAME: erbium
  TARGET_PORT: 3000

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest

    steps:
      # AUTH + CODE
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Azure Login
        uses: azure/login@v2
        with:
          creds: ${{ secrets.AZURE_GITHUB_ACTIONS }}

      # INFRA ENSURE BLOCKS
      - name: Check Resource Group exists
        run: |
          RG_EXISTS=$(az group show \
            --name "${{ env.RESOURCE_GROUP }}" \
            --query name \
            --output tsv 2>/dev/null || echo "")

          if [ -z "$RG_EXISTS" ]; then
            echo "❌ Resource group '${{ env.RESOURCE_GROUP }}' not found."
            echo "👉 Please create it manually first."
            exit 1
          fi

      - name: Ensure Log Analytics Workspace
        run: |
          WORKSPACE_EXISTS=$(az monitor log-analytics workspace show \
            --resource-group "${{ env.RESOURCE_GROUP }}" \
            --workspace-name "${{ env.LOG_ANALYTICS_WORKSPACE }}" \
            --query id \
            --output tsv 2>/dev/null || echo "")

          if [ -z "$WORKSPACE_EXISTS" ]; then
            az monitor log-analytics workspace create \
              --resource-group "${{ env.RESOURCE_GROUP }}" \
              --workspace-name "${{ env.LOG_ANALYTICS_WORKSPACE }}" \
              --location "${{ env.AZURE_REGION }}"
          fi

          WORKSPACE_ID=$(az monitor log-analytics workspace show \
            --resource-group "${{ env.RESOURCE_GROUP }}" \
            --workspace-name "${{ env.LOG_ANALYTICS_WORKSPACE }}" \
            --query customerId -o tsv)

          WORKSPACE_KEY=$(az monitor log-analytics workspace get-shared-keys \
            --resource-group "${{ env.RESOURCE_GROUP }}" \
            --workspace-name "${{ env.LOG_ANALYTICS_WORKSPACE }}" \
            --query primarySharedKey -o tsv)

          echo "::add-mask::$WORKSPACE_ID"
          echo "::add-mask::$WORKSPACE_KEY"
          echo "WORKSPACE_ID=$WORKSPACE_ID" >> $GITHUB_ENV
          echo "WORKSPACE_KEY=$WORKSPACE_KEY" >> $GITHUB_ENV

      - name: Ensure Azure Container Registry (ACR)
        run: |
          REGISTRY_NAME=$(echo "${{ env.ACR_REGISTRY }}" | cut -d'.' -f1)

          ACR_EXISTS=$(az acr show \
            --name "$REGISTRY_NAME" \
            --resource-group "${{ env.RESOURCE_GROUP }}" \
            --query name \
            --output tsv 2>/dev/null || echo "")

          if [ -z "$ACR_EXISTS" ]; then
            az acr create \
              --name "$REGISTRY_NAME" \
              --resource-group "${{ env.RESOURCE_GROUP }}" \
              --sku Standard \
              --admin-enabled true
          fi

          ACR_USERNAME=$(az acr credential show --name "$REGISTRY_NAME" --query username -o tsv)
          ACR_PASSWORD=$(az acr credential show --name "$REGISTRY_NAME" --query passwords[0].value -o tsv)

          echo "::add-mask::$ACR_USERNAME"
          echo "::add-mask::$ACR_PASSWORD"
          echo "ACR_USERNAME=$ACR_USERNAME" >> $GITHUB_ENV
          echo "ACR_PASSWORD=$ACR_PASSWORD" >> $GITHUB_ENV

      - name: Ensure Container Apps Environment
        run: |
          ENV_EXISTS=$(az containerapp env show \
            --name "${{ env.CONTAINER_APPS_ENVIRONMENT }}" \
            --resource-group "${{ env.RESOURCE_GROUP }}" \
            --query name \
            --output tsv 2>/dev/null || echo "")

          if [ -z "$ENV_EXISTS" ]; then
            az containerapp env create \
              --name "${{ env.CONTAINER_APPS_ENVIRONMENT }}" \
              --resource-group "${{ env.RESOURCE_GROUP }}" \
              --location "${{ env.AZURE_REGION }}" \
              --logs-workspace-id "$WORKSPACE_ID" \
              --logs-workspace-key "$WORKSPACE_KEY"
          fi

      # DOCKER BUILD + PUSH
      - name: Set up Docker Buildx
        uses: docker/setup-buildx-action@v3

      - name: Login to ACR
        uses: docker/login-action@v3
        with:
          registry: ${{ env.ACR_REGISTRY }}
          username: ${{ env.ACR_USERNAME }}
          password: ${{ env.ACR_PASSWORD }}

      - name: Build and push Docker image
        uses: docker/build-push-action@v6.15.0
        with:
          context: .
          file: ./Dockerfile
          push: true
          tags: ${{ env.ACR_REGISTRY }}/${{ env.ACR_REPOSITORY_NAME }}:${{ github.ref_name }}

      # CONTAINER APP DEPLOY
      - name: Crate/update Container App
        run: |
          az containerapp up \
            --name "${{ env.CONTAINER_APP_NAME }}" \
            --resource-group "${{ env.RESOURCE_GROUP }}" \
            --environment "${{ env.CONTAINER_APPS_ENVIRONMENT }}" \
            --ingress external \
            --target-port "${{ env.TARGET_PORT }}" \
            --location "${{ env.AZURE_REGION }}" \
            --image "${{ env.ACR_REGISTRY }}/${{ env.ACR_REPOSITORY_NAME }}:${{ github.ref_name }}" \
            --registry-server "${{ env.ACR_REGISTRY }}" \
            --registry-username "${{ env.ACR_USERNAME }}" \
            --registry-password "${{ env.ACR_PASSWORD }}"
```

### 5. Commit, tag and push

Once everything is set up on your project, you can commit your changes, push them to your repository, tag your latest commit with an appropriate version tag and push it as well.

E.g.

```sh
# Commit & Push
git commit -m 'Update to version 2.0.0'
git push origin main

# Tag & Push
git tag 2.0.0
git push origin 2.0.0
```

As soon you push the tag, a workflow should be initiated. You can check it by visiting your `Actions` tab of your GitHub repository.

---

With that, you now have a fully working CI/CD pipeline between GitHub and Azure, powered by Docker and GitHub Actions.

You can:

- Make changes, commit them.
- Create a new tag, push it to GitHub.
- Watch it deploy automagically.
