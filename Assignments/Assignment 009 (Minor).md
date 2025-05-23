# Assignment #009 <br/> Minor | Hacker News DevOps

In this assignment, you'll have to dockerize your `hackernews-server` project and then set up a CI/CD pipeline between GitHub Actions and Azure.

> This assignment is due by 5:00 PM, 4 April 2025.
>
> Once you've completed the assignment, submit it over [here](https://forms.gle/9JYTMEA78E7UCkkQ9).

> Your should compulsorily use your existing `hackernews-server` repository for this assignment.

> In order to complete this assignment, you can refer [CI/CD Pipeline Resource](https://github.com/stack-lane/BootcampX/blob/main/Module%20%2304/03%20CI%2BCD%20Pipeline.md).

## Important Restrictions

- You have to compulsorily create a new app registration for GitHub and call it `GitHubActions <YOUR-USN-IN-BLOCK-LETTERS>` (replace `<YOUR-USN-IN-BLOCK-LETTERS>` with your actual `USN`).
- Your Azure Region should be `centralindia` (Central India).
- Your **Resource Group (RG)** should be named `HackerNews`.
- Your **Azure Container Registry (ACR)** should be named `hackernews<your-usn-in-lowercase>.azurecr.io`.
- Your **ACR Repository** should be named `hackernews`.
- Your **Azure Container Apps Environment (ACAE)** should be named `HackerNewsContainerAppsEnvironment`.
- Your **Log Analytics Workspace (LAW)** should be named `HackerNewsLogAnalyticsWorkspace`.
- Your **Azure Container App (ACA)** should be named `hackernews`.
