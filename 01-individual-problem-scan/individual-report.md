# 01 — Individual Problem Scan

## Scan rộng

| # | Lăng kính | Problem quan sát được | Ai chịu ảnh hưởng? | Dấu hiệu thật |
|---|---|---|---|---|
| 1 | Lặp lại | Sàng lọc hàng trăm CV thủ công để tìm ứng viên pass vòng hồ sơ | HR (Talent Acquisition) | Mất 3-5 phút/CV, tốn hàng chục giờ/đợt tuyển |
| 2 | Lặp lại | Trả lời tin nhắn khách hàng (FAQ: còn hàng không, phí ship...) | Nhân viên trực page | 80% tin nhắn lặp lại, quá tải lúc cao điểm |
| 3 | Tốn thời gian | Đọc hàng ngàn review trên sàn TMĐT để tìm insight/lỗi sản phẩm | Product Manager, Marketing | Mất cả ngày để tổng hợp 1 file Excel data |
| 4 | Tốn thời gian | Gõ lại thông tin từ hóa đơn giấy/scan vào phần mềm kế toán | Kế toán viên | Lặp lại hàng tháng, tốn 3-5 phút/hóa đơn |
| 5 | Tốn thời gian | Dò tìm điều khoản rủi ro trong hợp đồng dài hàng chục trang | Legal, Sales | Mất 30-45 phút/hợp đồng, dễ hoa mắt bỏ sót |
| 6 | Lặp lại | Sắp xếp lịch phỏng vấn qua lại giữa ứng viên và Hiring Manager | HR Coordinator | Email qua lại 3-4 lần mới chốt được giờ |
| 7 | Tốn thời gian | Viết nội dung mô tả sản phẩm (Product Description) cho hàng trăm SKUs | Content, Chủ shop | 15-20 phút/bài chuẩn SEO |
| 8 | AI có thể tốt hơn | Đối chiếu công nợ giữa sổ ngân hàng và file nội bộ | Kế toán viên | Lệch số nhưng rất khó dò tìm do khối lượng lớn |
| 9 | AI có thể tốt hơn | Đọc các bài post của đối thủ trên mạng xã hội để phân tích chiến lược | Marketing | Dữ liệu rải rác, khó tổng hợp overview |
| 10 | Pain từ người khác | Sale giục duyệt hợp đồng nhanh nhưng Legal bị kẹt vì dài | Legal, Sales | Nút thắt làm chậm tiến độ chốt deal |


## Top 3

| Rank | Problem | Vì sao chọn | Điều còn chưa chắc |
|---|---|---|---|
| 1 | Sàng lọc hồ sơ (CV) | Nỗi đau rõ ràng ở mọi công ty, dữ liệu đầu vào (CV + JD) luôn có sẵn, metric tiết kiệm thời gian đo được ngay. | CV thiết kế quá dị/đồ họa phức tạp AI có thể đọc sót (OCR parse lỗi). |
| 2 | Chatbot giải đáp FAQ & Chốt đơn | Ảnh hưởng trực tiếp đến doanh thu (rớt đơn do trả lời chậm). Giá trị AI mang lại có thể tính ra tiền thật. | AI có thể "ảo giác" báo sai giá/tồn kho nếu không kiểm soát tốt logic. |
| 3 | Phân tích review TMĐT | Khối lượng dữ liệu (text) lớn, quá sức người nhưng lại là thế mạnh tuyệt đối của AI (NLP & Sentiment analysis). | Cách định nghĩa "insight tốt" khá cảm tính tùy mỗi Product Manager. |

## Problem Card #1 — Sàng lọc hồ sơ (CV)

**Problem 1 câu:**  
Mỗi đợt tuyển dụng, HR tốn hàng chục giờ đọc lướt thủ công hàng trăm CV định dạng khác nhau để đối chiếu với Job Description (JD) và lọc ra ứng viên pass vòng hồ sơ.

**Actor:**  
Chuyên viên tuyển dụng (Talent Acquisition / HR) chịu trách nhiệm cung cấp short-list ứng viên cho Hiring Manager.

**Thời điểm / bối cảnh:**  
Giai đoạn đầu của phễu tuyển dụng, sau khi đóng cổng nhận CV từ các kênh.

**Current workflow:**

```text
1. Tải hàng loạt CV từ email/platform tuyển dụng.
2. Mở từng file CV.
3. Đọc lướt tìm keyword (kinh nghiệm, kỹ năng, học vấn).
4. Đối chiếu tiêu chuẩn với file JD.
5. Phân loại Pass/Fail sơ bộ.
6. Nhập trạng thái vào file tracking (Excel/ATS).
7. Gửi email phản hồi/mời phỏng vấn.
```

**Bottleneck:**

Bước 3 & 4 — Đọc lướt và đối chiếu JD tốn khoảng 3-5 phút/CV. Do lặp lại liên tục, HR dễ bị hoa mắt, bỏ sót thông tin ứng viên tốt vào cuối ngày.

**Impact:**

300 CV mất khoảng 15-25 giờ làm việc. Ứng viên phải chờ 1-2 tuần mới nhận được phản hồi, dễ mất người giỏi vào tay đối thủ.

**Success metric:**

Giảm thời gian lọc 300 CV xuống dưới 1 giờ. Tỷ lệ CV pass vòng AI được Hiring Manager đồng ý phỏng vấn đạt trên 85%.

**Non-AI alternative:**

Bắt ứng viên tự điền form chuẩn hóa (nhưng ứng viên hay bỏ ngang vì phiền). Dùng tool ATS cũ bắt exact keyword (dễ loại nhầm CV có từ đồng nghĩa).

**AI hypothesis:**

AI trích xuất dữ liệu không cấu trúc từ file PDF/Image, đối chiếu linh hoạt ngữ nghĩa với JD để chấm điểm (match score). HR chỉ cần duyệt lại danh sách Top.

**Quick gut:**

Workflow.

### Draft current workflow

```text
CURRENT STATE — Khoảng 24 giờ / 300 CV

[1 Tải CV: 30']
→ [2 Mở file: 30']
→ [3 Đọc lướt tìm ý: 700'] <-- bottleneck
→ [4 Đối chiếu JD: 300'] <-- bottleneck
→ [5 Phân loại sơ bộ: 60']
→ [6 Nhập file tracking: 120']
→ [7 Gửi email: 60']
```

### Draft future workflow

```text
FUTURE STATE — Khoảng 1h20 phút / 300 CV

[1 Auto-fetch CV từ nguồn: 5']
→ [2 AI trích xuất data (Entity extraction): 5']
→ [3 AI đối chiếu & chấm điểm match với JD: 10']
→ [4 HR review list Top 30 ứng viên cao điểm nhất: 60'] <-- human boundary
→ [5 Gửi auto-email cho list pass/fail: 5']

Fallback: Nếu AI trích xuất lỗi do format PDF mờ, đẩy file đó ra một thư mục để HR check tay.
```
## Problem Card #2 — Chatbot giải đáp FAQ & Chốt đơn

**Problem 1 câu:**

Nhân viên trực page quá tải và hay bỏ lọt tin nhắn vì 80% câu hỏi của khách hàng lặp đi lặp lại, dẫn đến rớt đơn hàng vào giờ cao điểm hoặc ban đêm.

**Actor:**

Nhân viên CSKH/Trực page và Chủ shop kinh doanh.

**Thời điểm / bối cảnh:**

Khi khách hàng nhắn tin hỏi thông tin sản phẩm (giá, size, tồn kho, phí ship) vào các dịp chạy ads campaign hoặc ngoài giờ hành chính.

**Current workflow:**

```text
1. Nhận thông báo tin nhắn khách hàng.
2. Đọc câu hỏi và hiểu ý định.
3. Check tồn kho/bảng giá trên phần mềm nội bộ.
4. Gõ câu trả lời gửi khách.
5. Tư vấn thêm hoặc up-sale.
6. Xin thông tin giao hàng.
7. Nhập thông tin tạo đơn.
```

**Bottleneck:**

Bước 3 & 4 — Check thông tin và gõ câu trả lời lặp lại hàng trăm lần. Phải xử lý tin nhắn theo thứ tự (queue), khách cuối hàng phải chờ rất lâu.

**Impact:**

Chậm trả lời > 5 phút khiến tỷ lệ chốt đơn giảm mạnh. Mất chi phí thuê nhân viên trực ca đêm nhưng không tối ưu.

**Success metric:**

AI tự động xử lý >60% tin nhắn mà không cần người can thiệp. Thời gian phản hồi tin nhắn < 5 giây. Tỷ lệ conversion rate giữ nguyên hoặc tăng.

**Non-AI alternative:**

Sử dụng chatbot kịch bản (rule-based) với các nút bấm. Khách hàng cảm thấy cứng nhắc, không hỏi được đúng ý và thường bấm "Gặp nhân viên hỗ trợ".

**AI hypothesis:**

Agent AI kết nối với API kho hàng, hiểu ngôn ngữ tự nhiên, tự động truy xuất data và nói chuyện linh hoạt như nhân viên để chốt đơn.

**Quick gut:**

Agent.

### Draft current workflow

```text
CURRENT STATE — Tốn nguồn lực tuyến tính, ùn tắc lúc cao điểm

[1 Nhận tin: 1']
→ [2 Đọc hiểu: 1']
→ [3 Check kho/giá: 3'] <-- bottleneck lặp lại
→ [4 Gõ trả lời: 3'] <-- bottleneck lặp lại
→ [5 Tư vấn thêm: 5']
→ [6 Xin thông tin: 2']
→ [7 Lên đơn: 2']
```

### Draft future workflow

```text
FUTURE STATE — Xử lý song song, tức thời

[1 Khách nhắn tin: 0']
→ [2 AI hiểu intent & tự call API check kho: 0.1']
→ [3 AI sinh câu trả lời & dẫn dắt: 0.1']
→ [4 AI thu thập thông tin khách: 0.1']
→ [5 Nhân viên duyệt lại và bấm lên đơn: 2'] <-- human boundary

Fallback: Khách hỏi câu ngoài phạm vi hiểu biết → AI tự động bàn giao (handoff) cho nhân viên người thật xử lý.
```

## Problem Card #3 — Phân tích review thương mại điện tử

**Problem 1 câu:**

Bộ phận Product/Marketing không thể đọc thủ công hàng ngàn review từ nhiều nền tảng để kịp thời phát hiện lỗi sản phẩm hay xu hướng phàn nàn của khách hàng.

**Actor:**

Product Manager (PM) và Trưởng phòng Marketing / CSKH.

**Thời điểm / bối cảnh:**

Định kỳ hàng tháng để đo lường sức khỏe sản phẩm, hoặc ngay sau khi launch một sản phẩm mới ra thị trường.

**Current workflow:**


```text
1. Export dữ liệu review từ các sàn ra file Excel.
2. Gom chung vào 1 file master.
3. Đọc lướt từng dòng text review.
4. Gắn nhãn thủ công (VD: Tích cực/Tiêu cực, Lỗi bao bì).
5. Đếm số lượng theo từng nhãn.
6. Vẽ biểu đồ.
7. Viết báo cáo insight.
```

**Bottleneck:**

Bước 3 & 4 — Đọc lướt và gắn nhãn tốn lượng thời gian khổng lồ. Kết quả gắn nhãn bị phụ thuộc vào cảm tính của người ngồi đọc.

**Impact:**

Đội ngũ phản ứng chậm chạp với phản hồi thị trường. Mất hàng tuần mới biết lô hàng mới bị lỗi, gây thiệt hại cho thương hiệu.

**Success metric:**

Giảm thời gian làm báo cáo tổng hợp từ 2 ngày làm việc xuống dưới 15 phút. Độ bao phủ phân tích đạt 100%.

**Non-AI alternative:**

Thuê sinh viên/part-time đọc và phân loại dữ liệu (tốn kém, chất lượng không đồng đều). Hoặc chỉ lọc đọc review 1-2 sao.

**AI hypothesis:**

AI phân tích sắc thái ngữ nghĩa (Sentiment Analysis) và gom cụm chủ đề (Topic Clustering) tự động để sinh ra báo cáo xu hướng.

**Quick gut:**

Workflow.

### Draft current workflow

```text
CURRENT STATE — Khoảng 16 giờ / 5000 reviews

[1 Export data: 30']
→ [2 Merge data: 30']
→ [3 Đọc thủ công: 600'] <-- bottleneck
→ [4 Gắn nhãn phân loại: 180'] <-- bottleneck
→ [5 Tính toán tổng hợp: 60']
→ [6 Vẽ biểu đồ: 30']
→ [7 Viết báo cáo: 60']
```

### Draft future workflow

```text
FUTURE STATE — Khoảng 40 phút / 5000 reviews

[1 Script auto-pull data: 2']
→ [2 AI xử lý Sentiment & Topic Tagging: 5']
→ [3 AI sinh dashboard/summary insight: 3']
→ [4 PM đọc báo cáo & dò lại các cụm review bất thường: 15'] <-- human boundary
→ [5 PM viết action plan: 15']

Fallback: Các tag AI chưa tự tin được gom vào mục "Uncategorized" để PM định nghĩa lại.
```

