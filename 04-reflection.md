# 04 — Reflection cá nhân

**Học viên:** Đinh Văn Thư - 2A202600035
**Ngày:** 11/05/2026
**Buổi học:** Day 23 — Change Management & AI Adoption

---

## 1 metric hoặc 1 giả định tôi sẽ sửa

Trong quá trình xây dựng dashboard, giả định ban đầu của tôi là **NPS người dùng** (mức độ họ tự đánh giá tin tưởng AI) đủ để đo chất lượng sản phẩm. Đây là lỗi tư duy mà tôi nhận ra sau khi đặt mình vào vai người phản biện.

Người dùng SME mục tiêu — chủ doanh nghiệp hoặc HR không có nền tảng pháp lý — về bản chất **không có khả năng đánh giá đúng/sai** một cảnh báo về điều khoản hợp đồng lao động. Nếu AI tự tin sai, người dùng vẫn bấm "đúng" vì họ không biết khác. Đây chính xác là pattern đã xảy ra trong các vụ hallucination pháp lý: người dùng tin AI vì đầu ra nghe có vẻ hợp lý, không phải vì họ thật sự kiểm chứng được.

Metric tôi sẽ thay là **recall được đo bởi legal partner audit độc lập** — cụ thể là một công ty luật đối tác mỗi quý lấy ngẫu nhiên 50 hợp đồng đã rà soát, đánh giá lại thủ công và so sánh với kết quả AI. Chỉ số này đo được điều quan trọng nhất: AI có thật sự bắt được các lỗi pháp lý nghiêm trọng không, độc lập với cảm nhận của người dùng.

Bài học rộng hơn: trong AI cho domain chuyên sâu (pháp lý, y tế, tài chính), **người dùng cuối thường không đủ năng lực để là judge cho chất lượng AI**. Dashboard đo adoption phải phân biệt rõ giữa "người dùng cảm thấy hài lòng" và "AI thật sự đúng". Hai cái này có thể ngược chiều nhau — và cái nguy hiểm nhất là khi AI sai nhưng người dùng vẫn hài lòng.

_(~185 từ)_
