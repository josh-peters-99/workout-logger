---
runme:
  document:
    relativePath: ARCHITECTURE.md
  session:
    id: 01JGYDE6BG4JXVP7AFZYAG011B
    updated: 2025-01-06 16:26:17-07:00
---

# Project Architecture

## File Structure

```sh
workout-logger/
├── frontend/                      # Frontend (Next.js TypeScript)
│   ├── src/                       # Source code
│   ├── public/                    # Static assets
│   ├── package.json               # Dependencies for the frontend
│   ├── tsconfig.json              # TypeScript configuration
│   ├── .eslintrc.js               # Linting configuration
│   ├── .next/                     # Next.js build outputs (ignored in Git)
│   ├── .gitignore                 # Git ignore file
│   └── README.md                  # Frontend-specific documentation
├── backend/                       # Backend (Spring Boot)
│   ├── src/                       # Source code for Spring Boot
│   │   ├── main/
│   │   │   ├── java/
│   │   │   └── resources/
│   │   └── test/
│   ├── pom.xml                    # Maven/Gradle dependencies
│   ├── .gitignore                 # Git ignore file
│   └── README.md                  # Backend-specific documentation
├── serverless/                    # Serverless functions (AWS Lambda in Python)
│   ├── functions/                 # Individual Lambda functions
│   ├── requirements.txt           # Python dependencies
│   ├── .gitignore                 # Git ignore file
│   └── README.md                  # Serverless-specific documentation
├── infrastructure/                # Infrastructure as code (Python with Boto3)
│   ├── scripts/                   # Scripts for resource provisioning
│   ├── requirements.txt           # Python dependencies
│   ├── .gitignore                 # Git ignore file
│   └── README.md                  # Infrastructure-specific documentation
├── database/                      # Database-related files
│   ├── migrations/                # SQL or migration scripts
│   ├── schema.sql                 # Initial database schema
│   └── README.md                  # Database-specific documentation
├── .github/                       # GitHub-specific configurations
│   ├── workflows/                 # GitHub Actions workflows for CI/CD
├── docs/                          # Project documentation
│   ├── architecture.md            # Architecture overview
│   ├── requirements.md            # Requirements document
│   └── README.md                  # General documentation
├── .gitignore                     # Root Git ignore file
├── LICENSE                        # License file
├── README.md                      # Main project README
└── CONTRIBUTING.md                # Contribution guidelines

```