---
title: "Worklog Tuần 7"
date: 2026-07-13
weight: 1
chapter: false
pre: " <b> 1.7. </b> "
---

### Mục tiêu Tuần 7:
* Tích hợp sâu và đánh giá giao diện ứng dụng lâm sàng từ **Repo Smart Healthcare Platform** (Web App chính thức) với hệ thống AI Microservices qua luồng SSE/gRPC.
* Thực hiện kiểm thử chịu tải (Load Testing) cho các Endpoints và kiểm thử độ chính xác truy hồi của Advanced RAG trên lâm sàng.
* Tối ưu hóa chi phí vận hành Cloud (FinOps) và đóng gói bộ tài liệu hướng dẫn thực hành (**Workshop**).

### Các công việc triển khai trong tuần:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| **2** | - Tích hợp giao diện người dùng chính thức từ **Repo Smart Healthcare Platform** (Web Application hiện đại) với hệ thống AI Backend Microservice qua **FastAPI Gateway**.<br>- Cấu hình luồng Server-Sent Events (SSE) để kết nối hiển thị kết quả chẩn đoán và tư vấn AI. | 13/07/2026 | 13/07/2026 | [HL7/FHIR Basics](https://www.hl7.org/fhir/overview.html) |
| **3** | - **Đánh giá Giao diện & Trải nghiệm (UI/UX Evaluation trên Repo Smart Healthcare Platform):**<br>&emsp; + Đánh giá độ nhạy và tốc độ hiển thị token streaming real-time trên Dashboard bác sĩ.<br>&emsp; + Kiểm tra trải nghiệm người dùng khi xem các nguồn trích dẫn y khoa RAG (Citations) và các chỉ định thuốc đề xuất. | 14/07/2026 | 14/07/2026 | [Bi-directional Streaming](https://grpc.io/docs/what-is-grpc/core-concepts/#bidirectional-streaming-rpc) |
| **4** | - Thực hiện kiểm thử chịu tải (**Load Testing**) bằng Locust/Artillery cho luồng gRPC và SSE Gateway.<br>- Kiểm thử độ chính xác lâm sàng (Clinical RAG Benchmark) trên 50 ca bệnh án thử nghiệm. | 15/07/2026 | 15/07/2026 | [Protobuf V3](https://protobuf.dev/programming-guides/proto3/) |
| **5** | - Tối ưu hóa chi phí vận hành Cloud (**FinOps**):<br>&emsp; + Rà soát chi phí gọi API (OpenAI Embeddings, Cohere Reranker, Langfuse) và tài nguyên AWS.<br>&emsp; + Tối ưu hóa kích thước vector index trên **Amazon S3 Vector** và áp dụng cache cho các câu hỏi trùng lặp. | 16/07/2026 | 17/07/2026 | [async psycopg3](https://www.psycopg.org/psycopg3/docs/advanced/async.html) |
| **6** | - **Thực hành:** Đóng gói bộ tài liệu hướng dẫn thực hành (**Workshop** - Step-by-Step Guide).<br>- Viết chi tiết các Module hướng dẫn cộng đồng tự tái tạo giải pháp: Setup ViMQ NER, cấu hình gRPC Microservices, Amazon S3 Vector & Cohere Reranker, tích hợp giao diện Smart Healthcare Platform. | 17/07/2026 | 19/07/2026 | [FastAPI AsyncIO](https://fastapi.tiangolo.com/async/) |

### Kết quả đạt được:
* Hợp nhất thành công toàn bộ phân hệ UI (Smart Healthcare Platform Repo) và phân hệ AI Backend Microservice (ViMQ + Advanced RAG với Amazon S3 Vector).
* Đảm bảo hệ thống đạt chuẩn mực cao về hiệu năng chịu tải, độ chính xác y tế và chi phí tối ưu (FinOps).
* Đóng gói hoàn chỉnh bộ tài liệu Workshop thực hành sẵn sàng cho kỳ đánh giá cuối khóa của chương trình FCAJ.
