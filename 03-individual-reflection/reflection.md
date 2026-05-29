# 03 — Individual Reflection

---

## Đóng góp của Thành Công trong nhóm

| Hoạt động                  | Tôi đã làm gì?                                                                                                                                                                         | Kết quả / ảnh hưởng                                                  |
| ----------------------------| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ----------------------------------------------------------------------|
| Scan cá nhân               | Đưa ra 9 problems từ góc nhìn AI Engineer (clean data, eval output, tìm paper, train experiment, boilerplate code, viết báo cáo tiến độ, tóm tắt meeting, hướng dẫn intern, đọc paper) | Nhóm có thêm góc nhìn kỹ thuật, candidates #10 #11 #12 vào bảng tổng |
| Pitch Problem Card         | Pitch 3 bài: #10 Clean data, #11 Evaluate output AI, #12 Tìm & tóm tắt paper                                                                                                           | #12 (tìm & tóm tắt paper) vào shortlist top 4                        |
| Challenge bài của bạn khác | Challenge #7 (Discord search) về data access và scope; challenge #3 (deadline) về API integration                                                                                      | Giúp nhóm thấy rõ rủi ro của #7 và #3, góp phần chọn #4              |
| Gom trùng / cluster        | Đề xuất gộp #10 vào cluster F (Data pipeline) riêng; gộp #2 và #12 vào cluster D (Research & đọc hiểu)                                                                                 | Cluster rõ ràng hơn, giảm từ 12 xuống 6 nhóm                         |
| Chọn candidate problem     | Pitch và bảo vệ candidate #12 (Tìm & tóm tắt paper) để đưa vào shortlist top 4                                                                                                         | nhóm không chọn                                                      |
| Validation / research      | Tìm các tool tóm tắt paper như Semantic Scholar, Elicit, ChatPDF để validate giải pháp                                                                                                 | nhóm không chọn                                                      |
| Workflow nhóm              | Thiết kế current và future workflow cho bài toán tóm tắt paper của riêng mình                                                                                                          | nhóm không chọn                                                      |
| Problem Statement          | Viết nháp Problem Statement với các metric và boundary cụ thể cho bài toán tóm tắt paper                                                                                               | nhóm không chọn                                                      |
| Rule / Workflow / Agent    | Phân tích 3 mức độ Rule / Workflow / Agent để chứng minh tại sao bài toán tóm tắt paper nên dùng Workflow                                                                              | nhóm không chọn                                                      |
| Decision                   | Đề xuất quyết định Go cho bài toán tóm tắt paper cùng các điều kiện rollback/exit cụ thể                                                                                               | nhóm không chọn                                                      |

## Bảng dùng AI trong reflection

| Phase                   | Tôi dùng AI để làm gì?                            | AI hữu ích ở đâu?                                                    | AI sai/hời hợt ở đâu?                                               | Tôi sửa gì bằng nhận định của mình?                             |
| -------------------------| ---------------------------------------------------| ----------------------------------------------------------------------| ---------------------------------------------------------------------| -----------------------------------------------------------------|
| Problem Card            | Nhờ AI phản biện card #10 (clean data)            | Chỉ ra metric "data đủ sạch" cần định nghĩa rõ hơn                   | AI đề xuất thêm quá nhiều field không cần thiết                     | Chỉ giữ các field theo template, bổ sung metric cụ thể          |
| Workflow                | Nhờ AI chuyển mô tả workflow thành dạng text flow | Nhanh hơn khi format flow với ký hiệu →                              | AI gộp bước clean + validate thành 1, nhưng thực tế là 2 bước riêng | Tách lại vì bottleneck nằm ở bước clean, không phải validate    |
| Problem Statement       | Nhờ AI phản biện PS v0                            | Chỉ ra Boundary chưa nói về privacy khi dùng AI public               | AI đề xuất thêm field "stakeholder map" — quá rộng cho lab          | Chỉ thêm 1 dòng Boundary về privacy, không thêm field mới       |
| Rule / Workflow / Agent | Nhờ AI so sánh 3 mức                              | AI giải thích rõ khi nào cần Agent (tự lập kế hoạch, gọi nhiều tool) | AI thiên về đề xuất Agent "cho tương lai"                           | Nhóm quyết giữ Workflow vì workflow tuyến tính, không cần Agent |

## Reflection câu hỏi mở

- **Tôi học được gì khi nghe top 3 problems của các bạn khác?**
  Văn Công và Hiếu nhìn từ góc SV mới — những pain tưởng nhỏ (onboarding, search Discord) nhưng lặp lại mỗi ngày. Dũng có workflow cụ thể nhất vì đang thực tập hàng tuần. Tôi nhận ra problem tốt không cần "kỹ thuật" mà cần "lặp lại + đo được".

- **Nhóm có lúc nào bị solution-first không?**
  Có — lúc đầu tôi muốn pitch #10 (clean data) vì nghĩ "AI có thể tự clean data". Nhưng khi vẽ workflow thì thấy mỗi dataset khác nhau, không có 1 workflow cố định. Nhóm kéo lại đúng hướng: chọn bài có workflow rõ trước.

- **Tôi có thay đổi ý kiến sau khi bị challenge không?**
  Có — ban đầu tôi nghĩ #12 (tìm paper) là bài tốt nhất vì AI rất phù hợp. Nhưng nhóm challenge: "không phải cả nhóm trải nghiệm bối cảnh AI Engineer". Tôi đồng ý và chuyển sang ủng hộ #4.

- **Tôi đóng góp gì thật sự vào artifact cuối?**
  Research tool (4 tool), góp ý Boundary (privacy), lập luận không chọn Agent. Phần workflow chính do Dũng mô tả vì đó là workflow của Dũng.

- **Điều khó nhất khi viết Problem Statement là gì?**
  Viết Boundary — phải nghĩ "AI không được làm gì" thay vì "AI làm được gì". Đây là mindset ngược lại so với cách tôi thường nghĩ khi làm AI Engineer.

- **Nếu làm lại, tôi sẽ challenge nhóm mạnh hơn ở điểm nào?**
  Tôi sẽ hỏi kỹ hơn về metric "GVHD không chê chung chung" — đo thế nào? Rubric GVHD có rõ không? Nếu không rõ thì metric này khó verify.

Nếu làm lại:

```text
Tôi sẽ validate metric "giọng AI không tự nhiên" bằng cách cho 2-3 GVHD đọc blind test (1 bản AI draft, 1 bản SV tự viết) để xem họ phân biệt được không. Baseline hiện tại chủ yếu đến từ cảm nhận chủ quan của Dũng.
```
