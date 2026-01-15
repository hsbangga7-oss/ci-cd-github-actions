# CI/CD Pipeline Automation using GitHub Actions and AWS S3

## Project Overview
This project demonstrates a complete **CI/CD pipeline** that automatically deploys a static website to **Amazon S3** using **GitHub Actions**.  
Any change pushed to the `main` branch triggers an automated deployment, removing the need for manual uploads and ensuring consistent releases.

---

## Technologies Used
- GitHub Actions
- Amazon S3 (Static Website Hosting)
- AWS IAM
- YAML
- HTML/CSS

---

## CI/CD Workflow
1. Developer pushes code to the GitHub repository
2. GitHub Actions workflow triggers automatically
3. AWS credentials are securely accessed via GitHub Secrets
4. Static files are synced to the S3 bucket
5. Website updates are deployed instantly

