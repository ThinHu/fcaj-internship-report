---
title: "Worklog Tuần 3"
date: 2026-06-15
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---

### Mục tiêu Tuần 3:
* Tìm hiểu và nghiên cứu về bài toán trích xuất thực thể y tế tiếng Việt.
* Xử lý dữ liệu văn bản y tế đầu vào.
* Tìm hiểu các kiến trúc học sâu cơ bản và xây dựng mô hình AI nhận diện thực thể y tế (ViMQ).

### Các công việc triển khai trong tuần:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| **2** | Phân tích đặc thù văn bản y tế và làm quen với bộ dữ liệu y khoa tiếng Việt. | 15/06/2026 | 15/06/2026 | [ViMQ Repository](https://github.com/tadeephuy/ViMQ) |
| **3** | Viết mã tiền xử lý dữ liệu để chuyển đổi văn bản thành các con số cho AI hiểu (Tokenization & Encoding). | 16/06/2026 | 16/06/2026 | [ViMQ Repository](https://github.com/tadeephuy/ViMQ) |
| **4** | Chuẩn bị và biến đổi dữ liệu nhãn thành định dạng chuẩn để huấn luyện mô hình. | 17/06/2026 | 17/06/2026 | [ViMQ Repository](https://github.com/tadeephuy/ViMQ) |
| **5** | Lên ý tưởng và bắt đầu lắp ghép các thành phần mạng nơ-ron cơ bản cho mô hình ViMQ. | 18/06/2026 | 19/06/2026 | [ViMQ Repository](https://github.com/tadeephuy/ViMQ) |
| **6** | Hoàn thiện cấu trúc mô hình để dự đoán được loại bệnh, triệu chứng từ câu văn. | 20/06/2026 | 21/06/2026 | [ViMQ Repository](https://github.com/tadeephuy/ViMQ) |

### Kết quả đạt được:
* Hoàn thành xây dựng pipeline tiền xử lý dữ liệu NER span-based chuyên sâu cho ngôn ngữ tiếng Việt.
* Lập trình thành công kiến trúc mô hình ViMQ hiện đại, kết hợp sức mạnh của PhoBERT, BiLSTM và Biaffine Classifier.
* Đặt nền móng vững chắc cho khâu phân tích câu hỏi chuyên môn y tế (Query Analyzer) trong hệ sinh thái Smart Healthcare Platform.
