---
title: "Blog 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# WHAT IS AWS COGNITO? WHY IS IT AN INDISPENSABLE PIECE FOR DIGITAL HEALTHCARE SYSTEMS?

During the development of the Smart Healthcare Platform (an AI-powered medical triage and appointment booking system), managing identity and multi-role access control (Authentication & Authorization) posed a significant challenge. The system serves 3 completely distinct user groups: Patients, Doctors, and Receptionists. Instead of manually building a complex authentication service, integrating AWS Cognito was chosen as the optimal solution.

Key points to know:

* AWS Cognito is a Fully Managed Identity & Access Management service that supports both User Pools (user directory management) and Identity Pools (granting access to AWS resources).
* Completely solves the multi-role access control problem (RBAC - Role-Based Access Control) using the `cognito:groups` attribute embedded directly inside JWT Tokens.
* Supports a secure onboarding workflow for healthcare staff: Admins create accounts via API, Cognito automatically sends an email with a temporary password, and forces a password change upon the first login.
* The Backend Service (NestJS) seamlessly verifies tokens using Cognito's Public Key without storing any user passwords in the database.
* Integrates a UUID encryption strategy to anonymize original user identities, meeting strict compliance standards for sensitive healthcare data.
* Optimizes development and operational costs thanks to a generous AWS Free Tier allowance of up to 50,000 MAUs (Monthly Active Users) per month.

This post helps you understand why offloading the security and auth infrastructure burden to cloud-native services like AWS Cognito allows you to dedicate 100% of your resources to optimizing core business logic.

See details [Here](<https://www.facebook.com/groups/awsstudygroupfcj/permalink/2228021697962790/?rdid=MLFJXbxXfs8sMMKH#>)