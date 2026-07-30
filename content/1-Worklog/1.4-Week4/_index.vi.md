---
title: "Worklog Tuần 4"
date: 2026-06-22
weight: 1
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu Tuần 4:
* Huấn luyện mô hình ViMQ để nhận dạng văn bản y tế.
* Tìm cách làm cho mô hình học tốt hơn dù dữ liệu y khoa bị thiếu hụt hoặc nhiễu.
* Đánh giá độ chính xác của AI và đưa mô hình vào chạy thực tế.

### Các công việc triển khai trong tuần:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| **2** | Cấu hình các thông số cơ bản (Optimizer, hàm Loss) để bắt đầu quá trình huấn luyện AI. | 22/06/2026 | 22/06/2026 | [ViMQ Repository](https://github.com/tadeephuy/ViMQ) |
| **3** | Xây dựng quy trình tự động huấn luyện lặp lại nhiều lần để AI học được nhiều từ vựng mới hơn. | 23/06/2026 | 23/06/2026 | [ViMQ Repository](https://github.com/tadeephuy/ViMQ) |
| **4** | Áp dụng các thuật toán tạo nhiễu ngẫu nhiên giúp mô hình trở nên mạnh mẽ và ít bị dự đoán sai hơn. | 24/06/2026 | 25/06/2026 | [ViMQ Repository](https://github.com/tadeephuy/ViMQ) |
| **5** | Viết các tập lệnh để chấm điểm và kiểm tra xem mô hình AI đoán đúng được bao nhiêu phần trăm. | 26/06/2026 | 26/06/2026 | [ViMQ Repository](https://github.com/tadeephuy/ViMQ) |
| **6** | Đóng gói mô hình AI vừa huấn luyện vào hệ thống chatbot để phân tích câu hỏi bệnh nhân theo thời gian thực. | 27/06/2026 | 28/06/2026 | [ViMQ Repository](https://github.com/tadeephuy/ViMQ) |

### Kết quả đạt được:
* Huấn luyện và tối ưu hóa thành công mô hình NER tiếng Việt chuyên khoa y tế ViMQ với chiến lược Self-training tiên tiến.
* Đạt chỉ số F1-Score ấn tượng (88.4%), vượt trội so với các phương pháp trích xuất thực thể truyền thống.
* Tích hợp thành công ViMQ vào lõi AI Backend của Smart Healthcare Platform, hoàn thiện bước chuẩn bị ngữ cảnh chuyên sâu cho RAG Pipeline.
