# 03 — Product ROI Dashboard

## Hệ thống AI hỗ trợ rà soát hợp đồng lao động cho doanh nghiệp vừa và nhỏ tại Việt Nam

**Học viên:** Đinh Văn Thư - 2A202600035
**Ngày:** 11/05/2026
**Version:** v2 (sau red-team)

---

## Part A — Adoption Context

### Thông tin product

| Trường                  | Trả lời                                                                                                                                 |
| ----------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| **Product**             | LaborGuard AI — Hệ thống AI rà soát hợp đồng lao động cho SME Việt Nam                                                                  |
| **Người dùng chính**    | Chủ doanh nghiệp / quản lý HR tại SME (10–200 nhân viên); không có đội pháp chế nội bộ                                                  |
| **Bối cảnh sử dụng**    | Doanh nghiệp soạn thảo hoặc nhận hợp đồng lao động, cần kiểm tra tuân thủ Bộ luật Lao động 2019 và các Nghị định liên quan trước khi ký |
| **Mục tiêu kinh doanh** | Giảm rủi ro tranh chấp lao động; tiết kiệm chi phí thuê tư vấn pháp lý bên ngoài; tăng tốc độ onboarding nhân sự                        |
| **Rào cản ADKAR chính** | **Knowledge** (người dùng không biết luật lao động) + **Ability** (không biết cách sử dụng AI và kiểm tra output)                       |

### Bối cảnh thị trường

- Việt Nam có ~900.000 doanh nghiệp vừa và nhỏ (VCCI 2024), chiếm 97% tổng số doanh nghiệp.
- Phần lớn SME không có luật sư nội bộ; thuê tư vấn pháp lý bên ngoài tốn 500.000–2.000.000 VNĐ/hợp đồng.
- Tranh chấp lao động tăng: Bộ LĐTBXH ghi nhận hơn 3.000 vụ tranh chấp/năm, phần lớn liên quan đến điều khoản hợp đồng không rõ hoặc vi phạm pháp luật lao động.
- Bộ luật Lao động 2019 + Nghị định 145/2020/NĐ-CP có nhiều điều khoản bắt buộc mà SME thường bỏ sót.

---

### 4 Workflow chính

| #   | Workflow                                                                       | AI làm gì?                                                                                                                                         | Con người kiểm tra ở đâu?                                                                   | Khi AI sai thì xử lý thế nào?                                                                   |
| --- | ------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| 1   | **Rà soát hợp đồng đầu vào** (doanh nghiệp nhận hợp đồng từ nhân viên/đối tác) | Phân tích điều khoản, gắn cờ điều khoản thiếu, sai hoặc vi phạm luật; cho điểm rủi ro tổng thể                                                     | HR/chủ doanh nghiệp đọc báo cáo AI; xác nhận hoặc bác từng cảnh báo trước khi lưu           | Người dùng đánh dấu "AI sai" → ghi log → đội sản phẩm review hàng tuần; cập nhật rule base      |
| 2   | **Soạn thảo hợp đồng mẫu** (doanh nghiệp tạo hợp đồng mới)                     | Gợi ý template chuẩn theo loại hợp đồng (toàn thời gian / thời vụ / thử việc); điền trước thông tin cơ bản; cảnh báo điều khoản bắt buộc còn thiếu | Người dùng điền thông tin thực tế; đọc lại toàn bộ trước khi ký; ký xác nhận "đã đọc"       | Nếu điều khoản bị gợi ý sai → báo lỗi trong app → escalate lên tư vấn pháp lý đối tác (SLA 24h) |
| 3   | **Cập nhật khi luật thay đổi** (Nghị định mới / thông tư mới ban hành)         | Tự động so sánh hợp đồng hiện có của doanh nghiệp với quy định mới; liệt kê hợp đồng cần cập nhật                                                  | HR xem danh sách hợp đồng cần sửa; quyết định sửa ngay hay chờ gia hạn                      | Nếu AI bỏ sót thay đổi luật → doanh nghiệp báo cáo → đội pháp lý cập nhật rule base trong 48h   |
| 4   | **Giải thích điều khoản** (người dùng hỏi "điều khoản này có nghĩa gì?")       | Giải thích bằng tiếng Việt đơn giản; liên kết đến điều luật cụ thể; đưa ví dụ thực tế                                                              | Người dùng tự đánh giá mức độ hiểu; nếu vẫn không rõ → escalate chatbot → tư vấn người thật | AI disclaimer rõ: "Đây là giải thích tham khảo, không thay thế tư vấn pháp lý chuyên nghiệp"    |

---

### 3 Tactic tăng adoption

| Tactic                                                                                                                                                                | Nhắm vào rào cản nào?                 | Áp dụng cho workflow nào? | Người phụ trách            |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------- | ------------------------- | -------------------------- |
| **1. Onboarding có hướng dẫn từng bước** — upload hợp đồng đầu tiên miễn phí + video 3 phút "AI đang làm gì" + checklist "bạn cần kiểm tra gì trong báo cáo AI"       | Knowledge + Ability                   | Workflow 1 & 2            | Product + Customer Success |
| **2. Proof của 1 case thật** — sau khi AI phát hiện lỗi đầu tiên cho doanh nghiệp, gửi email "AI vừa giúp bạn tránh rủi ro X" kèm giải thích bằng tiếng Việt đơn giản | Desire (người dùng thấy giá trị thực) | Workflow 1                | Marketing + Product        |
| **3. Cộng đồng HR/SME** — group Zalo/Facebook chia sẻ case luật lao động; AI suggest nội dung dựa trên câu hỏi phổ biến trong group                                   | Awareness + Reinforcement             | Workflow 4                | Community Manager          |

---

## Part B — ROI Dashboard

### B.1 Metric toàn product

| Layer                      |                                                                      Metric |    Baseline |                 Target | Data source        | Owner           | Red-team risk                                              | Fix                                                                       |
| -------------------------- | --------------------------------------------------------------------------: | ----------: | ---------------------: | ------------------ | --------------- | ---------------------------------------------------------- | ------------------------------------------------------------------------- |
| **Activation**             |                   % doanh nghiệp upload ít nhất 1 hợp đồng trong 7 ngày đầu | 0% (launch) |                    60% | App analytics      | Product         | Người dùng đăng ký nhưng không upload vì sợ dữ liệu bị lộ  | Thêm cam kết bảo mật + tùy chọn ẩn tên nhân viên trong bản demo           |
| **Engagement / Retention** |                % doanh nghiệp active dùng ít nhất 2 lần/tháng sau tháng đầu |          0% |                    45% | App analytics      | Product         | Người dùng quét 1 lần rồi bỏ vì không thấy lợi ích rõ      | Push notification khi luật thay đổi + nhắc hợp đồng sắp hết hạn           |
| **Trust / Quality**        |                    % cảnh báo AI được người dùng xác nhận là "đúng/hữu ích" |     Chưa có |                   ≥75% | Feedback trong app | Product + Legal | Người dùng bấm "đúng" bừa để qua nhanh → metric bị inflate | Thêm câu hỏi follow-up ngẫu nhiên: "Bạn đã xử lý vấn đề này chưa?"        |
| **Value**                  | Số tiền tư vấn pháp lý bên ngoài doanh nghiệp tiết kiệm/tháng (self-report) |           0 | 2.000.000 VNĐ/DN/tháng | Survey hàng quý    | Business Dev    | Self-report dễ bị overestimate                             | Tam giác hóa với số lần escalate sang tư vấn thật (giảm = tiết kiệm thật) |

---

### B.2 Metric theo workflow

#### Workflow 1 — Rà soát hợp đồng đầu vào

| Layer            |                                                                            Metric |   Baseline |      Target | Data source                                       | Owner         | Red-team risk                                                              | Fix                                                                        |
| ---------------- | --------------------------------------------------------------------------------: | ---------: | ----------: | ------------------------------------------------- | ------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| **Activation**   |        % hợp đồng được upload và rà soát (trên tổng hợp đồng mới ký/tháng của DN) |         0% |         70% | App + HR survey                                   | Product       | HR quét hợp đồng không quan trọng, bỏ qua hợp đồng phức tạp (ngược ý định) | Phân loại hợp đồng theo mức rủi ro; ưu tiên nhắc scan loại cao rủi ro      |
| **Engagement**   |                       Thời gian trung bình từ upload đến user xác nhận báo cáo AI |    Chưa có |    ≤15 phút | App analytics                                     | Product       | Người dùng không xem báo cáo, bấm "xong" ngay                              | Bắt buộc mở ít nhất 1 cảnh báo trước khi "hoàn tất"                        |
| **Productivity** | Thời gian rà soát 1 hợp đồng so với trước khi dùng AI (baseline: tự đọc ~90 phút) | 90 phút/HĐ | ≤20 phút/HĐ | User survey trước/sau                             | Product       | Người dùng mới mất nhiều thời gian đọc báo cáo AI hơn tự đọc HĐ ngắn       | Đặt ngưỡng: chỉ đo HĐ >5 trang; HĐ ngắn cho xem thẳng                      |
| **Quality**      |    % điều khoản vi phạm/thiếu được phát hiện trên tổng số vấn đề thực tế (recall) |    Chưa có |        ≥85% | Audit bởi luật sư đối tác hàng quý (sample 50 HĐ) | Legal Partner | AI bỏ sót điều khoản ẩn hoặc điều khoản mới theo Nghị định chưa cập nhật   | Cập nhật rule base trong 48h sau khi Nghị định mới ban hành; audit định kỳ |
| **Trust**        |      NPS nội bộ: "Bạn có tin tưởng dùng kết quả AI này cho HĐ thật không?" (0–10) |    Chưa có |       ≥7/10 | In-app survey sau mỗi 5 lần dùng                  | Product       | Người dùng chấm 7 nhưng vẫn không thực sự dùng → metric misleading         | Cross-check với hành vi thật: số HĐ thực sự được ký sau khi dùng AI        |
| **Value**        |                  % doanh nghiệp báo cáo giảm tranh chấp lao động sau 6 tháng dùng |    Chưa có |   ≥30% giảm | Survey 6-month cohort                             | Business Dev  | Tranh chấp lao động có thể tăng/giảm vì nhiều lý do, không chỉ do AI       | Hỏi thêm: "Tranh chấp nào liên quan đến điều khoản hợp đồng?" để isolate   |

---

#### Workflow 2 — Soạn thảo hợp đồng mẫu

| Layer            |                                                                       Metric |                      Baseline |                    Target | Data source                                     | Owner         | Red-team risk                                                                    | Fix                                                                |
| ---------------- | ---------------------------------------------------------------------------: | ----------------------------: | ------------------------: | ----------------------------------------------- | ------------- | -------------------------------------------------------------------------------- | ------------------------------------------------------------------ |
| **Activation**   |            % doanh nghiệp mới dùng template AI ít nhất 1 lần trong tháng đầu |                            0% |                       50% | App analytics                                   | Product       | Doanh nghiệp có sẵn template cũ → không thấy cần dùng                            | So sánh: "Template bạn đang dùng có điều khoản bắt buộc XYZ chưa?" |
| **Engagement**   |                        Số template được tùy chỉnh và lưu lại (không chỉ xem) |                             0 |        ≥3 template/DN/quý | App analytics                                   | Product       | Người dùng dùng template nhưng không lưu → không tái dùng                        | Auto-save + thư mục "template của tôi"                             |
| **Productivity** |                       Thời gian soạn HĐ mới từ đầu (baseline tự soạn ~3 giờ) |                         3 giờ |                  ≤45 phút | User survey                                     | Product       | Người dùng mất nhiều thời gian đọc hiểu template hơn tự soạn                     | Thêm tooltip giải thích mỗi điều khoản ngay trong editor           |
| **Quality**      |        % template được tạo ra đạt ≥90% điều khoản bắt buộc theo luật (audit) |                       Chưa có |                      ≥95% | Legal audit hàng quý                            | Legal Partner | Template đúng luật nhưng thiếu điều khoản đặc thù ngành (may mặc ≠ IT)           | Thêm "loại hình doanh nghiệp/ngành" khi chọn template              |
| **Trust**        | % người dùng ký HĐ thực tế dựa trên template AI tạo ra (không sửa lại nhiều) |                       Chưa có |                      ≥60% | App tracking (so sánh template gốc vs bản cuối) | Product       | Người dùng sửa quá nhiều → template không phù hợp thực tế                        | Phân tích những phần bị sửa nhiều nhất → cải thiện template        |
| **Value**        |                           Chi phí soạn HĐ/tháng so với thuê tư vấn bên ngoài | 1.500.000 VNĐ/HĐ (thuê ngoài) | ≤100.000 VNĐ/HĐ (phí app) | Pricing model                                   | Business Dev  | Người dùng dùng app nhưng vẫn thuê tư vấn kiểm tra lại → không thật sự tiết kiệm | Đo: % doanh nghiệp đã dừng thuê tư vấn ngoài cho HĐ thông thường   |

---

#### Workflow 3 — Cập nhật khi luật thay đổi

| Layer            |                                                                           Metric |        Baseline |                     Target | Data source                             | Owner        | Red-team risk                                                         | Fix                                                                                  |
| ---------------- | -------------------------------------------------------------------------------: | --------------: | -------------------------: | --------------------------------------- | ------------ | --------------------------------------------------------------------- | ------------------------------------------------------------------------------------ |
| **Activation**   |                 % doanh nghiệp mở thông báo "luật thay đổi" khi có Nghị định mới |         Chưa có |                       ≥70% | App analytics                           | Product      | Người dùng ignore notification → HĐ lỗi thời mà không biết            | Dùng email + Zalo OA thay vì chỉ push notification trong app                         |
| **Engagement**   | % doanh nghiệp thực sự review danh sách HĐ cần cập nhật (không chỉ mở thông báo) |         Chưa có |                       ≥50% | App analytics                           | Product      | Người dùng xem xong rồi bỏ → rủi ro tuân thủ vẫn còn                  | Thêm deadline cụ thể + reminder 7 ngày trước hết hạn tuân thủ                        |
| **Productivity** |       Thời gian để doanh nghiệp rà soát toàn bộ HĐ hiện có sau khi luật thay đổi | Trước: vài tuần |                    ≤2 ngày | User survey sau sự kiện luật thay đổi   | Product      | Doanh nghiệp có 50+ HĐ → 2 ngày không đủ                              | Phân nhóm HĐ theo mức ảnh hưởng; xử lý critical trước                                |
| **Quality**      |          % Nghị định/Thông tư mới được tích hợp vào rule base trong 48h ban hành |         Chưa có |                       ≥95% | Internal tracking                       | Legal Team   | Văn bản pháp lý mới đôi khi mơ hồ, cần giải thích → không thể tự động | Có legal partner review & confirm trước khi push rule mới                            |
| **Trust**        |                      % người dùng tin rằng hệ thống "theo kịp luật mới" (survey) |         Chưa có |                       ≥80% | Quarterly survey                        | Product      | Người dùng nghi ngờ AI có cập nhật đúng không → không dùng            | Hiển thị "Cập nhật lần cuối: [ngày]" + link Nghị định gốc                            |
| **Value**        |    Số doanh nghiệp tránh được vi phạm tuân thủ sau thay đổi luật (không bị phạt) |         Chưa có | ≥90% trong cohort dùng app | Khảo sát + so sánh với thống kê BLĐTBXH | Business Dev | Khó isolate: DN không bị phạt có thể vì nhiều lý do                   | Hỏi cụ thể: "Bạn có nhận được quyết định xử phạt vi phạm hành chính lao động không?" |

---

#### Workflow 4 — Giải thích điều khoản

| Layer          |                                                                      Metric |                            Baseline |          Target | Data source              | Owner        | Red-team risk                                                                             | Fix                                                                              |
| -------------- | --------------------------------------------------------------------------: | ----------------------------------: | --------------: | ------------------------ | ------------ | ----------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| **Activation** |                         % người dùng đặt ít nhất 1 câu hỏi giải thích/tháng |                                  0% |             40% | App analytics            | Product      | Người dùng không biết có thể hỏi                                                          | Tutorial khi onboarding: "Nhấn vào điều khoản bất kỳ để hỏi AI"                  |
| **Engagement** |               % câu hỏi dẫn đến hành động (người dùng sửa HĐ hoặc hỏi thêm) |                             Chưa có |            ≥55% | App tracking             | Product      | Người dùng đọc giải thích nhưng không làm gì → giá trị thấp                               | Sau mỗi giải thích: "Điều khoản này có vấn đề không? Muốn AI đề xuất sửa không?" |
| **Quality**    |            % câu trả lời AI được người dùng đánh giá "dễ hiểu và chính xác" |                             Chưa có |            ≥80% | In-app thumbs up/down    | Product      | Người dùng không đủ kiến thức để đánh giá đúng/sai                                        | Audit sample 50 câu/tháng bởi legal partner; so với đánh giá người dùng          |
| **Trust**      | % người dùng dùng giải thích AI làm căn cứ quyết định (không escalate thêm) |                             Chưa có |            ≥65% | Tracking escalation rate | Product      | Người dùng luôn escalate → AI không có giá trị thực; hoặc không escalate khi nên → rủi ro | Phân loại: câu hỏi nào nên escalate (phức tạp) vs tự xử lý (đơn giản)            |
| **Value**      |                    Số lần escalate sang tư vấn pháp lý bên ngoài giảm/tháng | Baseline từ survey: ~5 lần/DN/tháng | ≤2 lần/DN/tháng | Tracking + survey        | Business Dev | Giảm escalate có thể vì người dùng bỏ qua vấn đề thay vì AI giải quyết được               | Cross-check: DN escalate ít hơn có tỉ lệ tranh chấp cao hơn không?               |

---

## Part C — Dashboard Mock

```text
┌─────────────────────────────────────┐  ┌─────────────────────────────────────┐
│ PRODUCT HEALTH                      │  │ WORKFLOW 1 — Rà soát HĐ đầu vào    │
│ Metric: % DN active ≥2 lần/tháng   │  │ Metric: Recall điều khoản vi phạm   │
│ Current: — Target: 45%              │  │ Current: — Target: ≥85%             │
│ Status: ○ (chưa launch)             │  │ Status: ○ (chưa launch)             │
│ Action if red: Push "luật thay đổi" │  │ Action if red: Audit + update rules  │
│   + nhắc HĐ sắp hết hạn            │  │   trong 48h; tăng sample audit       │
└─────────────────────────────────────┘  └─────────────────────────────────────┘

┌─────────────────────────────────────┐  ┌─────────────────────────────────────┐
│ WORKFLOW 2 — Soạn thảo mẫu         │  │ QUALITY / TRUST                     │
│ Metric: % template đạt ≥90%         │  │ Metric: NPS tin tưởng AI (0–10)     │
│   điều khoản bắt buộc (audit)      │  │ Current: — Target: ≥7/10            │
│ Current: — Target: ≥95%            │  │ Status: ○ (chưa launch)             │
│ Status: ○ (chưa launch)            │  │ Action if red: Tăng human review;    │
│ Action if red: Legal partner review │  │   thêm giải thích tại sao AI cảnh   │
│   + cập nhật template theo ngành   │  │   báo; giảm false positive rate      │
└─────────────────────────────────────┘  └─────────────────────────────────────┘

┌─────────────────────────────────────┐  ┌─────────────────────────────────────┐
│ VALUE                               │  │ DECISION                            │
│ Metric: Tiết kiệm chi phí tư vấn   │  │ Khuyến nghị: CONTINUE với điều      │
│   pháp lý bên ngoài (VNĐ/DN/tháng)│  │   kiện pilot 3 tháng đầu            │
│ Current: — Target: 2.000.000 VNĐ   │  │ Metric mạnh nhất: Recall WF1 ≥85%  │
│ Status: ○ (chưa launch)            │  │ Trước khi scale: (1) Đạt recall 85% │
│ Action if red: Tăng coverage điều  │  │   (2) NPS ≥7 (3) 50 DN pilot OK    │
│   khoản; giảm false negative rate  │  │ Pivot nếu: Recall <70% sau 3 tháng  │
└─────────────────────────────────────┘  └─────────────────────────────────────┘
```

**Màu sắc trạng thái:**

- 🟢 **Green:** Đạt target
- 🟡 **Amber:** 70–99% target — theo dõi chặt
- 🔴 **Red:** <70% target — hành động ngay
- ⚪ **Grey:** Chưa có data (pre-launch)

---

## Part D — Decision Memo

```markdown
# Decision Memo — LaborGuard AI (v2, sau red-team)

## 1. Khuyến nghị: CONTINUE — với điều kiện pilot 3 tháng

Tiếp tục với 50 doanh nghiệp SME pilot tại TP.HCM và Hà Nội.
Đánh giá lại sau 3 tháng với bộ metric B.1 và B.2 (WF1 ưu tiên).

## 2. Metric mạnh nhất để bảo vệ quyết định

**Recall của Workflow 1: % điều khoản vi phạm/thiếu được phát hiện ≥85%**

Đây là metric trung tâm vì:

- Nếu AI bỏ sót lỗi → DN ký HĐ có vấn đề → tranh chấp lao động → mất niềm tin → churn.
- Dễ đo khách quan (legal partner audit, không phụ thuộc self-report).
- Nếu recall <70% sau 3 tháng: pivot sang mô hình "AI chỉ hỗ trợ tư vấn người thật" thay vì rà soát tự động.

## 3. Metric/giả định đã sửa sau red-team

**V1:** Đo tỉ lệ "NPS người dùng" như metric chất lượng chính.
**V2:** Thay bằng "Recall được đo bởi legal partner audit (sample 50 HĐ/quý)".
**Vì sao sửa:** Người dùng SME không đủ kiến thức pháp lý để đánh giá đúng/sai → NPS bị inflate;
recall đo bởi bên thứ ba trung lập hơn và không bị bias.

**V1:** Đo "số tiền tiết kiệm" bằng self-report.
**V2:** Tam giác hóa: self-report + số lần escalate sang tư vấn thật + tỉ lệ tranh chấp.
**Vì sao sửa:** Self-report dễ bị overestimate; đo bằng 3 nguồn tăng độ tin cậy.

## 4. Trước khi scale, nhóm phải

1. Đạt recall ≥85% trên tập test 200 hợp đồng thực tế (audit bởi legal partner).
2. NPS tin tưởng AI ≥7/10 từ ≥30 doanh nghiệp pilot sau 60 ngày dùng.
3. Có failure path hoàn chỉnh: khi AI sai → người dùng báo → log → legal team fix trong 48h.
4. Hoàn thành DPIA (Đánh giá tác động xử lý dữ liệu) theo Luật BVDLCN 91/2025/QH15
   vì xử lý dữ liệu nhân sự là dữ liệu cá nhân nhạy cảm.
5. Tự phân loại tầng rủi ro AI theo Luật AI VN 134/2025/QH15 Điều 9
   (khả năng cao tầng Trung bình — chatbot giải thích pháp lý có thể gây nhầm lẫn)
   và thông báo Bộ KH&CN nếu thuộc tầng Trung bình hoặc Cao.
```

---

## Part E — Red-team và sửa v2

### Câu hỏi red-team mà bản thân tự đặt ra

| Vai           | Câu hỏi / Rủi ro                                                                                                                                                                           |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| CFO           | "ROI 2.000.000 VNĐ/tháng tiết kiệm — tính từ đâu? Doanh nghiệp có thật sự bỏ tiền thuê tư vấn ngoài cho TỪNG hợp đồng không?"                                                              |
| Người dùng HR | "Tôi không có nền tảng pháp lý — làm sao tôi biết AI đang gắn cờ đúng hay sai? Nếu tôi tin AI sai thì ai chịu trách nhiệm?"                                                                |
| Risk/Legal    | "Luật AI VN mới có hiệu lực 1/3/2026 — sản phẩm này có bị xếp tầng rủi ro Cao không (vì tư vấn pháp lý = tác động đến quyền lợi con người)? Nếu Cao thì phải đăng ký và giám sát thế nào?" |

### Thay đổi từ v1 sang v2

| #   | V1 có vấn đề gì?                                        | V2 sửa thành gì?                                                                    | Vì sao sửa tốt hơn?                                                                    |
| --- | ------------------------------------------------------- | ----------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| 1   | Metric chất lượng chính là NPS người dùng tự đánh giá   | Recall được đo bởi legal partner audit (sample 50 HĐ/quý)                           | Người dùng SME không đủ kiến thức để đánh giá chính xác → cần bên thứ ba có chuyên môn |
| 2   | "Value" metric chỉ dùng self-report tiết kiệm chi phí   | Tam giác hóa: self-report + số lần escalate giảm + tỉ lệ tranh chấp                 | Một nguồn dữ liệu dễ bị inflate; 3 nguồn cho kết quả tin cậy hơn                       |
| 3   | Không có điều khoản tuân thủ pháp lý cho chính sản phẩm | Thêm vào Decision Memo: DPIA theo PDPL + phân loại tầng AI theo Luật AI VN 134/2025 | Sản phẩm xử lý dữ liệu nhân sự → nghĩa vụ pháp lý cụ thể; bỏ qua = rủi ro founder      |

---

## Checklist trước khi nộp

- [x] Có 1 product cụ thể: LaborGuard AI — AI rà soát hợp đồng lao động cho SME Việt Nam.
- [x] Có 4 workflow chính.
- [x] Mỗi workflow có vai trò AI, human review và failure path.
- [x] Có rào cản ADKAR chính: Knowledge + Ability.
- [x] Dashboard có metric toàn product và metric theo từng workflow.
- [x] Không chỉ đo usage: có Productivity, Quality, Trust, Value ở mỗi workflow.
- [x] Có baseline, target, data source và owner cho các metric chính.
- [x] Có ít nhất 1 metric Quality, Trust và Value mỗi workflow.
- [x] Có Red-team risk và Fix cho mỗi metric.
- [x] Có ít nhất 2 thay đổi rõ từ v1 sang v2.
- [x] Decision Memo có khuyến nghị Continue với điều kiện cụ thể.
