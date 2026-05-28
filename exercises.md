# Ngày 1 — Bài Tập & Phản Ánh
## Nền Tảng LLM API | Phiếu Thực Hành

**Thời lượng:** 1:30 giờ  
**Cấu trúc:** Lập trình cốt lõi (60 phút) → Bài tập mở rộng (30 phút)

---

## Phần 1 — Lập Trình Cốt Lõi (0:00–1:00)

Chạy các ví dụ trong Google Colab tại: https://colab.research.google.com/drive/172zCiXpLr1FEXMRCAbmZoqTrKiSkUERm?usp=sharing

Triển khai tất cả TODO trong `template.py`. Chạy `pytest tests/` để kiểm tra tiến độ.

**Điểm kiểm tra:** Sau khi hoàn thành 4 nhiệm vụ, chạy:
```bash
python template.py
```
Bạn sẽ thấy output so sánh phản hồi của GPT-4o và GPT-4o-mini.

---

## Phần 2 — Bài Tập Mở Rộng (1:00–1:30)

### Bài tập 2.1 — Độ Nhạy Của Temperature
Gọi `call_openai` với các giá trị temperature 0.0, 0.5, 1.0 và 1.5 sử dụng prompt **"Hãy kể cho tôi một sự thật thú vị về Việt Nam."**

**Bạn nhận thấy quy luật gì qua bốn phản hồi?** (2–3 câu)
> Khi temperature tăng, câu trả lời trở nên sáng tạo hơn, đa dạng và ít lặp lại câu trả lời. Tuy nhiên, độ ổn định và tính chính xác có thể giảm, đặc biệt ở mức rất cao như 1.5.

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Mình thấy sẽ đặt khoảng 0.2–0.5. Mức này giúp chatbot trả lời ổn định, rõ ràng và chính xác, đồng thời vẫn đủ tự nhiên để tạo cảm giác thân thiện với người dùng.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> 10.500.000 token/ngày
**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> GPT-4oo: GPT-4o phù hợp khi cần chất lượng suy luận và độ chính xác cao, ví dụ: trợ lý AI phân tích tài liệu pháp lý, hỗ trợ y tế, AI coding assistant, hoặc chatbot doanh nghiệp cần trả lời phức tạp và ít sai sót. Trong các trường hợp này, chất lượng phản hồi tốt hơn giúp giảm lỗi và tăng trải nghiệm người dùng, nên chi phí cao hơn là hợp lý.
GPT-4o-mini phù hợp cho: 
chatbot CSKH cơ bản,
FAQ tự động,
phân loại ticket,
tóm tắt ngắn,
hoặc ứng dụng có lượng request rất lớn.
Các tác vụ này không yêu cầu suy luận quá sâu, nên dùng mini sẽ tiết kiệm chi phí đáng kể mà vẫn đáp ứng tốt nhu cầu thực tế.
---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> Streaming quan trọng nhất trong các ứng dụng cần phản hồi theo thời gian thực để người dùng cảm thấy hệ thống nhanh và tự nhiên hơn, ví dụ chatbot trò chuyện, AI coding assistant, trợ lý giọng nói hoặc công cụ viết nội dung. Việc hiển thị từng phần câu trả lời ngay khi model sinh ra giúp giảm cảm giác chờ đợi và cải thiện trải nghiệm người dùng đáng kể. Ngược lại, non-streaming phù hợp hơn khi hệ thống cần nhận toàn bộ kết quả trước khi xử lý hoặc hiển thị, chẳng hạn như tạo báo cáo hoàn chỉnh, phân tích dữ liệu, trả về JSON chuẩn cho backend hoặc các workflow cần kiểm tra tính đầy đủ và hợp lệ của output trước khi gửi cho người dùng.


## Danh Sách Kiểm Tra Nộp Bài
- [ ] Tất cả tests pass: `pytest tests/ -v`
- [ ] `call_openai` đã triển khai và kiểm thử
- [ ] `call_openai_mini` đã triển khai và kiểm thử
- [ ] `compare_models` đã triển khai và kiểm thử
- [ ] `streaming_chatbot` đã triển khai và kiểm thử
- [ ] `retry_with_backoff` đã triển khai và kiểm thử
- [ ] `batch_compare` đã triển khai và kiểm thử
- [ ] `format_comparison_table` đã triển khai và kiểm thử
- [ ] `exercises.md` đã điền đầy đủ
- [ ] Sao chép bài làm vào folder `solution` và đặt tên theo quy định 
