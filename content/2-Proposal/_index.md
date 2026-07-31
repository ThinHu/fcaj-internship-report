---
title: "Proposal"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

In this section, here is the summary of the proposed project for the development of the Digital Healthcare system, including objectives, AWS Cloud architecture, business workflows, and operational budget estimation.

# Smart Healthcare AI Triage & Appointment Booking Platform  
## Cloud-native Solution for Medical AI Triage and Online Appointment Management  

### 1. Introduction 
The Smart Healthcare Platform is designed to modernize the reception, initial triage, and appointment scheduling processes at clinics and hospitals. The system applies artificial intelligence (AI) models deployed on **Amazon Bedrock** with the **ViMQ** local augmentation model to consult patients. The platform is built following a Microservices/Cloud-native architecture on the **AWS Cloud** platform (Cognito, EC2, RDS PostgreSQL, S3, CloudWatch), serving thousands of concurrent requests from patients, doctors, and receptionists.  

### 2. Problem Statement  
*Current Issues*  
Medical facilities currently often face overcrowding at the reception desk. Traditional appointment scheduling through phone calls or over the counter easily leads to double-booking and extended wait times for patients. Furthermore, doctors spend a lot of time re-asking basic symptoms from patients due to the lack of pre-prepared information (Pre-consultation summary).  

*Solution*  
The platform provides a comprehensive solution including:  
1. **Real-time AI Chatbot:** Communicates with patients via WebSocket, collects and analyzes symptoms, and provides answers and suggestions to patients.
2. **Anti-double-booking Appointment System:** Utilizes **Pessimistic Locking** mechanism on **AWS RDS PostgreSQL** to completely resolve the Race Condition problem when multiple users book the same time slot.
3. **Security and Role-Based Access Control (RBAC):** Manages identities via **AWS Cognito**.

*Benefits and Return on Investment (ROI)*  
- Increases doctors' productivity by 30% thanks to available symptom summary reports compiled by AI.
- Eliminates 100% of double-booking risks, enhancing patient experience and satisfaction.
- Optimizes infrastructure costs through AWS Cloud's flexible scalability based on real traffic.  

### 3. Solution Architecture  
The system uses a Multi-tier Web architecture on the AWS Cloud platform, divided into 3 main layers: Frontend (Next.js), Backend Service (NestJS on EC2), and AI Services (Amazon Bedrock).  

<!--
![IoT Weather Station Architecture](/images/2-Proposal/edge_architecture.jpeg)

![IoT Weather Platform Architecture](/images/2-Proposal/platform_architecture.jpeg)
-->

*AWS Services Utilized*  
- *Amazon Cognito*: Identity management, login/registration, and user authorization (Patient, Doctor, Receptionist, Admin).
- *AWS EC2*: Deploys Web Frontend (Next.js) and Backend REST API / WebSocket (NestJS) applications via Docker Containers.
- *Amazon Bedrock*: Platform for provisioning and running AI models for medical symptom analysis.
- *Amazon RDS (PostgreSQL)*: Relational database storing information on patients, doctors, working schedules, and invoices.
- *Amazon S3*: Stores static files, avatars, prescriptions, and paraclinical results.
- *AWS CloudWatch*: Collects system logs, monitors CPU/Memory performance, and sends incident alerts.
- *AWS SES / SNS*: Automatically sends Email/SMS for appointment confirmation with check-in QR codes.  

*Component Design*  
- *Patient Interface (Next.js)*: Allows chatting with the Bot, viewing doctor lists, selecting time slots, and online payments.
- *Doctor Interface (Next.js)*: Allows setting available schedules and managing appointments.
- *Backend Microservices (NestJS)*: Handles Business Logic, WebSocket Gateway, connects to RDS PostgreSQL database.  

### 4. Technical Implementation  
*Deployment Phases*  
The project is implemented within **8 weeks** (2 months) through the following phases:  
1. *Weeks 1 - 2*: Requirements analysis, AWS Cloud architecture design, Database design, and Base Source Code initialization (Next.js + NestJS).
2. *Weeks 3 - 4*: Deploy AWS infrastructure (EC2, S3, RDS PostgreSQL), integrate ORM Prisma/TypeORM, and handle anti-double-booking mechanisms.
3. *Weeks 5 - 6*: Integrate AWS CloudWatch, integrate AI models on Amazon Bedrock, RBAC Dashboard.
4. *Weeks 7 - 8*: Stress Testing, E2E testing, Database Indexing optimization, Swagger API documentation packaging, and final Demo.

*Technical Requirements*  
- *Frontend*: Next.js 14, TailwindCSS, Socket.io-client, React Query.
- *Backend*: NestJS Framework, TypeORM/Prisma, TypeScript, Socket.io.
- *Database*: PostgreSQL 16.x on AWS RDS (Private Subnet).
- *AI/ML*: Python, Amazon Bedrock.
- *DevOps*: AWS EC2, AWS ECS, GitHub Actions (CI/CD).

### 5. Roadmap & Milestones  
- *Phase 1 (Weeks 1 - 2)*: Complete System Architecture & Database Schema design.
- *Phase 2 (Weeks 3 - 4)*: Successfully deploy AWS infrastructure (RDS PostgreSQL, S3, EC2) & Core APIs.
- *Phase 3 (Weeks 5 - 6)*: Successfully integrate AI chatbot.
- *Phase 4 (Weeks 7 - 8)*: Complete Stress Test, optimize UX/UI, and project acceptance.

### 6. Budget Estimation  
Infrastructure costs are estimated on the AWS Cloud environment for the MVP / Development Phase: 

*Monthly AWS Infrastructure Costs*  
- *AWS RDS (db.t3.micro - PostgreSQL)*: ~$15.00 USD/month (Single-AZ, 20 GB Storage).
- *AWS EC2 (t3.small - Backend & Frontend)*: ~$14.00 USD/month (Running 24/7).
- *Amazon S3 Standard*: ~$0.50 USD/month (5 GB Data Storage & Transfer).
- *Amazon Cognito*: $0.00 USD/month (Free for the first 50,000 MAUs).
- *AWS CloudWatch*: ~$2.00 USD/month (Metrics, Logs & Alarms).

*Total Cloud Infrastructure Cost*: ~$67.50 USD/month.

### 7. Risk Assessment  
*Risk Matrix*  
- Double-booking due to concurrent actions (Race Condition): High impact, medium probability.
- AI model connection disruption (Bedrock Timeout): Medium impact, low probability.
- Patient medical information leakage (Data Privacy): Very high impact, low probability. 

*Mitigation Strategy*  
- *Race Condition*: Use Pessimistic Locking directly from the PostgreSQL Database tier.  
- *AI Timeout*: Build a Fallback flow — If AI fails, the system automatically switches to the traditional manual doctor selection flow without disrupting user experience.  
- *Data Privacy*: Use UUID strings instead of auto-incrementing IDs in URLs, anonymize patient information when saving logs to CloudWatch.  

### 8. Expected Outcomes  
- **Technical Improvements:** Automate 80% of patient reception and triage processes; achieve system availability > 99.9% on the AWS Cloud platform.  
- **Long-term Value:** Provide a standardized data source for disease analysis and forecasting; the system is easily scalable for a chain of multiple clinic branches in the future.
