## Đóng góp của Hùng trong nhóm

| Hoạt động | Hùng đã làm gì? | Kết quả |
|---|---|---|
| Problem Statement | Hoàn thiện Problem Statement từ phiên bản v0 lên v1, bổ sung Actor, Workflow, AI Intervention Point, Success Metric và Boundary | Problem Statement rõ ràng, đáp ứng đầy đủ các trường yêu cầu của bài lab |
| Workflow | Đề xuất quy trình người dùng nhập link → hệ thống thu thập dữ liệu → AI phân tích → đưa ra khuyến nghị | Workflow thể hiện rõ bottleneck và vị trí AI tạo giá trị |
| AI Integration | Xác định AI chỉ tham gia ở bước phân tích dữ liệu giá và sinh khuyến nghị thay vì thay thế toàn bộ workflow | Nhóm thống nhất hướng làm Workflow tích hợp AI thay vì Agent hoàn chỉnh |
| Research & Refinement | Đọc lại các giải pháp như Keepa, BeeCost và đối chiếu với ý tưởng nhóm để tìm điểm khác biệt | Làm rõ giá trị cốt lõi của sản phẩm là phát hiện khả năng phân biệt giá thay vì chỉ theo dõi lịch sử giá |
| MVP Planning | Đề xuất phạm vi MVP chỉ tập trung vào một website và hai luồng so sánh (user mới và user cũ) | Scope phù hợp với thời gian của lab và có phương án fallback khi bị chặn crawl |
| Documentation | Chuẩn hóa nội dung báo cáo, chỉnh sửa mô tả workflow, metric và decision rationale | Báo cáo cuối cùng thống nhất về thuật ngữ và dễ theo dõi |

## Bảng dùng AI trong reflection

| Phase | Tôi dùng AI để làm gì? | AI hữu ích ở đâu? | AI sai/hời hợt ở đâu? | Tôi sửa gì |
|---|---|---|---|---|
| Problem Statement | Nhờ AI rà soát các trường còn thiếu và đề xuất cách diễn đạt | Giúp hoàn thiện Actor, Workflow, Metric và Boundary nhanh hơn | Một số mô tả còn chung chung, thiếu bối cảnh của bài toán | Điều chỉnh lại theo đúng workflow của nhóm |
| Workflow | Dùng AI gợi ý cách mô tả luồng trước và sau khi có hệ thống | Giúp workflow mạch lạc và dễ trình bày | AI có xu hướng biến toàn bộ quy trình thành Agent | Giữ lại hướng Workflow kết hợp AI theo yêu cầu của nhóm |
| Research | Hỏi AI về các công cụ tương tự trên thị trường | Tổng hợp nhanh các sản phẩm liên quan và ý tưởng triển khai | Có một số thông tin mang tính quảng bá hoặc chưa được kiểm chứng | Chỉ giữ các ý đã đối chiếu với tài liệu chính thức |
| MVP Design | Nhờ AI góp ý phạm vi MVP và các rủi ro kỹ thuật | Giúp xác định phạm vi triển khai khả thi trong thời gian ngắn | AI đề xuất nhiều tính năng vượt quá scope | Thu hẹp MVP chỉ còn một website và hai luồng so sánh |

## Bài học của Hùng

- Một Problem Statement tốt cần mô tả rõ actor, workflow, bottleneck và cách AI tạo ra giá trị.
- AI không nên xuất hiện ở mọi bước, mà chỉ nên tham gia ở những công đoạn con người khó thực hiện hoặc mất nhiều thời gian.
- Việc nghiên cứu các sản phẩm đã có giúp nhóm xác định được điểm khác biệt thay vì xây dựng lại những chức năng đã phổ biến.
- MVP cần được giới hạn phạm vi hợp lý để có thể chứng minh ý tưởng trước khi mở rộng.

Nếu làm lại:

```text
Tôi sẽ dành nhiều thời gian hơn để kiểm chứng giả thuyết về mức chênh lệch giá trên nhiều nền tảng khác nhau trước khi chốt Success Metric, nhằm tăng tính thuyết phục cho Problem Statement.
```