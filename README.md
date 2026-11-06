         ___        ______     ____ _                 _  ___  
        / \ \      / / ___|   / ___| | ___  _   _  __| |/ _ \ 
       / _ \ \ /\ / /\___ \  | |   | |/ _ \| | | |/ _` | (_) |
      / ___ \ V  V /  ___) | | |___| | (_) | |_| | (_| |\__, |
     /_/   \_\_/\_/  |____/   \____|_|\___/ \__,_|\__,_|  /_/ 
 ----------------------------------------------------------------- 


# AWS MicroservicesProject

A containerized, multi-tier microservices architecture deployed on AWS using **Amazon ECS (Fargate)**, **AWS CodeCommit**, and **AWS CodeDeploy**. 

This project demonstrates an end-to-end cloud-native microservices pipeline, separating independent application modules into containerized services managed with blue/green deployment strategies.

---

## 🏗️ Architecture Overview

The application is split into two core Node.js microservices:
* **Employee Service**: Manages employee data and internal API logic.
* **Customer Service**: Manages customer profiles, admin endpoints, and public-facing data.

### Key Infrastructure Components
* **Compute**: Amazon ECS running on AWS Fargate (Serverless Containers).
* **Load Balancing**: AWS Application Load Balancer (ALB) with path-based routing.
* **CI/CD Pipeline**: 
  * **AWS CodeCommit** for source control and code triggers.
  * **AWS CodeDeploy** for zero-downtime Blue/Green deployments across ECS task sets.
* **Monitoring**: Amazon CloudWatch log groups for centralized service logging.

---

## 📁 Repository Structure

```text
.
├── customer/                  # Customer Microservice
│   ├── app/                   # Application logic
│   ├── public/                # Static assets & frontend UI
│   ├── views/                 # Templating/HTML views
│   ├── Dockerfile             # Customer service container spec
│   └── package.json
├── employee/                  # Employee Microservice
│   ├── app/                   # Application logic
│   ├── public/                # Static assets & frontend UI
│   ├── views/                 # Templating/HTML views
│   ├── Dockerfile             # Employee service container spec
│   └── package.json
├── deployment/                # Deployment Specifications
│   ├── appspec-customer.yaml  # CodeDeploy AppSpec for Customer service
│   ├── appspec-employee.yaml  # CodeDeploy AppSpec for Employee service
│   ├── taskdef-customer.json  # ECS Task Definition for Customer service
│   └── taskdef-employee.json  # ECS Task Definition for Employee service
├── labuser.pem                # SSH key material
└── README.md
