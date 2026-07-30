---
title: "Blog 3: AWS S3 Bucket for Digital Healthcare System"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---

# [FCAJ2026] AWS S3 Bucket: The Cloud-Native Storage "Missing Piece" for Digital Healthcare Systems

### Introduction
During the development of our Digital Healthcare System (an AI-assisted medical consultation and appointment management platform), after solving the problems of anti-overlap appointment booking, integrating AI models, and building the user authentication flow, I faced another major headache: **File Data Management and Storage (File Storage)**.

Our system continuously generates a wide variety of file data:
* **Patients:** Avatars, medical summary reports/prescriptions in PDF format.
* **Doctors & Staff:** Professional degrees, medical practice certificates.
* **AI Models:** Training weight files (.pt, .bin) up to hundreds of MBs in size, along with consultation chat logs.

Initially, my most convenient habit when working locally was to dump certificate and avatar files directly into the `uploads/` folder of the NestJS Backend server, and commit the AI weight files straight into Git. However, as we prepared to push the system to Production, I realized this was a "disaster" in terms of security and scalability: the Git repo became too heavy, the Backend server was burdened with file storage (Stateful), and the risk of leaking personal medical files was extremely high.

That was when I shifted to exploring and applying **Amazon S3 (Simple Storage Service)**.

### Practical Application in the Project
Instead of turning the Backend server into a storage "dump," I restructured the entire system to push all file-based resources to an S3 Bucket. Specifically, the strategic application areas included:

* **Securing Doctor Practice Certificates:** Medical degrees are sensitive personal data that absolutely cannot be made public. I created a Private S3 Bucket to hold these files. When an Admin needs to review a doctor's profile, the NestJS Backend generates an S3 Presigned URL with a short expiration time. Once expired, the URL is automatically invalidated, ensuring absolute security.
* **AI Model Weights Management:** Weight files (`model.pt`) were completely separated from the source code. All weights and training checkpoints are stored on S3. When the AI service container starts up, a Python script automatically pulls the latest weights from S3 into memory to load the model. Version management for the AI model became extremely lightweight.
* **Exporting Medical Reports & Storing Chat Logs:** Whenever a patient completes a consultation or examination session, the system automatically exports a PDF report and records the chat log from the AI Service. These files are pushed directly to an S3 Bucket for downloading or long-term storage.

### Outstanding Values When Switching to Amazon S3
After successfully integrating S3 Buckets into the system, here are the biggest values the project gained:

* **Freeing the Backend to a "Stateless" state:** The NestJS Backend server now purely handles business logic and APIs. Removing all static files makes the server much lighter and easy to scale-out to multiple instances without worrying about out-of-sync stored files.
* **Absolute Security for Sensitive Medical Data:** There is no longer a risk of exposing direct file paths. Access control through IAM Roles and Presigned URLs ensures that only the right people at the right time can access medical documents.
* **Ultimate Reliability & Optimized Costs:** S3 guarantees data durability of up to 99.999999999% (11 nines). Besides, AWS provides 5GB of free storage for the first 12 months. Combined with Lifecycle Rules (automatically deleting temporary logs or moving old files to the low-cost Glacier storage), the cost of maintaining the storage infrastructure for the project is practically zero.

### Conclusion
Applying Cloud-Native services like Amazon S3 to manage files is the core mindset that helps standardize modern system architecture. Instead of turning the Backend server into a bulky "warehouse" and facing a series of security risks, shift the burden of storage and resource management to AWS S3.

This not only makes your project more professional and flexible but also allows you to focus entirely on developing core business features.

### References
* AWS. "Amazon Simple Storage Service (S3) User Guide". ([Link](https://docs.aws.amazon.com/AmazonS3/latest/userguide/))
* AWS. "Amazon S3 Product Overview". ([Link](https://aws.amazon.com/s3/))