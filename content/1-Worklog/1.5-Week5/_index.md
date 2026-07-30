---
title: "Week 5 Worklog"
date: 2026-06-29
weight: 1
chapter: false
pre: " <b> 1.5. </b> "
---

### Objectives for Week 5:
* Architect an Advanced RAG Pipeline leveraging **Amazon S3 Vector** as the primary vector database.
* Implement conversational query reformulation (**Contextualized Query Rewriting**) backed by PostgreSQL history.
* Deploy **Cohere Reranker** as an intelligent secondary filter to re-score and refine retrieved clinical documents.

### Tasks Implemented This Week:
| Day | Task | Start Date | Completion Date | Reference Materials |
| --- | --- | --- | --- | --- |
| **Mon** | - Standardize and execute semantic chunking across clinical treatment protocols and medical pharmacopeias.<br>- Generate high-dimensional embeddings (OpenAI Embeddings / Bedrock Titan Embeddings) and ingest them into **Amazon S3 Vector**. | 29/06/2026 | 29/06/2026 | [AWS S3 SDK](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/s3.html) |
| **Tue** | - Engineer **Contextualized Query Rewriting** workflows within LangChain:<br>- Retrieve multi-turn dialogue history from PostgreSQL (NeonDB/RDS) via `session_id` and prompt LLMs to reformulate follow-up queries into standalone contextual prompts. | 30/06/2026 | 30/06/2026 | [AWS Bedrock KB](https://docs.aws.amazon.com/bedrock/latest/userguide/knowledge-base.html) |
| **Wed** | - Implement Initial Retrieval pipelines: Query Amazon S3 Vector using the contextualized query and clinical entity keywords extracted by ViMQ to retrieve Top K (K=20) candidate documents. | 01/07/2026 | 01/07/2026 | [Bedrock API](https://docs.aws.amazon.com/bedrock/latest/APIReference/API_agent_StartIngestionJob.html) |
| **Thu** | - Architect and integrate **Advanced Reranking** utilizing **Cohere Reranker**:<br>- Pass the 20 candidate documents from Amazon S3 Vector through Cohere's Rerank API to re-score semantic relevance against the contextual query and clinical entities. | 02/07/2026 | 03/07/2026 | [BedrockRetriever](https://python.langchain.com/v0.2/docs/integrations/retrievers/bedrock/) |
| **Fri** | - **Practice:** Conduct comparative benchmark evaluations between baseline RAG (Vector Search only) and Advanced RAG (S3 Vector Search + Cohere Reranker + ViMQ Entities).<br>- Test against 50 complex clinical case and pharmacology consultations. | 03/07/2026 | 05/07/2026 | [Cohere Rerank v3.0](https://docs.cohere.com/docs/rerank-2) |

### Key Achievements:
* Successfully built a state-of-the-art Advanced RAG pipeline using Amazon S3 Vector, overcoming traditional vector retrieval limitations in healthcare.
* Seamlessly unified ViMQ entity extraction, Context Rewriting, and Cohere Reranking to deliver pristine clinical context to LLMs.
* Ensured the Smart Healthcare Platform clinical assistant consistently cites verifiable, evidence-based medical treatment protocols with minimal S3 storage costs.
