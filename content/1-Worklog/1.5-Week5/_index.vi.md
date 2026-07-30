---
title: "Worklog Tuần 5"
date: 2026-06-29
weight: 1
chapter: false
pre: " <b> 1.5. </b> "
---

### Mục tiêu Tuần 5:
* Xây dựng luồng Advanced RAG Pipeline kết hợp cơ sở dữ liệu vector **Amazon S3 Vector**.
* Tích hợp kỹ thuật tái cấu trúc câu hỏi hội thoại (**Contextualized Query Rewriting**) từ lịch sử PostgreSQL.
* Triển khai mô hình **Cohere Reranker** đóng vai trò màng lọc thứ cấp, chấm điểm lại và tinh lọc tài liệu y khoa.

### Các công việc triển khai trong tuần:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| **2** | - Chuẩn hóa và cắt đoạn (chunking) tập dữ liệu phác đồ điều trị, dược điển y khoa.<br>- Chuyển đổi tài liệu thành vector embeddings (OpenAI Embeddings / Bedrock Titan Embeddings) và tải lên cơ sở dữ liệu vector **Amazon S3 Vector**. | 29/06/2026 | 29/06/2026 | [AWS S3 SDK](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/s3.html) |
| **3** | - Lập trình luồng **Contextualized Query Rewriting** trong LangChain:<br>- Kết hợp `session_id` để lấy lịch sử trò chuyện từ PostgreSQL (NeonDB/RDS), dùng LLM cấu trúc lại câu hỏi nối tiếp thành câu hỏi độc lập ngữ cảnh. | 30/06/2026 | 30/06/2026 | [AWS Bedrock KB](https://docs.aws.amazon.com/bedrock/latest/userguide/knowledge-base.html) |
| **4** | - Lập trình luồng tìm kiếm ban đầu (Initial Retrieval): Sử dụng câu hỏi đã tái cấu trúc và từ khóa thực thể (Entities) từ mô hình ViMQ gửi vào Amazon S3 Vector để lấy Top K (K=20) tài liệu thô liên quan nhất. | 01/07/2026 | 01/07/2026 | [Bedrock API](https://docs.aws.amazon.com/bedrock/latest/APIReference/API_agent_StartIngestionJob.html) |
| **5** | - Nghiên cứu và triển khai kỹ thuật **Advanced Reranking** với **Cohere Reranker**:<br>- Đẩy 20 tài liệu thô từ Amazon S3 Vector qua Cohere Rerank API để chấm điểm lại sự tương quan ngữ nghĩa chuyên sâu với câu hỏi và thực thể y tế. | 02/07/2026 | 03/07/2026 | [BedrockRetriever](https://python.langchain.com/v0.2/docs/integrations/retrievers/bedrock/) |
| **6** | - **Thực hành:** Kiểm thử so sánh hiệu năng giữa RAG truyền thống (chỉ dùng Vector Search) và Advanced RAG (Vector Search trên S3 + Cohere Reranker + ViMQ Entities).<br>- Đánh giá trên tập 50 câu hỏi tư vấn thuốc và phác đồ điều trị phức tạp. | 03/07/2026 | 05/07/2026 | [Cohere Rerank v3.0](https://docs.cohere.com/docs/rerank-2) |

### Kết quả đạt được:
* Xây dựng thành công luồng Advanced RAG hiện đại sử dụng Amazon S3 Vector, giải quyết triệt để điểm yếu của RAG truyền thống trong y tế.
* Sự kết hợp giữa thực thể ViMQ NER, Context Rewriting và Cohere Reranker tạo ra nguồn tri thức đầu vào cực kỳ sạch và chính xác cho LLM.
* Đảm bảo hệ thống trợ lý y tế Smart Healthcare Platform luôn dẫn nguồn phác đồ điều trị chính xác, chuẩn khoa học với chi phí lưu trữ S3 cực kỳ tiết kiệm.
