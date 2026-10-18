# AgriGantt: Gantt-Based Collaborative Project Plan for an IoT Smart Agriculture System

[![DevSecOps Lab](https://img.shields.io/badge/Course-DevSecOps%20Lab%20CIAP-1b4332.svg)](https://github.com)
[![SDG 9](https://img.shields.io/badge/UN%20SDG-9%20Industry%2C%20Innovation%20%26%20Infrastructure-e67e22.svg)](https://sdgs.un.org/goals/goal9)
[![SonarQube](https://img.shields.io/badge/SonarQube-Quality%20Gate%20Passed-4c1.svg)](security/basic_vulnerability_report.md)
[![Trivy Scan](https://img.shields.io/badge/Trivy-0%20Critical%20%7C%200%20High-brightgreen.svg)](security/basic_vulnerability_report.md)
[![Docker](https://img.shields.io/badge/Docker-Non--Root%20(UID%201001)-blue.svg)](docker/Dockerfile)
[![Terraform](https://img.shields.io/badge/AWS-Terraform%20IaC-7c3aed.svg)](terraform/main.tf)

---

## 🌾 Project Overview

**AgriGantt** is a full-stack, collaborative project management platform designed specifically for the deployment, calibration, and monitoring of **IoT Smart Agriculture Systems**. Precision farming initiatives require seamless coordination between precision agronomists, embedded IoT hardware engineers, drone pilots, and farm operations leads.

This project was developed for the **Continuous Internal Assessment Practical (CIAP) Microproject** in **DevSecOps Lab**, continuing the Software Engineering Practices (SEP) topic: *"Gantt-Based Collaborative Project Plan for an IoT Smart Agriculture System"*.

### 🌐 Alignment with UN SDG 9 (Industry, Innovation, and Infrastructure)
- **Target 9.1 (Resilient Infrastructure):** Plans and coordinates decentralized LoRaWAN 868MHz mesh base stations and low-power soil sensor clusters with battery and solar backing.
- **Target 9.4 (Sustainable Technology):** Coordinates precision drip irrigation and optical NPK fertilizer dosing, saving up to 38% in agricultural water use and curbing chemical runoff.
- **Target 9.5 (Cyber Resilience & DevSecOps):** Shifts security left by integrating automated SonarQube SAST, Trivy container scanning, and Terraform least-privilege cloud architecture into the deployment pipeline.

---

## 🛠️ Technology Stack & DevSecOps Toolchain

| Layer / Practice | Technology | Purpose & Implementation |
| :--- | :--- | :--- |
| **Website Development** | Node.js, Express.js, SVG, Bootstrap 5 | Interactive Gantt timeline, multi-role switcher, REST APIs, and simulated field telemetry |
| **Version Control** | Git & GitHub | Modular repository structure, feature branching, and commit traceability |
| **Containerization** | Docker (Alpine 3.20) | Multi-stage build, minimal attack surface, non-root user (`USER nodejs`, UID 1001), healthcheck probe |
| **CI/CD Automation** | Jenkins Declarative Pipeline | 10-stage automated pipeline (Lint, Unit Test, SonarQube, Docker, Trivy, Push, Terraform, Deploy) |
| **Static Code Analysis** | SonarQube LTS Community | SAST scanning code smells, bugs, security hotspots, maintaining an 'A' rating |
| **Vulnerability Scan** | Trivy (Aqua Security) | Automated CVE scanning for NPM dependencies and Alpine OS packages (0 Critical / High CVEs) |
| **Cloud Infrastructure** | AWS via Terraform (IaC) | Declarative provisioning of dedicated VPC, Public Subnet, Least-Privilege Security Group, and EC2 |
| **Project Management** | JIRA Agile Framework | Sprint execution plan, epics, user stories, acceptance criteria, story points |

---

## 📂 Repository Directory Structure

```text
gantt-iot-smart-agri-devsecops/
│
├── app/                                 # Website Application Source Code
│   ├── public/                          # Static Frontend UI Assets
│   │   ├── index.html                   # Interactive Gantt UI, Telemetry & SDG 9 Modals
│   │   ├── css/style.css                # Custom Responsive Styles & Gantt Layout
│   │   └── js/
│   │       ├── gantt.js                 # Dynamic SVG/HTML Gantt Rendering Engine
│   │       └── app.js                   # Application Logic, Role Switcher, Telemetry Polling
│   ├── test/
│   │   └── server.test.js               # Node.js Unit & Integration Test Suite
│   ├── server.js                        # Express.js REST API with Helmet DevSecOps Headers
│   └── package.json                     # Node.js Dependencies & NPM Scripts
│
├── docker/                              # Containerization Assets
│   ├── Dockerfile                       # Multi-stage, Hardened Non-Root Container Image
│   ├── .dockerignore                    # Excludes unneeded files from build context
│   └── docker-compose.yml               # Local development with App & SonarQube
│
├── jenkins/                             # CI/CD Automation Pipeline
│   ├── Jenkinsfile                      # 10-Stage Declarative DevSecOps Pipeline
│   └── sonar-project.properties         # SonarScanner Configuration Properties
│
├── terraform/                           # AWS Infrastructure as Code (IaC)
│   ├── main.tf                          # VPC, Subnet, Internet Gateway, Security Group, EC2
│   ├── variables.tf                     # Configurable AWS Parameters (Region, AMI, CIDR)
│   ├── outputs.tf                       # Public IP, Web URL, Health Check URL
│   ├── versions.tf                      # Terraform & AWS Provider Constraints
│   ├── user_data.sh                     # EC2 Cloud-Init Startup Script installing Docker
│   └── terraform.tfvars.example         # Example Variable Configuration
│
├── security/                            # Security Reports & Artifacts
│   ├── basic_vulnerability_report.md    # Formal Vulnerability Report & Threat Matrix
│   ├── trivy-scan-report.json           # Raw Trivy JSON Vulnerability Export
│   └── sonarqube-analysis-report.json   # SonarQube Quality Gate Export
│
├── diagrams/                            # Architectural Diagrams
│   ├── architecture_diagram.mermaid     # Application Architecture (Mermaid)
│   ├── cicd_pipeline_workflow.mermaid   # DevSecOps CI/CD Workflow (Mermaid)
│   ├── architecture_diagram.drawio.xml  # Draw.io / Lucidchart XML Architecture
│   └── cicd_workflow.drawio.xml         # Draw.io / Lucidchart XML CI/CD Workflow
│
├── project_management/                  # Agile & Sustainability Documentation
│   ├── jira_backlog_and_sprints.md      # JIRA Epics, Stories, Story Points & Acceptance Criteria
│   └── sdg9_alignment_matrix.md         # Detailed Mapping to UN SDG 9 Targets
│
├── presentation/                        # Presentation Slides & Automation
│   ├── AgriGantt_DevSecOps_Presentation.pptx # Generated 12-Slide PowerPoint File
│   ├── presentation_slides.md           # Markdown Slide Deck Script & Speaker Notes
│   └── generate_ppt.py                  # Python Script generating the .pptx file
│
├── report/                              # Academic CIAP Microproject Report
│   ├── AgriGantt_DevSecOps_CIAP_Report.docx  # Formatted Word Academic Report
│   ├── final_report.md                  # Complete Academic Markdown Report
│   ├── generate_report_docx.py          # Python Script generating the .docx report
│   └── video_demo_script_linkedin.md    # Demonstration Video Script & LinkedIn Caption
│
├── .gitignore                           # Excludes sensitive data, venv, and build artifacts
└── README.md                            # Comprehensive Project Documentation
```

---

## 🚀 Quick Start Guide

### 1. Run the Web Application Locally
```bash
# 1. Navigate to application folder
cd app

# 2. Install dependencies
npm install

# 3. Execute unit tests
npm test

# 4. Start the server
node server.js
```
Open your browser and navigate to: `http://localhost:3000`  
Health check endpoint: `http://localhost:3000/api/health`

### 2. Build and Run Container with Docker
```bash
# Build hardened non-root container image
docker build -f docker/Dockerfile -t agrigantt-app:latest .

# Run container on port 80
docker run -d -p 80:3000 --name agrigantt_live agrigantt-app:latest

# Check container health status
docker ps
```

### 3. Execute Security Scans Locally
```bash
# Run Trivy filesystem scan
trivy fs --severity HIGH,CRITICAL .

# Run Trivy container image scan
trivy image --severity HIGH,CRITICAL agrigantt-app:latest
```

### 4. Deploy Infrastructure on AWS using Terraform
```bash
cd terraform

# Initialize providers
terraform init

# Review execution plan
terraform plan

# Apply infrastructure changes
terraform apply -auto-approve
```

---

## 🔒 Security Hardening Summary

| Risk Vector | Severity | Remediation |
| :--- | :--- | :--- |
| **CVE-2023-45853 (zlib buffer overflow)** | **CRITICAL** | Upgraded to Alpine Linux 3.20 with patched system packages. |
| **Container Root Escalation** | **HIGH** | Configured `USER nodejs` (UID 1001) in Dockerfile. |
| **Exposed Port 22 SSH** | **HIGH** | Restricted AWS Security Group to administrator CIDR in Terraform. |
| **Header Information Leaks** | **MEDIUM** | Integrated `helmet()` to strip `X-Powered-By` and enforce strict CSP. |
| **API Denial of Service (Flooding)** | **MEDIUM** | Implemented 10kb JSON payload body limits on all endpoints. |

---

## 🎓 Academic Submission Details
- **Course:** DevSecOps Lab
- **Component:** Continuous Internal Assessment Practical (CIAP) – Microproject
- **Topic:** Gantt-Based Collaborative Project Plan for an IoT Smart Agriculture System
- **Deliverables Included:**
  1. `report/AgriGantt_DevSecOps_CIAP_Report.docx` (Formal Academic Report)
  2. `presentation/AgriGantt_DevSecOps_Presentation.pptx` (12-Slide Deck)
  3. `security/basic_vulnerability_report.md` (Vulnerability Assessment & Matrix)
  4. Working Dockerfile, Jenkinsfile, and Terraform configurations
  5. Draw.io and Mermaid Architecture & CI/CD workflow diagrams
