# Phase 1 — Top 3 Problem Cards

> Bối cảnh: AI Engineer, vừa học vừa làm, team nhỏ dưới 10 người. Công việc chính: xử lý data, train/fine-tune model (LLM, CV, NLP), dùng HuggingFace/PyTorch, Vector DB. Giao tiếp qua Slack/Discord/Zalo, Google Docs/Sheets/Drive.

## Scan rộng

| #   | Lăng kính          | Problem quan sát được                                                                                                | Ai đang đau?                                  | Dấu hiệu thật                                                                        |
| -----| --------------------| ----------------------------------------------------------------------------------------------------------------------| -----------------------------------------------| --------------------------------------------------------------------------------------|
| 1   | Tốn thời gian      | Chuẩn bị / clean data cho mỗi experiment: xử lý missing values, chuẩn hóa format, loại noise, viết script tiền xử lý | Bản thân (AI Engineer)                        | Mỗi dataset mới mất 2-5 tiếng clean, chiếm 60-70% thời gian dự án                    |
| 2   | Tốn thời gian      | Tìm paper / docs / best practice cho task cụ thể: đọc arxiv, blog, GitHub, so sánh approach                          | Bản thân (AI Engineer)                        | Mỗi lần research mất 1-3 tiếng, paper dài 10-20 trang, khó biết cái nào relevant     |
| 3   | Tốn thời gian      | Evaluate chất lượng output AI: chạy benchmark, so sánh kết quả giữa các lần thử, phân tích lỗi                       | Bản thân, team                                | Mỗi lần eval mất 1-2 tiếng, phải viết script riêng, kết quả rải rác nhiều nơi        |
| 4   | Tốn thời gian      | Thử nghiệm train mất nhiều thời gian: tune hyperparameter, chờ train, so sánh kết quả giữa các run                   | Bản thân (AI Engineer)                        | Mỗi experiment mất vài tiếng đến vài ngày, thử sai nhiều lần mới tìm được config tốt |
| 5   | Lặp lại            | Viết boilerplate code cho mỗi experiment mới: data loader, training loop, logging, config                            | Bản thân, teammate                            | Mỗi project mới copy-paste + sửa lại, mất 1-2 tiếng setup                            |
| 6   | Lặp lại            | Viết báo cáo / update tiến độ thử nghiệm cho team lead: kết quả train, so sánh metric, next step                     | Bản thân, team lead                           | Mất ~30 phút/tuần, format lặp lại nhưng vẫn phải tự tổng hợp                         |
| 7   | AI có thể tốt hơn  | Tóm tắt meeting / cuộc họp: sau khi họp xong phải ghi lại nội dung chính, action items, ai làm gì                    | Cả team                                       | Hay quên nội dung nếu không ghi ngay, mất 10-20 phút tổng hợp                        |
| 8   | Pain từ người khác | Team member / intern hỏi lặp lại cách setup môi trường, cách chạy experiment, cách đọc kết quả                       | Intern, member mới, bản thân (phải hướng dẫn) | Câu hỏi lặp lại mỗi khi có người mới, mất 30-60 phút giải thích                      |
| 9   | AI có thể tốt hơn  | Đọc và tóm tắt paper dài để quyết định có nên áp dụng approach đó không                                              | Bản thân (AI Engineer)                        | Paper 10-20 trang, đọc xong mới biết có phù hợp hay không, mất 30-60 phút/paper      |

## Top 3

| Rank | Problem                              | Vì sao chọn                                                                                                              | Điều còn chưa chắc                                                       |
| ------| --------------------------------------| --------------------------------------------------------------------------------------------------------------------------| --------------------------------------------------------------------------|
| 1    | Chuẩn bị / clean data cho experiment | Workflow rõ, bottleneck cụ thể (chiếm 60-70% thời gian), metric thời gian dễ đo, có thể so sánh Rule/Workflow/Agent      | "Data đủ sạch" đo thế nào? Mỗi dataset khác nhau thì pipeline khác nhau? |
| 2    | Evaluate chất lượng output AI        | Actor rõ, lặp lại mỗi experiment, bottleneck ở viết script eval + so sánh kết quả rải rác, impact lớn lên tốc độ iterate | Eval metric khác nhau theo task, chuẩn hóa đến đâu?                      |
| 3    | Tìm paper / đọc tóm tắt paper        | Pain thật (mất nhiều giờ), AI có thể tóm tắt/so sánh paper, metric rõ (thời gian research)                               | Chất lượng tóm tắt AI có đủ tin cậy để ra quyết định kỹ thuật?           |


# Phase 2 — Top 3 Problem Cards + Draft Workflow

---

## Problem Card #1 — Chuẩn bị / Clean Data cho Experiment

```text
┌──────────────────────────────────────────────┐
│ PROBLEM CARD #1                              │
│                                              │
│ Problem 1 câu: AI Engineer mất 60-70% thời  │
│ gian dự án để clean/tiền xử lý data trước   │
│ khi train, mỗi dataset phải viết script      │
│ riêng, lặp lại nhiều bước thủ công.          │
│                                              │
│ Ai đang đau? AI Engineer, Data Engineer      │
│                                              │
│ Workflow hiện tại:                           │
│ 1. Nhận raw data → 2. Khảo sát data →       │
│ 3. Viết script clean → 4. Chạy + kiểm tra   │
│ → 5. Sửa script → 6. Lặp lại 4-5           │
│                                              │
│ Bước nghẽn nhất: Bước 2-3 (2-3 tiếng/lần)   │
│                                              │
│ Đo thành công bằng gì? Giảm thời gian từ    │
│ 2-5 tiếng → dưới 1 tiếng/dataset            │
│                                              │
│ Quick gut: ☑ Workflow                        │
└──────────────────────────────────────────────┘
```

### Chi tiết Problem Card #1

**Problem 1 câu:**
AI Engineer mất 60-70% thời gian dự án để chuẩn bị và clean data trước khi train model. Mỗi dataset mới phải viết script tiền xử lý riêng, xử lý missing values, chuẩn hóa format, loại noise — lặp lại nhiều bước thủ công.

**Actor:**
AI Engineer chịu trách nhiệm chuẩn bị data cho experiment/training trong team nhỏ.

**Thời điểm / bối cảnh:**
Mỗi khi bắt đầu experiment mới hoặc nhận dataset mới từ client/team. Xảy ra 2-4 lần/tháng.

**Current workflow 3-7 bước:**
1. Nhận raw data (CSV, JSON, DB dump, crawled data...)
2. Khảo sát data: check shape, dtypes, missing, duplicates, distribution
3. Viết script tiền xử lý: handle missing, normalize, encode, remove noise
4. Chạy script + kiểm tra output (sample check, statistics)
5. Phát hiện lỗi → sửa script → chạy lại
6. Lặp lại bước 4-5 cho đến khi data đủ sạch
7. Lưu processed data + ghi chú pipeline

**Bottleneck:**
Bước 2-3: khảo sát data thủ công + viết script clean riêng cho từng dataset mất 2-3 tiếng. Bước 4-6: vòng lặp debug script mất thêm 1-2 tiếng.

**Impact:**
- Mỗi dataset mới mất 2-5 tiếng clean, chiếm 60-70% thời gian dự án
- Delay experiment → chậm iterate → chậm delivery
- Script clean thường dùng 1 lần rồi bỏ, không tái sử dụng

**Success metric:**
- Giảm thời gian clean data từ 2-5 tiếng → dưới 1 tiếng/dataset
- Giảm số lần lặp debug script từ 3-5 lần → 1-2 lần
- Tăng tỷ lệ reuse pipeline code giữa các project

**Non-AI alternative:**
- Library có sẵn: pandas-profiling, great_expectations, data validation schemas
- Template pipeline cho từng loại data
- Checklist clean data chuẩn

**AI hypothesis:**
AI phân tích raw data → auto-suggest cleaning steps + generate script tiền xử lý. AI Engineer review script, chạy thử và sửa nếu cần.

**Quick gut:**
[x] Workflow

### Draft current workflow #1

```text
CURRENT STATE — 2-5 tiếng/dataset

[1 Nhận raw data: 0']
→ [2 Khảo sát data (EDA thủ công): 30-60']     <-- tốn thời gian
→ [3 Viết script clean: 60-120']                <-- bottleneck
→ [4 Chạy script + kiểm tra output: 15-30']
→ [5 Phát hiện lỗi → sửa script: 15-30']
→ [6 Lặp lại bước 4-5: × 3-5 lần]              <-- vòng lặp
→ [7 Lưu data + ghi chú: 10']
```

### Draft future workflow #1

```text
FUTURE STATE — dưới 1 tiếng/dataset

[1 Nhận raw data: 0']
→ [2 AI auto-profile data + báo cáo quality: 2-5']    -- Workflow step
→ [3 AI suggest cleaning steps + generate script: 3-5'] -- Workflow step
→ [4 AI Engineer review script + sửa: 15-20']          -- Human boundary
→ [5 Chạy script + AI kiểm tra output: 5-10']          -- Workflow step
→ [6 Sửa nếu cần: 10-15']
→ [7 Lưu pipeline + data: 5']

Fallback: AI generate script sai → Engineer tự viết lại như cũ.
AI profile thiếu sót → Bổ sung EDA thủ công.
```

---

## Problem Card #2 — Evaluate chất lượng output AI

```text
┌──────────────────────────────────────────────┐
│ PROBLEM CARD #2                              │
│                                              │
│ Problem 1 câu: Sau mỗi experiment, AI       │
│ Engineer phải viết script eval riêng, chạy   │
│ benchmark, so sánh kết quả giữa các run     │
│ — kết quả rải rác, khó track.               │
│                                              │
│ Ai đang đau? AI Engineer, Team Lead          │
│                                              │
│ Workflow hiện tại:                           │
│ 1. Train xong → 2. Viết eval script →       │
│ 3. Chạy eval → 4. Gom kết quả → 5. So sánh │
│ → 6. Báo cáo                                │
│                                              │
│ Bước nghẽn nhất: Bước 2+4 (1-2 tiếng)       │
│                                              │
│ Đo thành công bằng gì? Giảm thời gian eval  │
│ từ 1-2 tiếng → dưới 30 phút/experiment      │
│                                              │
│ Quick gut: ☑ Workflow  □ Rule                │
└──────────────────────────────────────────────┘
```

### Chi tiết Problem Card #2

**Problem 1 câu:**
Sau mỗi experiment, AI Engineer phải tự viết script eval, chạy benchmark trên nhiều metric, gom kết quả rải rác từ log/file/notebook rồi so sánh giữa các run — mất 1-2 tiếng mỗi lần và dễ bỏ sót.

**Actor:**
AI Engineer chịu trách nhiệm đánh giá model quality trước khi báo cáo cho team.

**Thời điểm / bối cảnh:**
Sau mỗi lần train/fine-tune xong, cần đánh giá trước khi quyết định bước tiếp. Xảy ra 3-5 lần/tuần trong giai đoạn thử nghiệm.

**Current workflow 3-7 bước:**
1. Train/fine-tune model xong → có checkpoint
2. Viết eval script (hoặc sửa script cũ cho phù hợp)
3. Chạy eval trên test set / benchmark
4. Gom kết quả từ log, TensorBoard, file CSV, notebook
5. So sánh kết quả giữa các run (bảng, biểu đồ)
6. Phân tích lỗi: case nào model sai, pattern lỗi
7. Viết summary + quyết định next step

**Bottleneck:**
Bước 2 (viết/sửa script eval) + Bước 4-5 (gom + so sánh kết quả rải rác). Kết quả nằm ở nhiều nơi khác nhau, không có dashboard tập trung.

**Impact:**
- 3-5 experiments/tuần × 1-2 tiếng eval = 3-10 tiếng/tuần
- So sánh bằng tay dễ miss insight
- Delay quyết định → chậm iterate

**Success metric:**
- Giảm thời gian eval từ 1-2 tiếng → dưới 30 phút/experiment
- Kết quả tất cả run được track ở 1 nơi
- Giảm số lần miss insight khi so sánh

**Non-AI alternative:**
- Dùng MLflow / W&B để auto-track experiment
- Template eval script reusable
- Dashboard Grafana / Streamlit cho metrics

**AI hypothesis:**
AI auto-generate eval report từ training logs: so sánh metrics giữa các run, highlight model nào tốt nhất, chỉ ra pattern lỗi. Engineer review rồi quyết định.

**Quick gut:**
[x] Workflow (kết hợp Rule cho phần tracking)

### Draft current workflow #2

```text
CURRENT STATE — 1-2 tiếng/experiment

[1 Train xong → checkpoint: 0']
→ [2 Viết/sửa eval script: 20-30']              <-- lặp lại
→ [3 Chạy eval trên test set: 10-20']
→ [4 Gom kết quả từ log/CSV/notebook: 15-20']   <-- rải rác
→ [5 So sánh giữa các run (thủ công): 15-30']   <-- bottleneck
→ [6 Phân tích lỗi: 10-20']
→ [7 Viết summary: 10']
```

### Draft future workflow #2

```text
FUTURE STATE — dưới 30 phút/experiment

[1 Train xong → auto-log metrics: 0']            -- Rule (MLflow/W&B)
→ [2 Auto-generate eval report: 2-3']            -- Workflow step
→ [3 AI so sánh runs + highlight best/worst: 2'] -- Workflow step
→ [4 AI phân tích error pattern: 3-5']           -- Workflow step
→ [5 Engineer review + quyết định: 15-20']       -- Human boundary
→ [6 Ghi nhận next step: 5']

Fallback: AI so sánh sai → Engineer check raw metrics.
Auto-log thiếu metric → Bổ sung script eval thủ công.
```

---

## Problem Card #3 — Tìm & Tóm tắt Paper / Docs

```text
┌──────────────────────────────────────────────┐
│ PROBLEM CARD #3                              │
│                                              │
│ Problem 1 câu: AI Engineer mất 1-3 tiếng    │
│ mỗi lần research: tìm paper trên arxiv,     │
│ đọc 10-20 trang, rồi mới biết có phù hợp    │
│ hay không. Nhiều paper đọc xong thấy không   │
│ liên quan.                                   │
│                                              │
│ Ai đang đau? AI Engineer, Researcher         │
│                                              │
│ Workflow hiện tại:                           │
│ 1. Có task/vấn đề → 2. Search arxiv/blog    │
│ → 3. Đọc abstract → 4. Đọc full paper →     │
│ 5. Ghi note → 6. Quyết định dùng hay không  │
│                                              │
│ Bước nghẽn nhất: Bước 3-4 (30-60 phút/paper)│
│                                              │
│ Đo thành công bằng gì? Giảm thời gian       │
│ research từ 1-3 tiếng → dưới 30 phút        │
│                                              │
│ Quick gut: ☑ Workflow                        │
└──────────────────────────────────────────────┘
```

### Chi tiết Problem Card #3

**Problem 1 câu:**
AI Engineer mất 1-3 tiếng mỗi lần research approach mới: search arxiv/blog, đọc paper 10-20 trang, ghi note, so sánh nhiều approach — nhiều paper đọc xong mới biết không phù hợp với bài toán mình.

**Actor:**
AI Engineer cần research approach/technique cho task cụ thể (fine-tuning strategy, data augmentation, architecture...).

**Thời điểm / bối cảnh:**
Khi bắt đầu task mới, khi model performance chưa đạt cần tìm approach khác, hoặc khi team lead yêu cầu survey. Xảy ra 1-3 lần/tuần.

**Current workflow 3-7 bước:**
1. Xác định vấn đề cần research (ví dụ: "cách fine-tune LLM với ít data")
2. Search trên arxiv, Google Scholar, blog, GitHub
3. Đọc abstract + skim 5-10 papers
4. Chọn 2-3 papers đọc kỹ (10-20 trang/paper)
5. Ghi note: approach, dataset, kết quả, limitation
6. So sánh các approach và quyết định áp dụng cái nào
7. Viết lại tóm tắt cho team

**Bottleneck:**
Bước 3-4: đọc nhiều paper nhưng tỷ lệ relevant thấp (chỉ 2-3/10 paper thật sự hữu ích). Mỗi paper đọc kỹ mất 30-60 phút.

**Impact:**
- 1-3 lần research/tuần × 1-3 tiếng = 1-9 tiếng/tuần
- Đọc paper không relevant = thời gian lãng phí
- Miss paper quan trọng vì không đủ thời gian đọc hết

**Success metric:**
- Giảm thời gian research từ 1-3 tiếng → dưới 30 phút
- Tăng tỷ lệ paper relevant từ 20-30% → trên 60%
- Không miss paper quan trọng trong top kết quả

**Non-AI alternative:**
- Follow các newsletter/digest (Papers With Code, Hugging Face blog)
- Dùng Semantic Scholar / Connected Papers
- Nhờ mentor/senior recommend paper

**AI hypothesis:**
AI tóm tắt paper + đánh giá relevance với bài toán cụ thể. Engineer chỉ đọc kỹ paper được AI đánh giá cao, tiết kiệm thời gian filter.

**Quick gut:**
[x] Workflow

### Draft current workflow #3

```text
CURRENT STATE — 1-3 tiếng/lần research

[1 Xác định vấn đề cần research: 5']
→ [2 Search arxiv/blog/GitHub: 15-20']
→ [3 Đọc abstract 5-10 papers: 20-30']
→ [4 Đọc kỹ 2-3 papers: 60-120']          <-- bottleneck
→ [5 Ghi note + so sánh approach: 15-20']
→ [6 Quyết định approach: 10']
→ [7 Viết tóm tắt cho team: 10-15']
```

### Draft future workflow #3

```text
FUTURE STATE — dưới 30 phút/lần research

[1 Xác định vấn đề + mô tả bài toán: 5']
→ [2 AI search + filter papers theo relevance: 2-3']      -- Workflow step
→ [3 AI tóm tắt top 5 papers (approach, kết quả, limit): 3-5'] -- Workflow step
→ [4 Engineer đọc tóm tắt + chọn 1-2 paper đọc kỹ: 10-15']   -- Human boundary
→ [5 AI so sánh approaches cho bài toán cụ thể: 2-3']    -- Workflow step
→ [6 Engineer quyết định approach: 5']                     -- Human boundary

Fallback: AI tóm tắt sai key insight → Engineer đọc full paper.
AI miss paper quan trọng → Bổ sung search thủ công.
```

---

## Card muốn pitch nhất

```text
Card #3 — Tìm & Tóm tắt Paper / Docs
```

Vì sao:

```text
- Pain thật và thường xuyên: mất 1-3 tiếng mỗi lần research, 1-3 lần/tuần
- Tỷ lệ lãng phí cao: 70-80% paper đọc xong mới biết không phù hợp
- Workflow rõ ràng: search → đọc abstract → đọc kỹ → ghi note → so sánh → quyết định
- Bottleneck cụ thể: bước đọc kỹ paper (60-120 phút) với tỷ lệ relevant thấp
- Metric dễ đo: thời gian research, tỷ lệ paper relevant, số paper miss
- AI rất phù hợp cho task này: tóm tắt + đánh giá relevance là thế mạnh của LLM
- Có thể so sánh rõ: No AI (newsletter) vs Rule (keyword filter) vs Workflow (AI tóm tắt) vs Agent (AI tự research)
- Nhiều tool tham khảo để research phase 4: Semantic Scholar, Elicit, ChatGPT, Perplexity
```

Câu hỏi muốn nhóm challenge:

```text
- Semantic Scholar / Elicit / ChatGPT đã làm được việc này rồi, có cần build thêm gì không?
- AI tóm tắt paper có đủ chính xác để ra quyết định kỹ thuật? Nếu miss key insight thì sao?
- Với paper mới (vừa publish), AI có hiểu đúng contribution chính không?
- Bài toán này scope có quá rộng không? Nên giới hạn ở loại paper nào?
```

