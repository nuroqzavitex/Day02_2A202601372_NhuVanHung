# Group Report — Day 02

## Thành viên nhóm

| STT | Họ và tên        | Mã học viên | Vai trò trong nhóm |
|-----|------------------|-------------|--------------------|
| 1   | Nguyễn Quý Dũng  | 2A202601200 | Nhóm trưởng        |
| 2   | Phạm Trung Hiếu  | 2A202601834 | Thành viên         |
| 3   | Đặng Minh Quang  | 2A202601108 | Thành viên         |
| 4   | Nguyễn Nhật Minh | 2A202601950 | Thành viên         |
| 5   | Nhữ Văn Hùng     | 2A202601372 | Thành viên         |
## Group convergence

| Cluster | Candidate examples | Pattern chung |
|---|---|---|
| Bất bình đẳng thông tin giá cả | Grab/Be tăng giá vô lý lúc trời mưa nhẹ, vé máy bay thay đổi sau mỗi lần F5 | Người dùng luôn là bên mù mờ thông tin, bị động trước thuật toán định giá của app |
| Price discrimination (Phân biệt giá) | Cùng một món hàng trên Shopee/Tiki nhưng nick mới giá rẻ hơn nick cũ (khách hàng trung thành bị chém đẹp) | Giá cả thay đổi theo profile người dùng, cookie, thiết bị truy cập |
| FOMO & Chiêu trò chốt sale | Đếm ngược "Chỉ còn 2 sản phẩm với giá này", "Giảm giá chớp nhoáng" | Dùng thuật toán đánh vào tâm lý ép người dùng mua ngay với giá cao |
| Tracking & So sánh giá | Mở nhiều tab ẩn danh, mượn điện thoại bạn bè để check xem giá có rẻ hơn không | Tốn thời gian làm thủ công để chống lại thuật toán tự động |

## Shortlist và score

| Candidate | Actor rõ | Workflow rõ | Pain có evidence | Impact đo được | Làm trong lab | So sánh R/W/A được | Nhóm hiểu domain | Tổng |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| Trợ lý chống phân biệt giá | 5 | 5 | 5 | 5 | 4 | 5 | 5 | 34 |
| Tool cảnh báo FOMO ảo | 4 | 3 | 4 | 3 | 4 | 3 | 4 | 25 |
| Bot tự động săn sale | 3 | 4 | 3 | 4 | 2 | 4 | 4 | 24 |

Nhóm chọn: **Trợ lý chống phân biệt giá (Anti-Algorithmic Pricing Assistant)**.

Vì sao chọn:

- Nỗi đau (pain point) rất thật và bức xúc, ai trong nhóm cũng từng bị.
- Có thể dùng kỹ thuật scraping cơ bản trong lab để lấy data demo (giả lập các user-agent/proxy khác nhau).
- Có thể vẽ workflow before (check giá bằng cơm) / after (AI tự check) cực kỳ rõ ràng.
- Giá trị mang lại đo lường được bằng tiền thật (số tiền tiết kiệm được).

Vì sao không chọn các bài khác:

- Bot tự động săn sale: Phụ thuộc nhiều vào API của sàn, captcha, dễ bị block, khó demo thành công trong thời gian lab.
- Tool cảnh báo FOMO ảo: Impact không quá lớn, chỉ giải quyết vấn đề tâm lý thay vì túi tiền.

## Quick validation

| Nguồn | Số người | Tín hiệu xác nhận | Tín hiệu phản bác | Nhóm sửa problem thế nào |
|---|---:|---|---|---|
| Phỏng vấn nhanh | 5 | 4/5 người từng mượn máy người khác check lại giá vé máy bay/Grab và thấy rẻ hơn. Đều thấy bực mình vì bị "luộc". | 1 người bảo mệt quá cần thì cứ mua, thời gian check giá còn đắt hơn tiền chênh lệch. | Insight: Không bắt người dùng tự thao tác nhiều. Tool phải tự động chạy ngầm và alert. |
| Quan sát thực tế | - | Thuật toán định giá cập nhật theo giây, check tay không bao giờ lại. | Nhiều sàn có cơ chế chống cào data (anti-scraping) rất gắt. | Giới hạn scope lab: Chỉ demo trên 1-2 web mua sắm cụ thể hoặc lấy data historical để chứng minh concept. |

Insight sau validation:

```text
Pain thật không nằm ở việc "hàng hóa đắt lên do lạm phát". Pain nằm ở sự bất công: cảm giác bị lừa khi biết người khác mua rẻ hơn mình tại cùng một thời điểm, hoặc bị tăng giá chỉ vì hệ thống biết mình "đang rất cần mua".
```

## Research giải pháp

| Nguồn / tool / case | Link | Họ giải quyết phần nào? | Điểm mạnh | Khoảng trống / rủi ro | Bài học cho nhóm |
|---|---|---|---|---|---|
| Keepa / CamelCamelCamel | https://keepa.com | Theo dõi lịch sử giá sản phẩm trên Amazon | Biểu đồ lịch sử giá trực quan, có cảnh báo khi giá giảm | Chỉ theo dõi giá theo một luồng tại một thời điểm, không phát hiện được sự khác biệt giá giữa các hồ sơ người dùng khác nhau | Cần theo dõi song song nhiều luồng, chẳng hạn người dùng ẩn danh và người dùng đã đăng nhập, để phát hiện khả năng phân biệt giá |
| BeeCost | https://beecost.vn | Theo dõi lịch sử giá trên Shopee và Tiki | Dễ sử dụng với người dùng Việt Nam, hỗ trợ kiểm tra biến động giá trước và trong các đợt khuyến mãi | Chủ yếu hiển thị lịch sử giá, chưa có AI phân tích hành vi hoặc cơ chế định giá của sàn | Browser extension là hình thức triển khai thuận tiện và phù hợp với thói quen người dùng |
| Trình duyệt Tor / Brave | - | Hạn chế việc theo dõi người dùng thông qua cookie và các kỹ thuật nhận diện trình duyệt | Giảm khả năng nền tảng xây dựng hồ sơ hành vi người dùng | Có thể gây bất tiện cho người dùng phổ thông, làm chậm trải nghiệm hoặc ảnh hưởng đến một số chức năng của website | Giải pháp của nhóm cần cân bằng giữa quyền riêng tư, khả năng chống theo dõi và trải nghiệm sử dụng |

Research takeaway:

```text
Không nên build một tracker giá thông thường. Phải làm một Workflow/Agent biết giả lập các "nhân dạng" khác nhau (thiết bị mới, ẩn danh, nick VIP, nick thường) để check giá chéo theo thời gian thực và dùng AI phân tích xem user hiện tại có đang bị mua hớ không.
```

## Workflow before/after

File nhóm nộp kèm:

```text
02-group-problem-statement-workflow.png/pdf/md
```

Nội dung workflow:

```text
CURRENT STATE — 4 bước, mất công & gây ức chế (15 phút)

[1 User xem đồ/đặt xe trên app, thấy giá cao: 1']
→ [2 Sinh nghi, chuyển sang tab ẩn danh web để check: 5']
→ [3 Vẫn chưa tin, lấy điện thoại bạn thân mở app check thử: 5']
→ [4 So sánh, chửi thề rồi vẫn phải mua vì đang cần: 4']  <-- bottleneck (tốn sức, ức chế)

FUTURE STATE — 3 bước, 1 phút

[1 User mở link sản phẩm, gửi cho Bot/Extension: 10''] 
→ [2 AI Agent tự động check qua proxy, so sánh giá lịch sử và giá chéo các profile: 40'']   -- Agent/Workflow step
→ [3 AI báo cáo: "Bạn đang bị tính đắt hơn 15% so với user mới. Khuyên: Mua bằng tab ẩn danh theo link này": 10'']    -- AI output & Actionable advice

Fallback:
Sàn chặn tool chặn IP → Báo người dùng tự quyết định dựa trên lịch sử giá cũ thay vì giá realtime chéo.

Bottleneck mới:
Tốc độ scrape data realtime để so sánh có thể hơi chậm (vài chục giây), user phải chờ một chút trước khi bấm thanh toán.
```

Before/after impact:

| Metric | Trước | Sau kỳ vọng | Ghi chú |
|---|---:|---:|---|
| Tổng thời gian kiểm tra chéo | 10–15 phút | Dưới 1 phút | Target chính |
| Cảm xúc người dùng | Ức chế, mơ hồ | Yên tâm, chủ động | Trải nghiệm người dùng là yếu tố quan trọng |
| Tỷ lệ mua với giá bất lợi | Rất cao | Gần như bằng 0 | Tác động có thể đo lường trực tiếp bằng chi phí tiết kiệm được |
| Bottleneck chính | Mượn máy hoặc mở cửa sổ ẩn danh để kiểm tra thủ công | Chờ bot crawl dữ liệu và trả kết quả | Có thể tối ưu bằng cách cải thiện hạ tầng và tốc độ crawl |
| Risk mới | Không có công cụ hỗ trợ nên phải kiểm tra thủ công | Có nguy cơ IP bị chặn hoặc dữ liệu crawl không chính xác | Cần cơ chế fallback và kiểm tra dữ liệu rõ ràng |

## Problem Statement v0

| Field | Nội dung |
|---|---|
| **Actor** | Người tiêu dùng thường xuyên mua sắm trực tuyến, đặt xe công nghệ hoặc đặt vé máy bay. |
| **Workflow** | Người dùng mở ứng dụng xem giá → Nghi ngờ bị phân biệt giá → Kiểm tra bằng cửa sổ ẩn danh hoặc thiết bị/tài khoản khác → So sánh giá → Quyết định mua. |
| **Bottleneck** | Việc tự kiểm tra và so sánh giá giữa nhiều thiết bị hoặc tài khoản mất nhiều thời gian, bất tiện, nên đa số người dùng chấp nhận mua với mức giá cao hơn. |
| **Impact** | Người dùng có thể chịu thiệt hại về chi phí do phân biệt giá và dần mất niềm tin vào tính minh bạch của nền tảng. |
| **Success Metric** | Giảm thời gian kiểm tra giá chéo xuống dưới 1 phút; cung cấp ngay mức giá hoặc cách thức mua có chi phí thấp nhất. |
| **Boundary** | Chỉ cung cấp thông tin và gợi ý cho người dùng; không tự động thực hiện giao dịch mua và không sử dụng các phương pháp can thiệp hoặc khai thác trái phép hệ thống của nền tảng. |

## Rule / Workflow / Agent

| Mức | Phương án | Khi nào đủ | Rủi ro | Chọn? |
|---|---|---|---|---|
| **Rule** | Theo dõi lịch sử giá bằng rule-based (tương tự Keepa) | Đủ khi giá chỉ thay đổi theo thời gian và áp dụng giống nhau cho mọi người dùng | Không phát hiện được cơ chế định giá động (Algorithmic Pricing) dựa trên hành vi hoặc hồ sơ người dùng | Không chọn làm giải pháp cốt lõi, chỉ dùng để hỗ trợ |
| **Workflow** | Người dùng nhập link → Script thu thập giá từ nhiều ngữ cảnh (ẩn danh, tài khoản cũ, ...) → Rule so sánh → Xuất báo cáo | Phù hợp để xây dựng MVP vì quy trình tuyến tính, dễ triển khai và kiểm thử | Khó thích ứng nếu nền tảng thay đổi cấu trúc website hoặc thuật toán định giá | Chọn cho giai đoạn 1 |
| **Agent** | AI Agent chạy trong trình duyệt, tự học quy luật thay đổi giá, so sánh nhiều nền tảng và đưa ra khuyến nghị mua tối ưu | Phù hợp khi cần khai thác AI để phân tích hành vi định giá và chủ động đề xuất chiến lược mua hàng | Độ phức tạp cao, yêu cầu nhiều dữ liệu và thời gian phát triển | Chọn làm định hướng phát triển hoàn chỉnh |

Mức chọn:

```text
Workflow lai Agent (Phase 1 tập trung Workflow).
```
Vì sao:

- Bước fetch data ẩn danh/nick phụ có thể làm bằng script (rule).

- Bước phân tích độ lệch giá và đưa ra lời khuyên "Nên mua lúc nào, bằng nick gì" cần AI để tổng hợp thành insight cho người dùng dễ hiểu.

- Vẫn để người dùng tự bấm nút "Thanh toán", kiểm soát được risk.

## Problem Statement v1

| Field | Nội dung |
|---|---|
| **Actor** | Người tiêu dùng cá nhân thường xuyên sử dụng các nền tảng thương mại điện tử, đặt xe hoặc đặt vé trực tuyến. |
| **Workflow** | Người dùng nhập liên kết sản phẩm → Công cụ tự động kiểm tra giá từ nhiều ngữ cảnh (ẩn danh, đăng nhập, ...) → AI phân tích dữ liệu và hành vi định giá → AI đưa ra khuyến nghị mua phù hợp → Người dùng quyết định và hoàn tất giao dịch. |
| **Bottleneck** | Người dùng khó tự phát hiện cơ chế định giá cá nhân hóa của các nền tảng do thiếu công cụ kiểm tra và so sánh hiệu quả. |
| **Impact** | Người dùng có thể phải trả mức giá cao hơn so với mức giá công bằng, làm tăng chi phí mua sắm và giảm niềm tin vào nền tảng. |
| **Success Metric** | Phát hiện được mức chênh lệch giá giữa các ngữ cảnh truy cập; thời gian trả kết quả dưới 1 phút; giúp người dùng tiết kiệm trung bình khoảng 5–10% giá trị đơn hàng. |
| **Boundary** | Chỉ cung cấp thông tin và khuyến nghị; không tự động thực hiện thanh toán hoặc mua hàng; khả năng hoạt động phụ thuộc vào việc thu thập dữ liệu từ các website. |
| **AI Intervention Point** | AI phân tích dữ liệu giá thu thập từ nhiều nguồn (ví dụ: giá hiện tại, giá khi truy cập ẩn danh, giá lịch sử...) để đánh giá khả năng tồn tại cơ chế định giá cá nhân hóa và đưa ra giải thích cùng khuyến nghị phù hợp. |
| **Mức chọn** | Workflow có tích hợp AI nhằm phân tích dữ liệu và tạo ra các khuyến nghị có thể hành động cho người dùng. |
| **Rủi ro & Người thật kiểm tra** | **Rủi ro:** Dữ liệu giá có thể bị cache hoặc thu thập không chính xác, dẫn đến khuyến nghị sai. **Người thật:** Người dùng vẫn là người trực tiếp xác nhận và thực hiện giao dịch mua ở bước cuối cùng. |

## Final decision

Decision:

```text
Go với một Pilot MVP (Minimum Viable Product).
```

Pilot nhỏ nhất:

- Chọn đúng 1 domain để test (ví dụ: một trang web bán vé máy bay hoặc 1 sàn TMĐT cụ thể).

- Xây dựng 1 bot Telegram / Extension nhận link.

- Bot thực hiện 2 luồng scrape: 1 luồng giả lập user cũ nhiều tiền (User-Agent xịn, cookie đã mua sắm nhiều), 1 luồng giả lập user mới toanh/ẩn danh.

- Đưa kết quả vào LLM để sinh ra thông báo: "Cảnh báo, bạn đang bị tính đắt hơn X đồng. Hãy mở ẩn danh để mua".

Exit / rollback:

- Nếu các trang web chặn scrape quá gắt (Cloudflare/Captcha), lùi về việc chỉ phân tích data lịch sử bằng file CSV để chứng minh bài toán (Proof of Concept).

- Nếu sự chênh lệch giá không tồn tại (sàn đang bán cùng 1 giá cho mọi người ở mọi luồng), chứng tỏ giả thuyết sai, phải đổi problem.

Decision rationale:

- Bài toán giải quyết nỗi đau có thật, có tính thời sự.

- Data collection có rủi ro kỹ thuật nhưng có thể có backup plan.

- Chứng minh được giá trị bảo vệ người dùng của AI trước AI của các doanh nghiệp lớn.


