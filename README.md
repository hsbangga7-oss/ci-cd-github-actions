# CI/CD Pipeline Automation using GitHub Actions and AWS S3

## Project Overview
This project demonstrates a complete **CI/CD pipeline** that automatically deploys a static website to **Amazon S3** using **GitHub Actions**.  
Any change pushed to the `main` branch triggers an automated deployment, removing the need for manual uploads and ensuring consistent releases.

---
## Repository Structure
.
├── .github/
│   └── workflows/
│       └── deploy.yml
│
├── website/
│   ├── index.html
│   └── style.css
│
└── README.md
---
## Architecture

```
┌──────────────────────┐
│      Developer       │
│                      │
│  Edit HTML / CSS     │
└──────────┬───────────┘
           │
           │ git push
           ▼
┌──────────────────────┐
│   GitHub Repository  │
│      main branch     │
└──────────┬───────────┘
           │
           │ workflow trigger
           ▼
┌────────────────────────────────┐
│       GitHub Actions           │
│                                │
│  ┌──────────────────────────┐  │
│  │ Checkout repository      │  │
│  ├──────────────────────────┤  │
│  │ Configure AWS credentials│  │
│  ├──────────────────────────┤  │
│  │ Sync website files       │  │
│  └──────────────────────────┘  │
└───────────────┬────────────────┘
                │
                │ aws s3 sync
                ▼
┌──────────────────────────────┐
│          Amazon S3           │
│                              │
│   Static Website Hosting     │
│                              │
│   ├── index.html             │
│   └── style.css              │
└──────────────┬───────────────┘
               │
               ▼
           Live Website
```
---
## Features
- Automated deployments — every push to main can trigger a deployment.
- GitHub Actions integration — deployment is handled entirely through a CI/CD workflow.
- Amazon S3 hosting — static website files are hosted using S3.
- Secure credential management — AWS credentials are stored using GitHub Secrets rather than committed to the repository.
- Repeatable releases — the same deployment process runs consistently for every change.
- No manual uploads — developers only need to commit and push their changes.
---
## Technologies Used

| Technology         | Purpose                               |
| ------------------ | ------------------------------------- |
| **GitHub Actions** | CI/CD automation                      |
| **Amazon S3**      | Static website hosting                |
| **AWS IAM**        | Access control and permissions        |
| **AWS CLI**        | Uploading/synchronizing website files |
| **YAML**           | GitHub Actions workflow configuration |
| **HTML/CSS**       | Static website content                |

---
## CI/CD Workflow
The deployment process follows these steps:
1. **Developer pushes changes**
A developer updates the website and pushes the changes to the main branch.
```bash
git add .
git commit -m "Update website"
git push origin main
```
2. **GitHub Actions starts**
The push event triggers the GitHub Actions workflow.

3. **Repository is checked out**
The workflow retrieves the latest version of the website source code.

4. **AWS credentials are configured**
The workflow securely retrieves the required AWS credentials from GitHub Secrets.
Credentials should never be hard-coded in the workflow or committed to the repository.

5. **Website is synchronized with S3**
The workflow uses the AWS CLI to synchronize the website files with the S3 bucket.

6. **Website is updated**
Once synchronization completes successfully, the latest website version is available through the configured S3 static website endpoint.
---
## Security
AWS credentials are stored as GitHub Actions Secrets and are not included directly in the repository.

Recommended secrets include:
```
AWS_ACCESS_KEY_ID
AWS_SECRET_ACCESS_KEY
AWS_REGION
```
---
## Deployment Flow
```
Developer
    │
    │ git push
    ▼
GitHub
    │
    │ push to main
    ▼
GitHub Actions
    │
    ├── Checkout
    │
    ├── Configure AWS
    │
    └── Sync files
            │
            ▼
       Amazon S3
            │
            ▼
      Static Website
```
---
## Project Goals
This project demonstrates practical experience with:

- CI/CD pipeline design
- GitHub Actions automation
- AWS S3
- AWS IAM
- AWS CLI
- Infrastructure security practices
- Automated static website deployments
- Secrets management
- Repeatable software delivery
---
## Licence
This project is intended for educational and portfolio purposes.
