---
title: "Week 2 Worklog"
date: 2026-06-08
weight: 1
chapter: false
pre: " <b> 1.2. </b> "
---

### Objectives for Week 2:
* Analyze the Microservices architecture and clinical query pipeline of **Smart Healthcare Platform** (on the `chatbot` branch).
* Implement high-speed inter-service communication utilizing **FastAPI Gateway (SSE)** and **gRPC Streaming**.
* Configure long-term conversational memory management using PostgreSQL (NeonDB/RDS) and LangChain.

### Tasks Implemented This Week:
| Day | Task | Start Date | Completion Date | Reference Materials |
| --- | --- | --- | --- | --- |
| **Mon** | - Deep dive into the Smart Healthcare Platform repository structure (focusing on the `chatbot` branch).<br>- Analyze the end-to-end data pipeline: UI -> Gateway -> AI Backend -> RAG & LLM Generation. | 08/06/2026 | 08/06/2026 | [Microservices Architecture](https://aws.amazon.com/microservices/) |
| **Tue** | - Study Server-Sent Events (SSE) protocols for real-time token streaming to clients.<br>- Develop the **FastAPI Gateway** acting as an API reverse proxy managing HTTP requests and `session_id` routing. | 09/06/2026 | 09/06/2026 | [FastAPI SSE](https://fastapi.tiangolo.com/advanced/websockets/) |
| **Wed** | - Architect and implement **gRPC Streaming** channels connecting the FastAPI Gateway to the AI Backend microservice.<br>- Author `.proto` schema definitions for high-speed internal RPC service communication. | 10/06/2026 | 11/06/2026 | [gRPC Python](https://grpc.io/docs/languages/python/) |
| **Thu** | - Provision **PostgreSQL (NeonDB Serverless / Amazon RDS)** for persistent chat history storage.<br>- Integrate LangChain's `PostgresChatMessageHistory` to maintain reliable conversational memory keyed by `session_id`. | 12/06/2026 | 12/06/2026 | [NeonDB Serverless](https://neon.tech/docs/introduction) |
| **Fri** | - **Practice:** Engineer the **Contextualized Query Rewriting** module within the AI Backend.<br>- Leverage LLMs (GPT-4o-mini / Bedrock Claude) combined with PostgreSQL chat history to autonomously rewrite ambiguous follow-up queries into standalone, clinically enriched prompts. | 13/06/2026 | 14/06/2026 | [LangChain Memory](https://python.langchain.com/v0.1/docs/modules/memory/) |

### Key Achievements:
* Successfully engineered the high-performance Microservices communication backbone for Smart Healthcare Platform.
* Mastered gRPC Streaming and SSE protocols, ensuring instantaneous real-time AI token streaming.
* Implemented robust conversational memory persistence and automated contextual query reformulation.
