---
title: "Proposal"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

In this section, here is the summary of the proposed project for the development of the Digital Healthcare system, including objectives, AWS Cloud architecture, core business workflows, and operational budget estimation.

# Smart Healthcare AI Triage & Appointment Booking Platform  
## Cloud-native Solution for Medical AI Triage and Online Appointment Management  

### 1. Executive Summary  
The Smart Healthcare Platform is designed to modernize the reception process, initial medical inquiries, and online appointment scheduling. The system applies a **Generative AI & RAG (Retrieval-Augmented Generation)** architecture combining **AWS Bedrock Knowledge Base**, the medical entity extraction model **ViMQ**, and the **GPT-4o-mini** LLM, while supporting the storage of **Pre-consultation Reports**. The platform is built following a Cloud-native architecture on the **AWS Cloud** infrastructure (Cognito, EC2, RDS PostgreSQL, S3, CloudWatch), integrated with a dedicated LLM monitoring system (**Langfuse**), serving the access needs of Patients, Doctors, and Administrators.  

### 2. Problem Statement  
#### Current Issues  
Medical facilities currently often face overcrowding at the reception desk because patients spend a lot of time asking basic medical questions. Traditional appointment scheduling through phone calls or over the counter easily leads to double-booking and extended wait times. For doctors, keeping track of their appointment lists and patient medical records manually is inefficient and lacks centralization.  

#### Solution  
The platform provides a comprehensive solution covering closed-loop business phases:
1. **Phase 1 - System Setup & Authorization (Auth Flow):** Admins manage and initialize accounts on the system. **AWS Cognito** provides centralized identity management (RBAC), supporting clear authorization for Patient, Doctor, and Admin roles.
2. **Phase 2 - Reception & Medical Declaration (Onboarding):** Patients register/log in on the Mobile Web App. Patients can update their personal information form, medical history, and basic health information.
3. **Phase 3 - AI RAG Medical Consulting Assistant (LLM Pipeline Flow):** 
   - The [LLM Intent Router] receives questions and routes the processing: extracts medical entities via **ViMQ (Local Host)** and routes intents via **AWS Bedrock Knowledge Base**.
   - The **GPT-4o-mini** model synthesizes knowledge and responds with accurate answers to the patient.
   - The entire conversation flow is logged and monitored for performance/tokens via **Langfuse** and **AWS CloudWatch**.
4. **Phase 4 - Specialist Appointment Booking (Booking Flow):** Patients proactively choose doctors and available time slots. **AWS RDS PostgreSQL** applies a **Pessimistic Locking** mechanism to eliminate 100% of double-booking risks (Race Condition). The consultation chat can be automatically summarized into a **Pre-consultation Report** file and saved to **Amazon S3**.
5. **Phase 5 - Appointment Lookup & Management (Doctor/Patient Portal):** Doctors log into the Portal to view the list of booked appointments and look up patients' personal information/medical history.

#### Benefits and Return on Investment (ROI)  
- Reduces initial consultation time at the reception counter by 60% thanks to the AI RAG Assistant answering questions automatically 24/7 with accurate medical data.
- Helps doctors easily grasp their work schedules and the list of patients for the day.
- Eliminates 100% of double-booking risks thanks to the Pessimistic Locking mechanism at the Database tier.
- Ensures the quality and safety of AI responses thanks to the centralized LLM monitoring system (**Langfuse**).
- Optimizes infrastructure operational costs thanks to the flexible scalability of AWS Cloud services.  

### 3. Solution Architecture  
The system uses a Multi-tier Web architecture combined with Hybrid AI services (Cloud Services + External SaaS + Local Host Services).  

![Smart Healthcare AI Architecture](/images/2-Proposal/architecture-diagram.png)

<!--
![IoT Weather Station Architecture](/images/2-Proposal/edge_architecture.jpeg)

![IoT Weather Platform Architecture](/images/2-Proposal/platform_architecture.jpeg)
-->

#### AWS Services & Technologies Utilized  
- *Amazon Cognito*: Identity management, login/registration, RBAC authorization for Patients, Doctors, and Admins.
- *AWS EC2*: Deploys Web Frontend (Next.js) and Backend REST API / WebSocket Gateway / LLM Intent Router (NestJS) applications packaged via Docker Containers.
- *AWS Bedrock Knowledge Base*: Stores and retrieves the medical knowledge base (RAG Pipeline) for consultation.
- *External SaaS & Local Models*: **GPT-4o-mini** (response generation), **ViMQ Local Host** (medical NER extraction), and **Langfuse** (monitoring LLM metrics, latency, and tokens).
- *Amazon RDS (PostgreSQL)*: Relational database storing patient, doctor, and appointment information with Pessimistic Locking mechanism (`FOR UPDATE`).
- *Amazon S3*: Stores static assets, consultation chat history report files (PDF/JSON), and attachments.
- *AWS CloudWatch*: Collects Backend and EC2 system logs, and aggregated logs from Langfuse.  

#### Component Design  
- *Patient Interface (Next.js - Mobile View)*: Allows updating personal information, chatting with the AI RAG Assistant to answer medical queries, and booking medical appointments.
- *Doctor Interface (Next.js - Desktop View)*: Allows Doctors to log in, look up the list of booked consultations/appointments, and view patients' personal information/medical history/AI consultation reports from S3.
- *Admin Portal*: Manages the directory of doctors, user accounts, and views operational statistical reports.
- *Backend Services (NestJS)*: Handles Business Logic, LLM Intent Router, connects to RDS PostgreSQL, S3, and AI APIs (Bedrock, GPT-4o-mini, ViMQ, Langfuse).  

### 4. Technical Implementation  
**Deployment Phases**  
The project is implemented within **8 weeks** (2 months) through the following phases:  
1. *Weeks 1 - 2*: Analyze Business Flow requirements, design Hybrid AI AWS Cloud architecture, design Database ERD, and initialize Base Source Code (Next.js + NestJS).
2. *Weeks 3 - 4*: Configure AWS Cognito (RBAC Auth Flow), deploy AWS infrastructure (EC2, S3, RDS PostgreSQL), integrate Prisma ORM, and handle the anti-double-booking mechanism (Pessimistic Locking).
3. *Weeks 5 - 6*: Integrate RAG Pipeline (AWS Bedrock KB + GPT-4o-mini + ViMQ Local), connect Langfuse for LLM monitoring, complete the lookup interface for Doctors & booking interface for Patients.
4. *Weeks 7 - 8*: Integrate AWS CloudWatch, perform Stress Testing (Concurrency Booking), package Docker containers, configure CI/CD, and project acceptance handover.

**Technical Requirements**  
- *Frontend*: Next.js, TailwindCSS, Socket.io-client, React Query.
- *Backend*: NestJS Framework, Prisma ORM, TypeScript, Socket.io.
- *Database*: PostgreSQL 16.x on AWS RDS (`db.t4g.micro` - Private Subnet).
- *AI/ML*: AWS Bedrock KB, OpenAI API (GPT-4o-mini), ViMQ Local Service, Langfuse.
- *DevOps*: Docker, AWS CLI, GitHub Actions (CI/CD).

### 5. Roadmap & Milestones  
- *Phase 1 (Weeks 1 - 2)*: Complete System Architecture & Database Schema design according to the new Business Flow.
- *Phase 2 (Weeks 3 - 4)*: Successfully deploy AWS infrastructure (Cognito Auth Flow, RDS PostgreSQL, S3, EC2) & Booking Concurrency API.
- *Phase 3 (Weeks 5 - 6)*: Successfully integrate RAG Pipeline (Bedrock + GPT-4o-mini + ViMQ), Langfuse monitoring, and complete the schedule lookup Portal for Doctors.
- *Phase 4 (Weeks 7 - 8)*: Complete concurrent booking Stress Test, deploy CI/CD on AWS Cloud, and project acceptance.

### 6. Budget Estimation  
Infrastructure costs are estimated on the AWS Cloud & AI Services environment for the MVP / Development Phase: 

*Monthly Infrastructure & Services Costs*  
- *AWS RDS (db.t4g.micro - PostgreSQL)*: ~$12.00 USD/month (Single-AZ, ARM Graviton2).
- *AWS EC2 (t3.small - Backend & Frontend)*: ~$14.00 USD/month (Running Docker 24/7).
- *AWS Bedrock Knowledge Base*: ~$10.00 USD/month (Vector storage & Search Queries cost).
- *OpenAI API (GPT-4o-mini)*: ~$5.00 USD/month (Token cost based on actual usage).
- *Amazon S3 Standard*: ~$0.50 USD/month (5 GB Data Storage & Transfer).
- *Amazon Cognito*: $0.00 USD/month (Free for the first 50,000 MAUs).
- *AWS CloudWatch & Langfuse*: ~$3.00 USD/month (Metrics, Logs, Alarms & LLM Monitoring).

*Total Cloud & AI Infrastructure Cost*: ~$44.50 USD/month.

### 7. Risk Assessment  
#### Risk Matrix  
- Double-booking due to concurrent actions (Race Condition): High impact, medium probability.
- LLM API connection disconnection (OpenAI / Bedrock Timeout): Medium impact, low probability.
- AI provides inaccurate medical knowledge responses (Hallucination): High impact, low probability. 

#### Mitigation Strategy  
- *Race Condition*: Use Pessimistic Locking (`FOR UPDATE`) directly from the PostgreSQL Database tier when securing a schedule slot.  
- *API Timeout & Fallback*: Build a Fallback flow — If the LLM API encounters an issue, the system automatically redirects patients to the direct appointment booking interface.  
- *Reduce Hallucination & Monitoring*: Use RAG via **AWS Bedrock Knowledge Base** to scope accurate medical data, combined with **Langfuse** to monitor quality and alert on abnormal AI responses. 

### 8. Expected Outcomes  
- **Technical Improvements:** Automate initial medical inquiries for patients using accurate AI RAG; achieve system availability > 99.9% on the AWS Cloud platform.  
- **Practical Value:** Provide a transparent and accurate appointment scheduling solution, helping patients proactively manage their time and making it easy for doctors to manage their consultation lists.
