---
title: "Worklog Tuần 2"
date: 2026-06-08
weight: 1
chapter: false
pre: " <b> 1.2. </b> "
---

### Mục tiêu Tuần 2:
* Phân tích kiến trúc Microservices và Pipeline xử lý câu hỏi y tế của dự án **Smart Healthcare Platform** (trên branch `chatbot`).
* Nghiên cứu cơ chế giao tiếp tốc độ cao giữa các dịch vụ bằng **FastAPI Gateway (SSE)** và **gRPC Stream**.
* Thiết lập hệ thống quản lý bộ nhớ hội thoại dài hạn với PostgreSQL (NeonDB/RDS) và LangChain.

### Các công việc triển khai trong tuần:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| **2** | - Khám phá và phân tích sâu cấu trúc Repository của Smart Healthcare Platform (branch `chatbot`).<br>- Nghiên cứu luồng dữ liệu (Data Pipeline): từ Giao diện UI -> Gateway -> AI Backend -> RAG & LLM Generation. | 08/06/2026 | 08/06/2026 | [Microservices Architecture](https://aws.amazon.com/microservices/) |
| **3** | - Nghiên cứu giao thức Server-Sent Events (SSE) để truyền phát (streaming) câu trả lời real-time về Client.<br>- Lập trình **FastAPI Gateway** đóng vai trò Proxy tiếp nhận request HTTP và quản lý `session_id`. | 09/06/2026 | 09/06/2026 | [FastAPI SSE](https://fastapi.tiangolo.com/advanced/websockets/) |
| **4** | - Nghiên cứu và cấu hình giao thức **gRPC Streaming** kết nối giữa FastAPI Gateway và phân hệ AI Backend.<br>- Viết file định nghĩa `.proto` cho các service giao tiếp nội bộ tốc độ cao. | 10/06/2026 | 11/06/2026 | [gRPC Python](https://grpc.io/docs/languages/python/) |
| **5** | - Thiết lập cơ sở dữ liệu **PostgreSQL (NeonDB Serverless / Amazon RDS)** lưu trữ lịch sử trò chuyện.<br>- Tích hợp `PostgresChatMessageHistory` của LangChain để duy trì bộ nhớ hội thoại theo `session_id`. | 12/06/2026 | 12/06/2026 | [NeonDB Serverless](https://neon.tech/docs/introduction) |
| **6** | - **Thực hành:** Viết module **Contextualized Query Rewriting** trong AI Backend.<br>- Sử dụng LLM (GPT-4o-mini / Bedrock Claude) kết hợp lịch sử chat từ PostgreSQL để tự động tái cấu trúc câu hỏi gốc thành một câu hỏi độc lập mang đầy đủ ngữ cảnh y khoa. | 13/06/2026 | 14/06/2026 | [LangChain Memory](https://python.langchain.com/v0.1/docs/modules/memory/) |

### Kết quả đạt được:
* Định hình thành công nền tảng kiến trúc Microservices hiệu năng cao cho Smart Healthcare Platform.
* Làm chủ công nghệ giao tiếp gRPC Streaming và SSE, đảm bảo trải nghiệm AI phản hồi tức thì (real-time streaming).
* Xây dựng hoàn chỉnh luồng quản lý bộ nhớ hội thoại thông minh và tái cấu trúc câu hỏi tự động (Contextualized Query).
