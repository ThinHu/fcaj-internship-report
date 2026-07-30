---
title: "Worklog Tuần 6"
date: 2026-07-06
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---

### Mục tiêu Tuần 6:
* Xây dựng luồng điều phối (Orchestration) tổng hợp tri thức với **LangChain Framework** và mô hình LLM.
* Tích hợp mô hình Ngôn ngữ Lớn (GPT-4o-mini / Bedrock Claude 3.5 Sonnet) sinh câu trả lời tư vấn streaming real-time.
* Cấu hình hệ thống Giám sát & Quản trị mô hình (**LLM Observability**) toàn diện với **Langfuse** và **AWS CloudWatch**.

### Các công việc triển khai trong tuần:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| **2** | - Lập trình luồng điều phối (Orchestration) trong AI Backend sử dụng **LangChain Framework**.<br>- Xây dựng QA Prompt chuyên sâu tổng hợp 4 nguồn thông tin: Câu hỏi tái cấu trúc + Lịch sử chat + ViMQ Intent/Entities + Top Tài liệu đã Rerank. | 06/07/2026 | 06/07/2026 | [RunnableBranch](https://python.langchain.com/v0.1/docs/expression_language/primitives/routing/) |
| **3** | - Tích hợp mô hình LLM (**GPT-4o-mini / Amazon Bedrock Claude 3.5 Sonnet**) vào luồng LangChain.<br>- Cấu hình cơ chế truyền phát trực tiếp (Streaming): Token sinh ra từ LLM đẩy qua gRPC -> FastAPI Gateway (SSE) về Client. | 07/07/2026 | 07/07/2026 | [Medical Prompt Safety](https://www.anthropic.com/news/prompt-engineering-for-medical-ai) |
| **4** | - Nghiên cứu và triển khai nền tảng **Langfuse (LLM Observability)** cho hệ thống Smart Healthcare Platform.<br>- Cấu hình Langfuse Tracing để ghi nhận toàn bộ vết thực thi của LangChain: thời gian xử lý từng bước (latency), số lượng token input/output và chi phí (cost). | 08/07/2026 | 08/07/2026 | [Red-Flag Warnings](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7326087/) |
| **5** | - Tích hợp hệ thống giám sát hạ tầng với **AWS CloudWatch Logs và Metrics**.<br>- Đồng bộ hóa log từ FastAPI Gateway, AI Backend Microservice và cơ sở dữ liệu NeonDB/RDS lên CloudWatch. | 09/07/2026 | 10/07/2026 | [Medical Disclaimer](https://en.wikipedia.org/wiki/Medical_disclaimer) |
| **6** | - **Thực hành:** Kiểm thử khả năng quan sát (Observability Audit) và xử lý ngoại lệ (Error Handling).<br>- Giả lập các tình huống nghẽn mạng, lỗi gọi API LLM/Reranker và kiểm tra cơ chế fallback/retry trong LangChain. | 10/07/2026 | 12/07/2026 | [GPT-4o-mini API](https://platform.openai.com/docs/models/gpt-4o-mini) |

### Kết quả đạt được:
* Hoàn thiện hoàn toàn luồng xử lý AI Backend Microservice từ NLP (ViMQ) -> RAG (Amazon S3 Vector / Cohere) -> LLM Generation (LangChain).
* Đem lại trải nghiệm người dùng xuất sắc với cơ chế streaming token độ trễ cực thấp qua gRPC/SSE.
* Đạt tiêu chuẩn quản trị AI chuyên nghiệp với hệ thống Observability (Langfuse + AWS CloudWatch), kiểm soát chặt chẽ hiệu năng và chi phí.
